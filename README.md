# Health-Reminder 便携版自动构建

本项目不包含任何源代码，仅通过 GitHub Actions 自动从 [kaima2022/Health-reminder](https://github.com/kaima2022/Health-reminder) 上游仓库拉取最新源码，构建并发布 **便携版（免安装）** 和 **安装版（NSIS）** 的 Windows 可执行文件。

## 为什么有这个仓库？

- 上游官方只提供 NSIS 安装包，没有便携版（Portable）。
- 通过 CI 自动化构建，无需在本地搭建 Rust 和 Node.js 环境。
- 每天自动检查更新，你随时可以获取最新版本。

## 如何获取最新版本？

有两种方式：

### 1. 从 Releases 下载（推荐）

访问本仓库的 [Releases 页面](https://github.com/YOUR_USERNAME/health-reminder-portable/releases)（将 YOUR_USERNAME 替换为你的 GitHub 用户名），每次构建成功后会自动创建一个预发布（Pre-release），其中包含两个附件：

- `Health-Reminder-Portable-vX.X.X.zip` — 便携版压缩包，解压后双击 `health-reminder.exe` 即可运行，无需安装。
- `Health-Reminder-Setup-vX.X.X.exe` — 标准 NSIS 安装包，双击安装后使用（与原官方版一致）。

### 2. 从 Actions Artifacts 下载（最新构建）

进入本仓库的 [Actions 页面](https://github.com/YOUR_USERNAME/health-reminder-portable/actions)，选择最近一次成功的工作流运行，在底部 **Artifacts** 区域可以下载 `Health-Reminder-Builds.zip`，其中包含上述两个文件。

## 自动构建计划

- 每天 UTC 2:00（北京时间 10:00）自动触发一次构建。
- 你也可以手动触发：进入 Actions 页面，选择 `Build Installer + Portable`，点击 **Run workflow** 即可立即构建最新版。

## 文件命名规则

- 便携版 ZIP：`Health-Reminder-Portable-v{版本号}.zip`
- 安装版 EXE：`Health-Reminder-Setup-v{版本号}.exe`

版本号与上游项目 `tauri.conf.json` 中的 `version` 字段保持一致。

## 与原版有什么区别？

| 特性 | 本仓库构建版 | 上游官方版 |
|------|------------|----------|
| 便携版（免安装） | ✅ 提供 | ❌ 不提供 |
| 安装版（NSIS） | ✅ 提供 | ✅ 提供 |
| 自动更新器签名 | ❌ 已禁用 | ✅ 有（使用官方私钥） |
| 代码完整性 | 从上游源码构建，功能一致 | 官方构建 |

如果你只需要便携版，下载 ZIP 即可；如果你需要安装版，也可一同获取。

## 许可证

本仓库仅包含 CI 配置文件，构建产物基于上游项目的 [MIT 许可证](https://github.com/kaima2022/Health-reminder/blob/main/LICENSE)。使用本构建产物即表示你同意遵守原项目的许可证条款。

