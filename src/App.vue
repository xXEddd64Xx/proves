<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h4>Indica un número enter: </h4>
    <input type="number" v-model="n"><button v-on:click="afegirNum()">Entrar</button>
    <h1>Llista de números</h1>
    <Number v-on:mostrarNum="mostrarNum" v-for="a in nArray" v-bind:num="a" v-bind:key="a"/>
    <h4>El número pitjat és: <span id="numb"></span></h4>
  </div>
</template>

<script>
import Number from './components/Number.vue'

export default {
  name: 'App',
  components: {
    Number
  },
  data() {
    return {
      nArray: []
    }
  },
  methods: {
      afegirNum : function() {
        var esRepe = false;
          for (var i = 0; i < this.nArray.length; i++) {
            if (this.nArray[i]==this.n) {
              esRepe = true;
            }
          }
          if (!esRepe) {
            this.nArray.push(this.n);
          } else { alert("Nombre repetit, afegeix-ne un altre"); }
          
      },
      mostrarNum : function(num) {
        var txt = document.getElementById("numb");
        txt.innerHTML = num;
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
