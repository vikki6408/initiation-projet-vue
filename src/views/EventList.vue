<template>
  <div class="events">
    <EventCard v-for="item in events" :key="item.id" :event="item" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService'

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    }
  },
  /*created() {
    axios //appelle l'api
      .get('https://my-json-server.typicode.com/vikki6408/bd_vue/events')
      .then((response) => {
        console.log('event :' + response.data)
        this.events = response.data
      })
      .catch((error) => {
        console.log(error)
      })
  },*/
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data
      })
      .catch((error) => {
        console.log(error)
      })
  },
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
