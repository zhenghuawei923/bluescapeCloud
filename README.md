# bluescapeCloud
Bluescape Cloud File Downloader - A Windows desktop application for downloading files from json including  Cloud links of files.

## 项目概览

**蓝景云文件下载器** - 一个 Windows 桌面应用，用于从腾讯云下载文件。

### 项目结构

```
tencent_downloader/
├── api/client.py           # API 客户端（登录、获取文件树、下载文件）
├── core/
│   ├── download_manager.py # 下载管理器（并发控制、进度追踪）
│   ├── download_task.py    # 下载任务
│   └── file_tree_manager.py # 文件树管理器
├── ui/
│   ├── main_window.py      # 主窗口
│   ├── login_page.py       # 登录页面
│   ├── file_browser_page.py # 文件浏览页面（树形展示）
│   ├── download_page.py    # 下载页面
│   └── settings_dialog.py  # 设置对话框
├── utils/style.py          # Apple 风格样式
├── config.py               # 配置管理
└── main.py                 # 程序入口
```

### 核心功能

1. **Key 码登录验证** - 通过 key 码登录系统
2. **文件树浏览** - 树形展示文件结构，支持展开/折叠
3. **多文件选择** - 支持勾选多个文件/文件夹
4. **并发下载** - 最多 5 个并发下载任务
5. **实时进度** - 显示每个文件的下载进度条
6. **失败重试** - 自动重试 3 次
7. **状态统计** - 显示总文件数、下载中、成功、失败数量
8. **自定义下载位置** - 可选择保存路径

### 技术栈

- **PyQt6** - GUI 框架
- **requests** - HTTP 请求
- **QThreadPool** - 线程池管理并发下载

### API 接口

后端运行在 `http://localhost:5000`，提供：
- `POST /api/login` - 登录验证
- `GET /api/files` - 获取文件树
- `GET /api/json` - 获取 JSON 文件

### 配置

配置文件：`~/.tencent_downloader/config.json`
- 默认下载路径
- 是否记住下载路径
- 最大并发下载数
