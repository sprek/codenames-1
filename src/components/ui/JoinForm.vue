<template>
  <v-card>
    <v-card-text>
      <v-form @submit="joinGame">
        <!-- <v-text-field label="Username" v-model="username" required></v-text-field> -->
        <v-text-field label="Enter Room ID" v-model="room_num" solo light></v-text-field>
        <v-btn block color="primary" large @click.stop="joinGame">Join</v-btn>
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapMutations } from 'vuex';

export default {
  name: 'create-form',
  data() {
    return {
      // username: '',
      room_num: null,
    };
  },
  computed: {
    room_id() {
      return this.room_num.toUpperCase();
    },
  },
  methods: {
    ...mapMutations(['set_username', 'set_room']),
    joinGame() {
      // this.set_username(this.username);
      this.set_room(this.room_id);
      this.$router.push({ name: 'Player', params: { room: this.room_id } });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
