# 理货大师 Tidy Master — 离线完整版

2D 网页休闲小游戏，纯前端单页实现，**无任何网络依赖**（图形为本地 SVG，音效为 WebAudio 实时合成）。

## 目录结构

```
理货大师-离线版/
├── index.html            # 游戏主文件（入口）
├── README.md             # 本说明
└── assets/               # 全部图片资源（相对路径引用）
    ├── items/            # 货架商品图标
    │   ├── apple.svg     苹果
    │   ├── banana.svg    香蕉
    │   ├── grape.svg     葡萄
    │   ├── carrot.svg    胡萝卜
    │   ├── broccoli.svg  西兰花
    │   ├── tomato.svg    番茄
    │   ├── juice.svg     果汁
    │   └── milk.svg      牛奶
    └── ui/               # 界面图标
        ├── logo.svg      游戏图标（兼 favicon）
        ├── cat-fruit.svg 水果区图标
        ├── cat-veg.svg   蔬菜区图标
        └── cat-drink.svg 饮料区图标
```

## 运行方式

- **直接双击 `index.html`** 即可在浏览器中离线运行（所有资源走相对路径，无需服务器）。
- 建议使用 Chrome / Edge / Firefox / Safari 现代版本。

## 玩法

1. 货架上随机摆放并部分重叠堆放着水果、蔬菜、饮料；被上层挡住（重叠 >30%）的商品无法拖动。
2. 按住商品**拖拽**到底部对应大类的筐里松手：拖进正确的筐即整理成功，进度 +1、连击 +1。
3. 拖进**错误**的筐会扣 10 秒并断连击；拖到筐外则自动弹回货架。
4. 在倒计时内清空全部商品即过关，按剩余时间比例评定 1–3 星；剩余 10 秒时会响起倒计时提示音。
5. 共 10 关：第 1–3 关两排货架，第 4 关起升级为三排；商品种类随关卡递增（3 → 8 种）。

## 部署到 Netlify

方式一（拖拽）：把整个 `理货大师-离线版` 文件夹拖到 Netlify Drop 页面即可。
方式二（Git）：将本目录作为仓库根目录，Build command 留空，Publish directory 填 `.`。
发布后入口为 `https://<站点名>.netlify.app/index.html`。

## 技术说明

- 单文件 HTML + 原生 JS，无框架、无构建步骤、无 CDN。
- 关卡配置位于 `index.html` 中的 `LEVELS` 数组（件数 / 种类 / 时限），与规则逻辑分离，便于调参。
- 星级、关卡解锁进度、静音状态保存在浏览器 `localStorage`。
