<template lang="pug">
  span ${{result.toFixed(2)}}
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  computed: {
    ...mapGetters([
      'data'
    ]),
    result () {
      return this.data
        .filter(it => it.active && it.amount > 0)
        .reduce((acc, item) => {
          return (acc + item.thisMonthAmt)
        }, 0)
    }
  }
}
</script>