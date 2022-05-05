<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md q-gutter-sm">
     <q-btn color="primary" label="Register" v-if="!showRegistrationForm" @click="showRegistrationForm = true" />
    </div>
    <form>
      <div class="q-pa-md" v-if="showRegistrationForm">
        <div class="q-gutter-md" style="max-width: 300px">
        <q-input outlined v-model="newUser.username" label="Username" />
        <q-input outlined v-model="newUser.password" label="Password" />
      </div>
   </div>
   <div class="q-pa-md q-gutter-sm registrationButtonsLayout" v-if="showRegistrationForm">
     <q-btn color="primary" label="Submit" @click="addUser" />
     <q-btn color="primary" label="Reset" @click="resetRegistrationForm" />
    </div>
  </form>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data() {
    return {
      showRegistrationForm: false,
      users: [{}],
      newUser: {username: '', password: ''},
    }
  },
  methods: {
    addUser() {
      this.users.push(this.newUser);
      this.resetRegistrationForm();
      this.showRegistrationForm = false;

    },
    resetRegistrationForm() {
      this.newUser = {username: '', password: ''};
    },
  }
})
</script>
