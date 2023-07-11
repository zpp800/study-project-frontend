<script setup>
import {get} from "@/net"
import {useStore} from "@/stores";
import router from "@/router";
import {ElMessage} from "element-plus";
const store = useStore();
if(store.auth.user == null) {
  get('/api/user/me', (message) => {
    store.auth.user = message
    router.push('/index')
  }, () => {
    store.auth.user = null
  })
}


// get('/api/user/me',() =>{
//   ElMessage.success('已登录')
// },() =>{
//   ElMessage.warning('未登录')
// })
</script>

<template>
  <router-view/>
</template>

<style scoped>
.welcome-title {
  position: absolute;
  bottom: 30px;
  left: 30px;
  color: white;
  text-shadow: 0 0 10px black;
}
</style>
