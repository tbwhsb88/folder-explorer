<template>
  <a-tooltip :placement="placement" title="复制到剪贴板">
    <a-button
      class="is-ml-2 is-mr-2"
      size="small"
      icon="copy"
      @click="onClick"/>
  </a-tooltip>
</template>

<script>
export default {
  name: 'export-copy',
  props: {
    value: {
      type: String,
      default: '',
      required: false
    },
    placement: {
      type: String,
      default: 'bottom',
      required: false
    }
  },
  methods: {
    onClick () {
      if (this.value === '') {
        this.$message.warning('请先扫描一个非空目录')
      }
      this.$copyText(this.value)
        .then(() => {
          this.$message.success('内容已经复制到剪贴板')
        }, () => {
          this.$message.error('出现了一些小错误')
        })
    }
  }
}
</script>
