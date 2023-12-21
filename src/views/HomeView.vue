<template>
  <div class="ContentEditableMain">
    <div
      contenteditable="true"
      class="ContentEditable"
      @input="inputValue"
      ref="editableDiv"
    ></div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const editableDiv = ref(null);

onMounted(() => {
  const savedData = localStorage.getItem('saveData');
  editableDiv.value.innerHTML = savedData || ''; // Set content from localStorage or keep it empty
});

const inputValue = () => {
  const content = editableDiv.value.innerHTML;
  localStorage.setItem('saveData', content);
};
</script>
