# 博客维护小抄

这个项目是一个 Hugo 静态博客，主题是 `hugo-theme-ladder`。平时主要改 `content`、`static` 和 `config.yml`，一般不要改 `themes` 里的主题源码。

## 常用命令

在项目目录 `/Users/season/Documents/Blog` 里执行：

```bash
hugo server -D
```

本地预览网站。浏览器打开 `http://localhost:1313`。

```bash
hugo --cleanDestinationDir
```

生成正式网站文件。生成结果在 `public` 文件夹里。

## 新建文章

```bash
hugo new content/blog/my-post.md
```

把 `my-post` 换成英文、数字或短横线组成的文件名，比如：

```bash
hugo new content/blog/hello-2026.md
```

然后打开新生成的 Markdown 文件，按这个结构写：

```markdown
---
title: "文章标题"
date: 2026-05-31T20:00:00+08:00
tags: ["生活", "随笔"]
series: []
featured: false
draft: true
---

这里写摘要。

<!--more-->

这里写正文。
```

写完准备发布时，把 `draft: true` 改成：

```yaml
draft: false
```

如果想让文章出现在首页精选区域，把 `featured` 改成 `true`。

## 修改文章

文章都放在：

```text
content/blog/
```

直接修改对应的 `.md` 文件即可。保存后，如果本地预览服务正在运行，网页通常会自动刷新。

## 添加图片

把图片放到：

```text
static/images/postimages/
```

文章里这样引用：

```markdown
![](/images/postimages/图片文件名.jpg)
```

头像和网站图标目前在：

```text
static/images/juan.png
```

## 修改网站信息

主要配置在：

```text
config.yml
```

常改的地方：

- `title`: 网站标题
- `baseURL`: 网站正式地址，目前是 `https://season.zone/`
- `params.author`: 作者名
- `params.info`: 首页个人介绍
- `menu.main`: 顶部菜单

## 发布网站

运行：

```bash
hugo --cleanDestinationDir
```

然后把 `public` 文件夹里的内容发布到你的托管平台。

我目前没有在这个文件夹里看到 Git 仓库记录，所以还不能判断你之前是用 GitHub Pages、Netlify、Vercel，还是手动上传发布的。如果之后想恢复成自动发布，建议把整个项目放进 Git 仓库，而不是只保存 `public`。

常见托管平台设置：

- 构建命令：`hugo --cleanDestinationDir`
- 发布目录：`public`
- Hugo 版本：`0.153.0` 或更新的 extended 版本

## 项目结构

```text
config.yml                 网站配置
content/blog/              文章 Markdown 文件
content/blog.md            文章列表页
content/archives.md        归档页
content/tags.md            标签页
content/guestbook.md       留言板页
static/images/             图片、头像等静态文件
themes/hugo-theme-ladder/  当前主题
public/                    构建生成的网站文件
```

## 小提醒

`public` 是 Hugo 自动生成的结果，平时不要在里面手动改内容。要改网站内容，请改 `content`、`static` 或 `config.yml`，再重新运行构建命令。
