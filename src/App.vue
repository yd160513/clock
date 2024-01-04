<script setup lang="ts">
import moment from 'moment'
import { onMounted, ref } from "vue";

const currentTime = ref('')
const date = ref('')
const week = ref('')

const getCurrentDate = () => {
  currentTime.value = moment().format('HH:mm:ss');
  date.value = moment().format('YYYY/MM/DD');
  week.value = getWeek(moment().day())
}

const getWeek = (week: number) => {
  switch (week) {
    case 0:
      return '星期日';
    case 1:
      return '星期一'
    case 2:
      return '星期二';
    case 3:
      return '星期三'
    case 4:
      return '星期四';
    case 5:
      return '星期五'
    case 6:
      return '星期六';
    default:
      return ''
  }
}

onMounted(() => {
  getCurrentDate()
  setInterval(getCurrentDate, 1000)
})

</script>

<template>
  <div class="clock">
    <div class="date">
      {{ date }}
    </div>
    <div class="time">
      {{ currentTime }}
    </div>
    <div class="week">
      {{ week }}
    </div>
  </div>
</template>

<style lang="scss" scoped>
.clock {
  color: #000000;
  display: flex;
  flex-direction: column;
  height: 100%;

  .date {
    margin-top: 4px;
    margin-left: 4px;
  }

  .week {
    margin-bottom: 4px;
    margin-right: 4px;
    text-align: right;
  }

  .date, .week {
    color: #ffffff;
    font-size: 8px;
    height: 10px;
    overflow: hidden;
  }

  .time {
    overflow: hidden;
    flex: 1;
    font-size: 36px;
    display: flex;
    align-items: center;
    -webkit-text-stroke: 1px #ffffff;
    justify-content: center;
  }
}
</style>
