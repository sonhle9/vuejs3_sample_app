<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h2 v-if="num === 0">0</h2>
  <h2 v-else-if="num < 0">-</h2>
  <h2 v-else-if="num > 0">+</h2>
  <h2 v-else>#0</h2>

  <template v-if="display">
    <h2>M</h2>
    <h2>A</h2>
    <h2>T</h2>
  </template>
  <h2 v-show="showElement">Using v-show</h2> <!-- show and hide by css property -->
  <h2 v-if="showElement">Using v-if</h2>
  <h2 v-for="(name, index) in names" :key="name">{{ index }} {{ name }}</h2>
  <h2 v-for="(name) in fullNames" :key="name">{{ name.first }} {{ name.last }}</h2>
  <div v-for="actor in actors" :key="actor.name">
    <h2>{{ actor.name }}</h2>
    <h3 v-for="movie in actor.movies" :key="movie">{{ movie }}</h3>
  </div>
  <h2 v-for="(name) in fullNames" :key="name">{{ name.first }} {{ name.last }}</h2>
  <h2 v-for="(value, key, index) in myInfo" :key="value">{{ index }} {{ key }} {{ value }}</h2>
  <template v-for="name in names" :key="name">
    <h2>{{ name }}</h2>
    <br>
  </template>

  <div>{{ name }}</div>
  <div v-text="name"></div>
  <div v-html="name"></div>
  <h2 v-bind:id="headingID">Heading</h2>
  <button v-bind:disabled="isDisabled">Bind</button>
  <h2 class="underline" v-bind:class="status">Underline text</h2>
  <h2 v-bind:class="isPromoted && 'promoted'">Promoted movie</h2>
  <h2 v-bind:class="isSoldout ? 'sold-out' : 'new'">Soldout? movie</h2>
  <h2 v-bind:class="['new', 'promoted']">Newly promoted movie</h2>
  <h2 v-bind:class="[isPromoted && 'promoted', isSoldout ? 'sold-out' : 'new']">Array condition movie</h2>

  <h2 v-bind:style="{
    color: highlightColor,
    // 'font-size': headerSize + 'px'
    fontSize: headerSize + 'px',
    padding: '20px'
  }">Inline Style</h2>

  <h2 v-bind:style="headerStyleObject">Style Object</h2>
  <h2 v-bind:style="[baseStyleObject, successStyleObject]">Success Style</h2>
  <h2 v-bind:style="[baseStyleObject, dangerStyleObject]">Danger Style</h2>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

// export default {
//   name: 'App',
//   components: {
//     HelloWorld
//   }
// }
export default {
  name: 'App',
  data() {
    return {
      num: 0,
      display: true,
      showElement: true,

      names: ['Bruce', 'Clack', 'Diana'],
      fullNames: [
        { first: 'Bruce', last: 'Wayne' },
        { first: 'Clack', last: 'Kent' },
        { first: 'Princess', last: 'Diana' },
      ],
      actors: [
        { 
          name: 'Christian Bale', 
          movies: ['Batman', 'The Prestige'], 
        },
        { 
          name: 'Di Caprio', 
          movies: ['Titanic', 'Inception'],
        },
      ],
      myInfo: { first: 'Bruce', last: 'Wayne' },

      name: "<b>Spiderman</b>",
      headingID: "heading",
      isDisabled: false,
      status: "danger",
      isPromoted: true,
      isSoldout: true,
      highlightColor: "orange",
      headerSize: 50,
      headerStyleObject: {
        color: 'orange',
        fontSize: '50px',
        padding: '20px'
      },
      baseStyleObject: {
        fontSize: '50px',
        padding: '10px',
      },
      successStyleObject: {
        color: 'green',
        backgroundColor: 'lightgreen',
        border: '1px solid green',
        padding: '20px',
      },
      dangerStyleObject: {
        color: 'darkred',
        backgroundColor: 'red',
        border: '1px solid darkred',
      },
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

.underline {
  text-decoration: underline;
}

.promoted {
  font-style: italic;
}

.new {
  color: olivedrab;
}

.sold-out {
  color: red;
}
</style>
