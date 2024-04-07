<template>
    <v-container>
      <h1>{{ key }}</h1>
      <v-card>
        The {{ degree }} chord of {{ key }} is {{ chord }}
      </v-card>
      <button @click="load">Another</button>
    </v-container>
  </template>
  <script>
  import keys from '../assets/keys.json'
  export default {
    name: 'FlashCard',
    data() {
      return {
        key: '',
        chords: '',
        chord: '',
        degree: ''
      }
    },
    methods: {
      pickKey(){
        const n = Math.floor(Math.random()*2)
        const key = Object.keys(keys)[n]
        return {key: key, chords: keys[key]}
      },
      pickChord(chords){
        const n = Math.floor(Math.random()*7)
        const chord = Object.keys(chords)[n]
        return {chord: chords[chord], degree: chord}
      },
      load(){
        const {key, chords} = this.pickKey()
        const {chord, degree } = this.pickChord(chords)
        this.key = key
        this.chords = chords
        this.chord = chord
        this.degree = degree
      },
    },
    mounted(){
      this.load() 
    }
  
  }
  </script>
  
  <style scoped>
  </style>
  