<!--
 * @Author        : fineemb
 * @Github        : https://github.com/fineemb
 * @Description   : 
 * @Date          : 2020-02-16 22:33:53
 * @LastEditors   : fineemb
 * @LastEditTime  : 2020-07-14 01:31:33
 -->

# Lovelace Gaode Map Card

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

这个是一个基于高德地图API的Lovelace卡片,完全复刻的官方地图卡片,几乎包含了原来卡片的所有功能. 未来可能会支持更多新的技能.

+ 完全复刻官方的卡片
+ 支持前台自定义卡片配置.

## 更新

+ v1.1
  + 修复未设置路径显示的时候出现空白的错误

  
+ v1.2 **破坏性更新** ( 注意下面的配置示例的变化 )
  + 修复多个key冲突的问题
  + 更改卡片关键字为 `gaode-map-card`
  + 更改配置entities格式和官方map卡片一样

+ v1.2.1
  + 修复`device_tracker`未纳入范围显示的问题

+ v1.2.2
  + 修复覆盖层导致地图不能缩放移动的问题

+ v1.2.3
  + 增加了实时路况的显示开关
  + 修复了icon显示的问题
  
## 预览
![](1.gif)

## HACS 安装
搜索Gaode Map card, 或者手动添加地址安装
## 手动安装
1. 下载 `cn-map-card.js`
1. 复制到 `www\community\lovelace-cn-map`
1. 在Lovelace的resources下添加以下配置
    ``` yaml
    resources:
      - url: /local/community/lovelace-cn-map/cn-map-card.js
        type: module
    ```
1. 在Lovelace视图 `views.cards` 内部添加卡片配置
    ```yaml
      type: 'custom:gaode-map-card'
      default_zoom: '9'
      dark_mode: false
      hours_to_show: '168'
      entities:
        - person.a
        - person.b
        - person.c
        - zone.school
        - zone.home
      key: f87e0c9c4f3e1e78f963075d142979f0
      title: Map
    ```

## 选项

| 属性名 | 类型 | 默认 | 描述
| ---- | ---- | ------- | -----------
| title | string | 选项 | 卡片标题
| entities | entity id | **必选** | 需要显示的条目,支持person,zone,device_tracker
| default_zoom | Number | 选项 | 地图默认缩放等级
| dark_mode | boolean | 选项 | 地图夜间黑暗模式开关
| traffic | boolean | 选项 | 实时路况
| hours_to_show | Number | 选项 | 指定时间内的历史路径,这里是填的是小时
| key | string | **必选** | 自己去高德申请key,内置的key说不定哪天就失效了.
