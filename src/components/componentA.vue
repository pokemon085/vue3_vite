<template>
  <h1>Computed 計算屬性</h1>
  computed寫法1: <input type="number" v-model="num">
  <h3>{{ numFormat }}</h3>

  computed寫法2: <input type="text" v-model="fullName"><br/><br/>
  firstName:{{firstName}} <br/> lastName:{{lastName}}
</template>
<script setup>
import { computed,ref } from "vue";
const num = ref(0);
const firstName = ref('john');
const lastName = ref('doe');

//computed寫法1
const numFormat = computed(() => {
  if (Number.isNaN(num.value * 100)) return num.value;
  return `${num.value * 100}%`;
});

//computed寫法2
const fullName=computed({
    get(){
        return `${firstName.value}_${lastName.value}`
    },
    set(newName){
        const [newFirstName,newlastName]=newName.split('_')
        firstName.value=newFirstName
        lastName.value=newlastName
    }
})
</script>
<style>
</style>