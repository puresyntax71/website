<template>
  <section class="about hero is-fullheight-with-navbar">
    <div class="hero-body">
      <div class="container">
        <div class="columns">
          <div class="column is-6">
            <h3 class="title is-3">About Me</h3>
            <div class="content">
              <p>I am a web developer from the <strong>Philippines</strong>. I am somewhat fluent
              with <strong>PHP</strong> and <strong>Javascript</strong>.</p>
              <p>I mainly use <strong>Drupal</strong> for developing websites but have experience
              with other technologies not limiting to <strong>PHP</strong>. I mostly do
              <strong>backend development</strong> but I am also comfortable with <strong>frontend
              development</strong> and a little bit of <strong>devops</strong>.</p>
              <p>I build websites from ground up and also do support for existing websites.</p>
              <p>My role mostly involves <strong>migration</strong>, <strong>consuming third-party
                APIs</strong>, <strong>developing custom modules and themes in Drupal</strong>,
              and <strong>site building and configuration</strong>.
              <p>I also occasionally write <strong>tech stuffs</strong> on my
              <a href="https://blog.strict-panda.com">blog</a>.</p>
            </div>
          </div>
          <div class="column is-5 is-offset-1">
            <Skill v-for="skill in getSkills" :key="skill.id" :id="skill.id" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import Skill from '@/components/Skill.vue';

export default {
  name: 'About',
  components: {
    Skill,
  },
  computed: {
    ...mapGetters('airtable', [
      'getItems',
    ]),
    getSkills() {
      return this.getItems('skills');
    },
  },
  methods: {
    ...mapActions('airtable', [
      'fetchSkills',
    ]),
  },
  mounted() {
    this.fetchSkills();
  },
};
</script>
