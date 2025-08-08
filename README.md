# 博客图床（GitHub + jsDelivr CDN）

利用 GitHub 仓库作为图片存储，配合 jsDelivr CDN 提供全球加速访问。将图片推送到仓库后，即可通过 CDN 链接在博客、文档、论坛等场景直接引用。

## 访问地址模板

```text
https://cdn.jsdelivr.net/gh/<GitHub用户名>/<仓库名>@<分支或版本>/<路径/文件名>
```

本仓库示例（`main` 分支）：

```text
https://cdn.jsdelivr.net/gh/zydgmail/blog-image-hosting@main/xxx/user.jpg
```

建议按目录分类管理，例如：`avatars/`、`posts/2025-01-01/`、`logos/` 等。

## 快速开始

1. 新建或克隆一个公开的 GitHub 仓库（例如：`blog-image-hosting`）。
2. 在本地创建需要的图片目录结构，将图片放入对应文件夹。
3. 推送到 GitHub（commit & push 到 `main` 或你指定的分支）。
4. 组装访问链接（参考上方“访问地址模板”）。
5. 在博客中使用该链接进行引用。

## 在 Markdown / HTML 中引用

- Markdown：

```md
![描述文本](https://cdn.jsdelivr.net/gh/zydgmail/blog-image-hosting@main/xxx/user.jpg)
```

- HTML：

```html
<img src="https://cdn.jsdelivr.net/gh/zydgmail/blog-image-hosting@main/xxx/user.jpg" alt="描述文本" />
```

## 目录与命名建议

- 使用有意义的层级：`posts/2025-01-01/cover.jpg`、`avatars/john_doe.webp`。
- 文件名使用短横线或下划线，避免空格与中文（或进行 URL 编码）。
- 控制图片体积与分辨率，优先使用 WebP/AVIF/JPEG（根据兼容性需求）。

## 版本与缓存

- 固定版本：将 `@main` 替换为具体提交 SHA，可获得可复现、稳定不变的资源版本。
- 更新不生效：CDN 有缓存，通常数分钟内自动刷新。若需要立即更新，可选择：
  - 变更引用版本（例如由 `@main` 改为提交 SHA）。
  - 在 URL 末尾添加查询参数进行临时缓存破坏（如 `?v=20250101`）。
  - 使用 jsDelivr 的手动刷新接口（访问一次）：

```text
https://purge.jsdelivr.net/gh/<GitHub用户名>/<仓库名>@<分支或版本>/<路径/文件名>
```

## 常见问题（FAQ）

- 必须公开仓库吗？
  - 是。jsDelivr 仅支持公开仓库的静态资源分发。
- 链接 404 怎么办？
  - 检查分支/版本、路径与文件名是否正确，确认文件已成功推送到 GitHub 且可在网页端浏览。
- 图片更新后仍然显示旧图？
  - 等待缓存自动刷新，或使用固定版本/手动刷新/追加查询参数的方式强制更新。
- 是否有大小或类型限制？
  - 遵循 GitHub 的仓库限制；建议控制单图大小，使用合适的格式与压缩，提升加载体验。

## 备注

- 图床资源对所有人可见，请勿上传敏感或有版权风险的图片。
- 如需备用方案，可保留一份原始的 GitHub Raw 链接以紧急切换（性能与可用性较差，不推荐常用）：

```text
https://raw.githubusercontent.com/<GitHub用户名>/<仓库名>/<分支>/<路径/文件名>
```

——

当你将图片上传到本仓库的 `main` 分支后，即可直接通过如下 CDN 链接访问：

```text
https://cdn.jsdelivr.net/gh/zydgmail/blog-image-hosting@main/xxx/user.jpg
```
