<template>
    <div class="todo-item" v-bind:class="{'is-complete':completed}">
        <p>
            <input type="checkbox" :checked="completed" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
            </p>
            
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    data() {
        return {
            completed: false
        }
    },
    mounted() {
        this.completed = this.todo.completed
    },
    props: ["todo"],
    methods: {
        markComplete() {
            this.completed = !this.completed
        }
    }
};
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #ff0000;
        width: 20px;
        height: 20px;
        color: #fff;
        border: none;
        padding: 5px, 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>