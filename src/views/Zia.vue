<template>
  <div class="flex justify-center">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  </div>
  <div class="flex items-center flex-col space-y-4">
    <div>
      <div>#Ali</div>
      <t-button variant="warning" icon="accessible" outline disabled>
        some text
      </t-button>
    </div>
    <div>
      <div>#zia</div>
      <t-number-picker :max="5" v-model="numberPickerCount"></t-number-picker>
    </div>
    <div>
      <div>#zia</div>
      <t-modal v-model="modal" :close-callback="modalCloseCallback">
        <!--        <template #closeButton="attrs">-->
        <!--          <t-button v-bind="attrs">close</t-button>-->
        <!--        </template>-->
        <p class="text-gray-800">
          Are you sure you want you delete your account? This action cannot be
          undone.
        </p>

        <div class="text-right mt-4">
          <button
            @click="modal = false"
            class="px-4 py-2 text-sm text-gray-600 focus:outline-none hover:underline"
          >
            Cancel
          </button>
          <button
            class="mr-2 px-4 py-2 text-sm rounded text-white bg-red-500 focus:outline-none hover:bg-red-400"
          >
            Delete
          </button>
        </div>
      </t-modal>
      <t-button @click="modal = true">open modal</t-button>
    </div>
    <div>
      <div>#zia</div>
      <t-switch
        v-model="switchModel"
        :true-value="1"
        :false-value="0"
        label="فقط کالاهای موجود"
      ></t-switch>

      <!--      <t-switch-->
      <!--        v-model="switchModel"-->
      <!--        :value="[{ a: 1 }]"-->
      <!--        label="فقط کالاهای موجود"-->
      <!--      ></t-switch>-->
      <!--      <t-switch-->
      <!--        v-model="switchModel"-->
      <!--        :value="{ a: 2 }"-->
      <!--        label="فقط کالاهای موجود"-->
      <!--      ></t-switch>-->
    </div>

    <div>
      <div>#zia</div>
      <t-checkbox
        v-model="checkboxModel"
        :true-value="1"
        :false-value="0"
        label="سامسونگ"
      ></t-checkbox>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { ref, watchEffect } from "vue";

import TButton from "@/components/tailwind/TButton.vue";
import TNumberPicker from "@/components/tailwind/numberPicker/TNumberPicker.vue";
import TModal from "@/components/tailwind/modal/TModal.vue";
import TSwitch from "@/components/tailwind/switch/TSwitch.vue";
import TCheckbox from "@/components/tailwind/checkbox/TCheckbox.vue";
export default defineComponent({
  name: "App",
  components: {
    TCheckbox,
    TSwitch,
    TModal,
    TNumberPicker,
    TButton
  },
  setup() {
    const numberPickerCount = ref<number>(3);
    const switchModel = ref<any>("");
    const checkboxModel = ref<any>("");
    const modal = ref<boolean>(false);
    const modalCloseCallback = () => {
      console.log("modal has been closed");
      return true;
    };
    watchEffect(() => {
      console.log("switchModel", switchModel.value);
      console.log("checkboxModel", checkboxModel.value);
    });
    return {
      numberPickerCount,
      switchModel,
      modal,
      modalCloseCallback,
      checkboxModel
    };
  }
});
</script>
