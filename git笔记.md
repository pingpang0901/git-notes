# Git 笔记

## 一、Git 是什么

Git（版本控制）：通俗理解，就是一个保存代码、程序、软件历代版本的软件。

## 二、仓库（Repository）

Git 的仓库分为本地仓库和远端仓库两类。

### 2.1 本地仓库

Local Repository：本地仓库。

### 2.2 远端仓库

Remote Repository：远端仓库。

### 2.3 GitHub

GitHub：一个提供 Remote Repository 的网页。

## 三、把项目上传到 GitHub

整体流程：先在 GitHub 上创建仓库，再在 agent 中打开项目文件夹，最后初始化并推送。

1. 在 GitHub 上创建仓库。
2. 记住要上传的项目所在文件夹，在 agent 里选择该文件夹。
3. 发送提示词：

> 把这个文件夹初始化成 git 项目，并且推送到 GitHub 上面

### 3.1 初始化仓库

`git init`（init：初始化）：在 VSCode 中通过「文件 → 打开文件夹 → Source Control」初始化仓库。

### 3.2 .gitignore

`.gitignore`：声明哪些文件不受到 Git 管理，在里面输入文件名即可。

为了避免把无关文件一起上传，可以使用优化后的提示词：

> 把这个文件夹初始化成 git 项目，注意把不需要的内容排除掉，并且推送到 GitHub 上面

## 四、提交与版本历史（Commit）

每次提交都会形成一次 commit，commit 链就是项目的历史版本。

### 4.1 查看某个历史版本

- **方法一**：将鼠标移到要查看的版本，右击鼠标，点击 Checkout（Detached）〔签出（已分离）〕。
- **方法二**：在历史版本上直接创建分支。

### 4.2 Detached

Detached：分离头指针，表示不处于任何一个分支中。

## 五、版本回退与撤销

### 5.1 将仓库回退到某个历史版本

鼠标移到历史版本，右击鼠标，点击 Copy Commit Hash（复制提交哈希），发给 agent：

> 你把仓库还原到 {commit id}，这次提交的状态，后面的所有改动都不要了。

### 5.2 撤掉某次错误提交而不改动其他提交

发给 agent：

> 你把这一次提交撤销掉：{commit id}，保持其他不变。

### 5.3 比较两个版本之间的修改

发给 agent：

> 比较一下 {commit id1} 和 {commit id2} 提交修改了什么内容

## 六、Worktree（工作树）

Worktree：创建主文件分支，对分支的修改不会影响主文件，可以在分支上进行开发测试，最后可以合并到主文件中。

## 七、Git 分区（Git Areas）

Git 分区及数据流向如下图所示：

![Git 分区示意图：工作区、本地仓库与远端仓库](assets/git-areas.png)

## 八、与远端仓库协作

### 8.1 克隆远端仓库

复制 GitHub 仓库地址，在 VSCode 中选择「文件 → Source Control → 克隆仓库」。

### 8.2 推送到远端仓库

在 VSCode 里打开文件夹，选择「Source Control → 提交代码 → 发布 Branch → 选择账户」。

## 九、GitHub 快捷键

| 快捷键 | 功能 |
| --- | --- |
| `/` | 搜索栏 |
| `T` | 文件搜索栏 |
| `L` | 快速查看代码行 |
| `?` | 查看快捷键 |
| `.` | 网页版 VSCode |

## 十、下载安装 Claude 时遇到的问题

### 10.1 运行 Set-ExecutionPolicy 报错

直接使用终端运行 `Set-ExecutionPolicy Unrestricted` 会报错，需要以管理员身份运行终端。

### 10.2 运行 node -v 报错

终端运行 `node -v` 报错，说明电脑上没有安装 Node，需要到 Node 官网下载安装。

### 10.3 .claude.json 中 DeepSeek 的 URL 配置错误

创建 `.claude.json` 时，文本内容中 DeepSeek 的 URL 应使用 `https://api.deepseek.com/anthropic`，而不是 `https://api.deepseek.com`。
