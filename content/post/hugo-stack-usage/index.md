---
title: "Hugo Stack Usage"
description: Hugo 主题 Stack 使用注意事项
date: 2022-09-30T02:02:10+08:00
draft: false

image: 
tags: ["gohugo"]
license: CC BY-NC-ND
---

# Hugo 主题 Stack 的使用

[Hugo Theme](https://themes.gohugo.io/themes/hugo-theme-stack/) & [项目地址](https://github.com/CaiJimmy/hugo-theme-stack) & [官方文档](https://stack.jimmycai.com/)

``` Q&A
- 为什么不用 [hugo-theme-stack-starter](https://github.com/CaiJimmy/hugo-theme-stack-starter)

    主要还是不知道这个项目具体比 Hugo + theme 的方式做多了什么，后期迁移方不方便、后期修改 theme 方不方便，基于这样的考虑所以不用 starter 项目来创建
```

## 注意事项
### 1. 文章默认放置在 `content/post` 目录下
在 [hugo-theme-stack/config.yaml](https://github.com/CaiJimmy/hugo-theme-stack/blob/master/config.yaml) 中可以配置，可覆盖

``` yaml
params:
    mainSections:
        - post # 这里指定了
```

### 2. 默认文章的组织格式有要求
如 [Writing/Markdown](https://stack.jimmycai.com/writing/markdown) 所述，MD 书写的目录结构应为 `content/post/<post-title>/index.md` 

```
content
└── post
    └── my-first-post
        ├── index.md
        ├── image1.png
        └── image2.png
```

这算是对 [Hugo/Content Organization](https://gohugo.io/content-management/organization/) 的更严格限制

### 3. 默认配置并不能达到 Demo 的效果
[项目地址](https://github.com/CaiJimmy/hugo-theme-stack) 里有个目录 `exampleSite`，里面有 Demo 的配置（该目录的内容极具参考意义）。

如果使用 `git submodule add` 的方式引入该主题，submodule 所在目录就有 [项目地址](https://github.com/CaiJimmy/hugo-theme-stack) 的内容（如果使用 go module 方式，则需要打开项目地址手动拷贝）

需要做：
1. 使用 exampleSite/config.yaml 替换 `hugo new site xxx` 自动生成的 config.toml（或按需补充）
2. 将 exampleSite/content/page 和 exampleSite/content/categoties 两个目录及其内容复制到使用 `hugo new site xxx` 自动生成的 content 目录里
3. 按需修改上面两步涉及的内容
4. （可选）将 exampleSite/archetypes 下的内容复制到使用 `hugo new site xxx` 自动生成的 archetypes 目录里，目录的含义参考 [Directory Structure](https://gohugo.io/getting-started/directory-structure/)