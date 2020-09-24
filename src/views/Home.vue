<template>
  <div class="home container">
    <div class="row">
      <div class="col s12">
        <h2 class="center-align">Vue Todo</h2>
        <form @submit.prevent="addTodo">
          <div class="col s12">
            <div class="input-field col s6 offset-s3">
              <input type="text" id="autocomplete-input" class="autocomplete" v-model="newTodo">
              <label for="autocomplete-input">Add Todo</label>
            </div>
          </div>
          <div class="col s6 offset-s3">
            <button type="submit" class="right-align waves-effect waves-light btn">Add</button>
          </div>
        </form>
        <div class="col s12">
          <h3>Todos:</h3>
          <ul style="list-style:none;">
            <li v-for="(todo, index) in todos" :class="{todoComplete: todo.complete}" :key="index" @dblclick="todo.complete = !todo.complete"><h4>{{todo.todo}}</h4></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data() {
    return {
      todos: [],
      newTodo: '',
      isComplete: false,
    }
  },
    methods: {
      addTodo() {
        let todo = {
          todo: this.newTodo,
          complete: false,
        }
        this.newTodo = '';
        return this.todos.push(todo);
      }
    }
}
</script>

<style lang="scss">
  .todoComplete {
    text-decoration: line-through;
    color: rgb(90, 214, 100);
  }
</style>
