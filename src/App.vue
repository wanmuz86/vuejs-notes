<template>
  <div id="app">
    <h1>Hello my name is {{name}}</h1>
    <p> And I am {{age}} years old. Currently I am in {{location}}</p>
    <button v-on:click="buttonPressed">Click me!</button>
    <hr/>
    <h2>Counter</h2>
    <p>{{number}}</p>
    <p>{{message}}</p>
    <button v-on:click="increment">Increment</button>
    <button v-on:click="decrement" v-bind:disabled="buttonDisabled">Decrement</button>
    <button v-on:click="reset">Reset</button>
    <hr/>
    <p v-if="number % 2 == 0">Current number is even number</p>
    <p v-else>Current number is odd number</p>
    <ul>
      <li v-for="student in students" :key="student">
        {{student}}
      </li>
    </ul>
    <hr>
    <h2>My simple to do!</h2>
    <input type="text" name="item" placeholder="Enter item name" v-model="itemName"/>
    <input type="text" name="place" placeholder="Enter item place" v-model="itemPlace"/>
    <button v-on:click="addPressed">Add new Item!</button>
    <table>
      <tr>
        <th>Item</th>
        <th>Place</th>
      </tr>
      <tr v-for="todo in todos" :key="todo.item" v-on:click="selectItem(todo)">
        <td>{{todo.item}}</td>
        <td>{{todo.place}}</td>
      </tr>
    </table>
    <div v-if="selectedItem">
      <h2>Selected To Do Item</h2>
      <p>{{selectedItem.item}}</p>
      <p>{{selectedItem.place}}</p>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      name: "Muzaffar",
      age:30,
      location:'Bangi',
      number:0,
      message:"",
      buttonDisabled:false,
      students:["Vincent","Ansow","Joseph","SevaSanghari"],
      todos:[{item:"eat",place:'KFC'},{item:"prepare class",place:'Office'},{item:"do laundry",place:'home'}],
      itemName:"",
      itemPlace:"",
      selectedItem:null
    }
  },
  methods: {
    buttonPressed: function(){
      alert("Button is pressed")
    },
    increment: function(){
      // this means get the global variable - from data 
      this.message = ""
      this.number++
      this.buttonDisabled = false
    },
    decrement:function(){
      if (this.number > 0){
        this.number--
      }
      else {
        this.message = "Number cannot be smaller than zero"
        this.buttonDisabled = true;
      }

    },
    reset:function(){
      this.message = ""
      this.number = 0
      this.buttonDisabled = false
    },
    addPressed:function(){
      var newItem = {
        item:this.itemName,
        place:this.itemPlace
      }
      this.todos.push(newItem)
      this.itemName = ""
      this.itemPlace = ""
 
    },
    selectItem:function(todo){
      this.selectedItem = todo
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
