# DrawBuddy · 万能绘图工作台

一个**单页、纯前端、完全离线可用**的绘图工具，把主流的图表/示意图需求集中到一个页面里：流程图、时序图、思维导图、统计图表，以及"零语法"的快速生成器。

打开 `index.html` 即用，无需安装、无需联网、无需构建。

---

## 功能总览

### 一、图表绘制（17 类模板）

基于 [Mermaid](https://mermaid.js.org/) 渲染，左侧选模板 → 中间改代码 → 右侧实时预览。

| 分类 | 图表类型 |
| --- | --- |
| 流程与结构 | 流程图（纵向 / 横向）、时序图、类图、状态图、ER 图（数据库）、架构方块图 |
| 计划与梳理 | 思维导图、时间线 / 步骤、甘特图、用户旅程图、Git 分支图 |
| 数据与决策 | 饼图、象限图、XY 折线柱状图、桑基图、需求图、自定义笔记 |

- 实时渲染 + 语法错误定位提示
- `Ctrl + 滚轮` 缩放、拖拽平移、一键适应窗口 / 1:1
- 支持导入 `.mmd` 文件

### 二、统计图表（9 类）

基于 [Chart.js](https://www.chartjs.org/)：柱状图、条形图、折线图、面积图、饼图、环形图、雷达图、散点图、极坐标图。

改 JSON 数据即自动刷新：`labels` 为横轴/分类，`datasets` 为数据系列。

### 三、快速生成（无需学语法）

| 生成器 | 输入格式 |
| --- | --- |
| 步骤 → 流程图 | 每行一个步骤；行首 `#` 表示判断（菱形），缩进两格为其分支 |
| 大纲 → 思维导图 | 第一行为中心主题，2 空格 / Tab 缩进表示层级 |
| 时间 → 时间线 | `时间 : 事件1 : 事件2` |
| 角色 → 时序图 | `甲 ->> 乙 : 消息` |
| 数据 → 饼图 | `名称 : 数值` |

生成结果会自动转入「图表绘制」模式，可继续手工微调。

### 四、导出

| 方式 | 说明 |
| --- | --- |
| **导出 PNG** | 3 倍清晰度位图，适合直接贴到文档、汇报材料 |
| **导出 SVG** | 矢量图，任意放大不糊，适合印刷与二次编辑 |
| **导出 README** | 生成 Markdown 文档：图表模式输出 ` ```mermaid ` 代码块（GitHub / Gitee / Typora **原生渲染**），统计模式输出 Markdown 数据表格 |

---

## 使用方式

### 方式一：直接打开（推荐）

下载或克隆本仓库后，双击 `index.html` 即可。

```bash
git clone https://github.com/yxpil/drawbuddy.git
```

### 方式二：在线访问

启用 GitHub Pages 后可直接访问：<https://yxpil.github.io/drawbuddy/>

### 方式三：本地起服务（可选）

```bash
python -m http.server 8080
# 浏览器打开 http://localhost:8080
```

---

## 快捷键

| 快捷键 | 功能 |
| --- | --- |
| `Ctrl + Enter` | 立即重新渲染 |
| `Ctrl + S` | 保存草稿到浏览器本地 |
| `Ctrl + 滚轮` | 缩放预览 |
| 拖拽预览区 | 平移画布 |

草稿、图表数据、生成器输入都会自动保存在浏览器 `localStorage`，刷新不丢失；所有数据都留在本机，不会上传。

---

## 目录结构

```
drawbuddy/
├── index.html               # 全部界面与逻辑（单文件应用）
└── assets/
    ├── mermaid.min.js       # 图表渲染引擎（本地化，离线可用）
    ├── chart.umd.min.js     # 统计图表引擎（本地化，离线可用）
    └── tailwind.js          # 样式引擎（Play CDN 本地化）
```

界面使用 Tailwind 工具类 + CSS 变量主题；全部图标为内联 SVG sprite，无外部图标依赖、无 emoji。

---

## 已知限制

- **桑基图**（`sankey-beta`）的语法解析器不支持中文标签，模板中已注明需使用英文标签。
- **象限图 / XY 图 / 需求图**中的中文文本必须加双引号（模板已按正确写法给出）。
- PNG 导出会按当前主题填充底色（深色主题为深色背景）；如需透明背景可改用 SVG 导出。

---

## License

MIT

---

<div align="center">

<a href="https://github.com/yxpil/drawbuddy">
  <img width="100%" src="https://alittlecatgirlpanel.yxp.hk/card?repo=yxpil/drawbuddy" alt="gh-card · yxpil/drawbuddy" />
</a>

<sub>Powered by <a href="https://alittlecatgirlpanel.yxp.hk"><b>gh-card</b></a> · 粉色手写体 README 仓库名片</sub>

</div>
