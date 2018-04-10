<template>
  <div>
    <h2>{{msg}}</h2>
    <hr/>
    <h3>{{count}}</h3>
    <div>
      <button @click="$store.commit('add',10)">加分</button>
      <button @click="reduce">减分</button>
    </div>
    <div>
      <button @click="addAction">加分</button>
      <button @click="reduceAction">减分</button>
    </div>
  </div>
</template>

<script>
  import store from '@/vuex/store'
  import {mapState,mapMutations,mapGetters,mapActions} from 'vuex';
  export default {
    data(){
      return {
        msg:'Hello Vuex',
      }
    },
//    computed:{
//      count(){
//        return this.$store.state.count;
//      }
//    },
      computed:{
//        ...mapState(['count']),
        count(){
          return this.$store.state.a.count;
        }
//        ...mapGetters(['count'])
      },
      methods:{
        ...mapMutations(['reduce','add']),
        ...mapActions(['addAction','reduceAction'])
      },// 将 `this.reduce()` 映射为 `this.$store.commit('reduce')`
//    computed:mapState(["count"]),//当映射的计算属性的名称与 state 的子节点名称相同时，我们也可以给 mapState 传一个字符串数组。
    store // 把 store 对象提供给 “store” 选项，这可以把 store 的实例注入所有的子组件
  }
</script>
