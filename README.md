# S.S.T.G. · Simple Seamless Texture Generator

> 一个纯浏览器端的**无缝迷彩 / 纹理生成器**（Simple Seamless Texture Generator）。7 种图案类型、实时参数调节、2×2 平铺验证、PNG / SVG 导出。零依赖，单 HTML 文件，打开就能用。

**在线体验 / Live Demo:** <https://plasticpinaceae.github.io/Pinaceae/>

![status](https://img.shields.io/badge/status-online-brightgreen) ![deps](https://img.shields.io/badge/dependencies-0-blue) ![stack](https://img.shields.io/badge/stack-vanilla%20JS-yellow) ![license](https://img.shields.io/badge/license-MIT-orange)

---

## 这是什么

S.S.T.G. 是一个**在浏览器里直接生成 4 方连续（seamless）纹理**的工具：图案上下左右无缝拼接，适合做游戏贴图、背景底纹、迷彩布料、印花等需要重复平铺的场景。

- **7 种纹理类型**：经典迷彩、数码迷彩、有机/丛林、等高线/地形、反应-扩散、碎片迷彩、眩目迷彩
- 每种类型都有**内置预设**，配上侧栏参数（种子、配色、缩放、扭曲……）实时调节
- **2×2 平铺预览** 实时验证接缝是否真无缝（`✓ 无缝` / `⚠ 检测到接缝`）
- **一键导出**：单张 PNG、2×2 PNG，反应-扩散图案还可导出 **SVG 矢量**（线条可无限放大）
- **反应-扩散**支持上传图片作为「扩散起点」，图案沿你的图形轮廓生长（保留原比例、可反相）
- **快照**功能，随手保存多个版本对比挑选
- 中英双语界面，深色 UI + 金色高亮（`#c8a84e`）

技术栈：**纯原生 HTML + CSS + JavaScript**，无框架、无构建、无 npm，`<canvas>` 渲染。

## 使用说明

打开 [在线地址](https://plasticpinaceae.github.io/Pinaceae/) 即可，无需安装。

1. **选纹理类型** — 在左侧「纹理类型」里挑一种（迷彩 / 地形 / 反应-扩散 等）。
2. **选预设** — 点「预设」里的方块套用一套现成风格，右上角小 `i` 可看说明。
3. **调参数** — 拖动「参数」区的滑杆（配色、缩放、扭曲、阈值等），中央画布**实时更新**。
4. **随机生成** — 点 `🎲 随机生成` 换一版；想保留某部分不变，可**锁定**种子 / 配色 / 图案 / 扭曲后再随机。
5. **验证无缝** — 开 `2×2 平铺` 看四块拼接的接缝，顶部状态显示 `✓ 无缝` 说明可安全平铺；`网格` 辅助对齐。
6. **存快照** — 满意的版本点 `+ 保存快照` 存起来，方便多版对比。
7. **导出**
   - `📥 导出贴图`：导出单张无缝 PNG
   - `📥 导出 2×2`：导出 2×2 平铺后的 PNG
   - `📐 导出 SVG`：导出矢量线条（**仅反应-扩散**类型可用，可无限缩放不糊）
   - 可在「导出尺寸」里选输出分辨率

### 反应-扩散进阶（图生纹理）

- **懒人调节**（主题金色高亮）：`线条密度` / `线条粗细` 两个滑杆，不用懂参数也能快速出图。
- **上传孔位**：点 `⬆ 上传孔位` 或直接把图片**拖进来**，图案会沿你上传图形的轮廓作为「扩散起点」生长。
  - 上传的图片**保留原始比例**（居中留白填充，不会被拉伸变形）
  - 可勾选 `反相蒙版` 切换生长的内外区域
- 想矢量输出时用 `📐 导出 SVG`，线条连续无碎片、跨平铺接缝也连续。

## 目录说明

```
sstg/repo/
├── index.html              ← 主程序（HTML/CSS/JS 全部内联）
├── fonts/
│   ├── MicrogrammaD-Bold.otf
│   └── MicrogrammaD-Medium.otf
├── AI_CONTEXT.md           ← 项目背景与设计约定（写给 AI 协作者）
├── README.md               ← 你正在看的
├── LICENSE                 ← MIT
└── dev.ps1                 ← 一键本地起服务器（Windows）
```

> **仓库命名说明**：GitHub 仓库名是历史遗留的 `Pinaceae`（作者账号主题），但**项目正式名是 `S.S.T.G.`**。为不破坏 GitHub Pages 的 URL，仓库名保持不变，代码与文档一律以 `S.S.T.G.` 为准。

## 本地开发

### 方式 1：双击 `index.html`
最快，但 `file://` 协议下浏览器**可能拒绝加载 .otf 字体**（会回退到 Inter/系统字体）。要看完整效果请用方式 2。

### 方式 2：本地静态服务器（推荐）

Windows PowerShell：

```powershell
cd D:\dev\sstg\repo
./dev.ps1        # 启动 python http.server 并打开浏览器
```

或手动：

```powershell
cd D:\dev\sstg\repo
python -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 部署

推送到 `main` 分支后，GitHub Pages 会在 1–2 分钟内自动更新：

```bash
git add .
git commit -m "feat: xxx"
git push
```

线上地址：<https://plasticpinaceae.github.io/Pinaceae/>

## 给 AI 协作者

如果你是 AI，接手这个项目前请**先读 [`AI_CONTEXT.md`](./AI_CONTEXT.md)**，
它提供了项目身份、设计约定与协作准则（尤其：别再把它当成旧的「CRT 扫描器」）。

## License

[MIT](./LICENSE) — 请注明出处。

---

> Vibe Coding 项目，作者 [@plasticpinaceae](https://github.com/plasticpinaceae)。
