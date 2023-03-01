<!-- eslint-disable vue/no-parsing-error -->
<template>
  <div class="data-list">
    <el-row>
      <el-col :span="24">
        <el-input v-model="input" placeholder="请输入内容" style="width: 135px; margin-left: 20px" />
        <el-select v-model="value" placeholder="请选择" style="margin-left: 20px">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          />
        </el-select>
        <el-date-picker
          v-model="value1"
          type="datetimerange"
          range-separator="至"
          start-placeholder="开始日期"
          end-placeholder="结束日期"
        />
        <el-button type="primary" icon="el-icon-search">搜索</el-button>
        <el-button type="primary" icon="el-icon-edit">添加</el-button>
        <el-button type="primary" icon="el-icon-download">导出</el-button>
        <el-checkbox v-model="checked" style="margin-left: 20px">审核人</el-checkbox>
      </el-col>
    </el-row>
    <!-- 表格 -->
    <el-table
      :data="list"
      style="width: 100%;"
      boder
    >
      <el-table-column
        prop="id"
        label="序号"
        align="center"
        width="180"
      >
        <template
          slot-scope="{$index}"
        >
          <div>{{ $index + 1 }}</div>
        </template>
      </el-table-column>
      <el-table-column
        prop="name1"
        label="物品名称"
        align="center"
        width="180"
      />
      <el-table-column
        prop="name2"
        label="扫描人员"
        align="center"
        width="180"
      />
      <el-table-column
        prop="picture"
        align="center"
        label="样品图片"
      >
        <template
          slot-scope="{ row }"
        >
          <img :src="row.img" style="width:60px" alt="">
          </img>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'DataList',
  data() {
    return {
      options: [{
        value: '选项1',
        label: '黄金糕'
      }, {
        value: '选项2',
        label: '双皮奶'
      }, {
        value: '选项3',
        label: '蚵仔煎'
      }, {
        value: '选项4',
        label: '龙须面'
      }, {
        value: '选项5',
        label: '北京烤鸭'
      }],
      list: [{
        name1: '人体肾结石',
        name2: '杨蕾',
        address: '上海市普陀区金沙江路 1518 弄'
      }],
      value: '',
      checked: true
    }
  }
}
</script>

<style lang="scss">
.data-list{
  padding: 20px;
  box-sizing: border-box;
}
</style>
