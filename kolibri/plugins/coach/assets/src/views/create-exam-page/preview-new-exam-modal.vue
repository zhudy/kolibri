<template>

  <preview-exam-modal
    :examChannelId="examChannelId"
    :examQuestionSources="examQuestionSources"
    :examSeed="examSeed"
    :examNumQuestions="examNumQuestions"
    :examCreation="true">
    <icon-button slot="randomize-button" :text="$tr('randomize')" :primary="true" @click="$emit('randomize')"/>
  </preview-exam-modal>

</template>


<script>

  const ExamActions = require('../../state/actions/exam');

  module.exports = {
    $trNameSpace: 'previewNewExamModal',
    $trs: {
      randomize: 'Randomize questions',
    },
    components: {
      'preview-exam-modal': require('../exams-page/preview-exam-modal'),
      'icon-button': require('kolibri.coreVue.components.iconButton'),
    },
    props: {
      examChannelId: {
        type: String,
        required: true,
      },
      examQuestionSources: {
        type: Array,
        required: true,
      },
      examSeed: {
        type: Number,
        required: true,
      },
      examNumQuestions: {
        type: Number,
        required: true,
      },
    },
    methods: {
      close() {
        this.displayExamModal(false);
      },
    },
    vuex: {
      actions: {
        displayExamModal: ExamActions.displayExamModal,
      },
    },
  };

</script>


<style lang="stylus" scoped></style>
