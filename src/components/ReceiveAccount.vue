<template>
  <a-input-group compact>
    <a-select v-model="type" style="width:100px" @change="handleTypeChange">
      <a-select-option value="alipay">
        支付宝
      </a-select-option>
      <a-select-option value="bank">
        银行卡
      </a-select-option>
    </a-select>
    <a-input style="width: calc(100% - 100px)" v-model="number" @change="handleNumberChange" />
  </a-input-group>
</template>

<script>
export default {
  props: {
    value: {
      type: Object // type和number
    }
  },
  watch: {
    value(val) {
      Object.assign(this, val);
    }
  },
  data() {
    const { type, number } = this.value || {};
    return {
      type: type || "alipay",
      number: number || ""
    };
  },
  methods: {
    handleTypeChange(val) {
      this.$emit("change", { ...this.value, type: val });
    },
    handleNumberChange(e) {
      this.$emit("change", { ...this.value, number: e.target.value });
    }
  }
};
</script>

<style></style>
