<template>
  <c-icon
    @click="GENERATOR_SET_IS_GROUP(!isGroup)"
    :title="tooltip"
    v-bind:class="{ 'icon-selected' : isGroup }"
    :icon="icon"
    class="secondary icon" />
</template>

<script>
import { mapState, mapMutations } from 'vuex'
import { GENERATOR_SET_IS_GROUP } from '@/store/mutations.constants'

export default {
  computed: {
    ...mapState('generator', [
      'isGroup'
    ]),

    tooltip () {
      return this.isGroup
        ? this.$t('cancelGroup')
        : this.$t('startGroup')
    },

    icon () {
      return this.isGroup
        ? 'times'
        : 'list-ol'
    }
  },

  methods: mapMutations('generator', [
    GENERATOR_SET_IS_GROUP
  ])
}
</script>

<style scoped lang="scss">
.icon {
  transition: all 0.25s ease-in-out;

  &.icon-selected {
    background-color: white;
    color: black !important;
    padding: 5px;
    width: 35px;
    border-radius: 50%;

    .light & {
      background-color: black;
      color: white !important;
    }
  }
}
</style>

<i18n>
{
  "en": {
    "startGroup": "Start a link group",
    "cancelGroup": "Cancel link group"
  },
  "fr": {
    "startGroup": "Démarrer un groupe de liens",
    "cancelGroup": "Annuler le groupe de liens"
  },
  "es": {
    "startGroup": "Comience un grupo de enlaces",
    "cancelGroup": "Cancelar grupo de enlaces"
  }
}
</i18n>
