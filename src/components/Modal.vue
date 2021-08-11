<template>
  <div class="modal flex">
    <div class="modal-content">
      <p>你确定要退出表单填写吗？你填写的表单将不会被保存</p>
      <div class="actions flex">
        <button @click="closeModal" class="purple">返回</button>
        <button @click="closeInvoice" class="red">退出</button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapMutations, mapState } from "vuex";
export default {
  name: "Modal",
  methods: {
    ...mapMutations(["TOGGLE_MODAL", "TOGGLE_INVOICE", "TOGGLE_EDIT_INVOICE"]),
    closeModal() {
      this.TOGGLE_MODAL();
    },
    closeInvoice() {
      this.TOGGLE_MODAL();
      this.TOGGLE_INVOICE();
      if (this.editInvoce) {
        this.TOGGLE_EDIT_INVOICE();
      }
    },
  },
  computed: {
    ...mapState(["editInvoce"]),
  },
};
</script>

<style lang="scss" scoped>
.modal {
  z-index: 100;
  position: fixed;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100%;
  .modal-content {
    border-radius: 20px;
    padding: 48px 32px;
    max-width: 450px;
    background-color: #252945;
    color: #fff;
    p {
      text-align: center;
    }
    .actions {
      margin-top: 24px;
      button {
        flex: 1;
      }
    }
  }
}
</style>