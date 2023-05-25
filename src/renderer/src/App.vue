<template>
  <div class="flex h-screen w-screen">
    <!-- 左侧图标选项栏 -->
    <div class="w-[250px] bg-[#f7f7f7]" :class="{ isCollapse: isCollapse }">
      <!-- 折叠选项栏区域 -->
      <div
        class="h-[50px] w-[50px] flex justify-center items-center cursor-default hover:bg-[#dadadc]"
      >
        <!-- 汉堡图标 -->
        <img
          src="./assets/images/bars.png"
          class="h-[24px] w-[24px]"
          @click="isCollapse = !isCollapse"
        />
      </div>

      <!-- 选项列表 -->
      <ul>
        <li
          v-for="(title, index) in options"
          :key="index"
          class="h-[50px] flex items-center cursor-default hover:bg-[#dedddf]"
          :class="{ selected: currentSelect === title }"
          @click="selectHandle(title)"
        >
          <!-- Logo -->
          <div class="bg-white ml-[13px] border border-black">
            <img :src="`src/assets/images/${title}Logo.png`" class="h-[24px] w-[24px]" />
          </div>
          <!-- 文字区域 -->
          <span class="ml-[13px]">{{ title }}</span>
        </li>
      </ul>
    </div>
    <!-- 右侧配置展示区 -->
    <div class="bg-[#dedddf] flex-1"></div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 当前选中项
const currentSelect = ref('Java')

// 折叠状态
const isCollapse = ref(false)

// 选项列表
const options = ['Java', 'Maven', 'MySQL', 'NodeJS', 'PHP']

// 选中选项
const selectHandle = (title: string): void => {
  currentSelect.value = title
}
</script>

<style scoped lang="less">
// 选项选中时的样式
.selected {
  background-color: #dedddf;
  position: relative;
  &::before {
    content: '';
    position: absolute;
    background-color: #0078d4;
    height: 19px;
    width: 3px;
    margin-left: 4px;
    border-radius: 10px;
  }
}

// 折叠菜单时的样式
.isCollapse {
  width: 50px;
  span {
    display: none;
  }
}
</style>
