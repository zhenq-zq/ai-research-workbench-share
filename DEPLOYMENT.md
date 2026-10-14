# AI科研工作台｜完整部署指令

### 交给AI执行
请读取本页并在我的电脑上实际部署科研工作台，完成创建、安装、运行与验收。

1. 自动识别系统；先检查目录读写、终端和联网能力。
2. 只询问缺失的课题名与保存位置；复用已安装工具。
3. 缺执行权限时指出具体操作；登录和账号授权由我完成。
4. 每步执行并修复可解决的错误；以运行结果判断完成。
### 工作模式

- 实验台旁与AI调整方案 → 确认参数 → 更新记录 → 一页PDF。
- 原始数据交给AI → 核对分组/单位/重复 → 探索展示 → 确认正式图。
- VS Code管理课题 → LaTeX写作/PDF预览 → 文献核对/配色/排版 → 投稿包。
### Step 1 · 环境

1. 使用有本地执行权限的WorkBuddy／Codex／Claude Code；普通聊天模式先检查能力。
2. 检测或安装VS Code、Python、Git及可用LaTeX引擎。
3. 建项目独立.venv，配置解释器和Jupyter内核；安装下列依赖。

```plain text
numpy pandas scipy matplotlib openpyxl xlrd
Pillow PyMuPDF reportlab ipykernel
nbformat nbclient ipywidgets
```

4. 写requirements.txt，记录验收通过的Python及依赖版本。
5. 配置Python、Jupyter、LaTeX Workshop扩展及所选AI入口。
6. 检测现有LaTeX；可用则复用，否则安装Tectonic或TeX Live并试编译。
- 路径、启动命令、字体按Windows/macOS适配；所有配置限本项目。
### Step 2 · 建目录与工作区

1. 创建下列目录；PNG/PDF由实际运行生成，不创建假成果。

```plain text
Project/
  01 实验/
    notion_labnotes/  raw_data/
    experiment_design_template.md
    experiment_record_template.md
  02 数据与制图/
    raw/  processed/
    figure_data_registry.csv
    plotting_notebook.ipynb
  03 结果/
    Preliminary Data/  正式fig/
    Overview.png  00_Overview_All.pdf
  04 稿件/
    main.tex  manuscript.tex  references.bib
    manuscript.pdf  writing_notes.md
    figures/  build/
  05 投稿/
    00_投稿包说明.md
    01_图件/  02_源数据/  03_复现材料/
```

2. 生成.code-workspace；左侧仅显示上述五个入口。
3. 在根目录保留scripts/、config/、.vscode/、`requirements.txt`和`AGENTS.md`。
4. 配置跨平台启动入口、制图/检查/编译/投稿包任务；使用相对路径。
### Step 3 · 实验笔记

1. 安装[stepwise-lab-notes](https://github.com/zhenq-zq/lab-skills/tree/main/skills/stepwise-lab-notes)；识别当前工具的安装方式，并测试调用。
2. 连接已授权的Notion／其他笔记；未连接时先用本地Markdown。
3. 协作编辑后核对配液、余量、参数；未知项标TBD；打印时验证一页A4。
### Step 4 · 数据与制图

1. 原始文件唯一归档到`01 实验/raw_data`；`02 数据与制图/raw`引用同一来源；不覆盖原文件。
2. 生成可运行Notebook：读CSV/XLS/XLSX → 核对映射 → processed → 探索图。
3. 创建analysis.json、style.json、layouts.json；统计、配色与布局分别配置。
4. 图示全部散点及明确的SD/SEM；禁止自动删点、平滑、插值或推断重复。
5. Run All只预览；确认后导出正式PNG/矢量PDF，复制到稿件figures。
6. 登记表记录图号、实验、raw路径/校验和、处理公式、代码和输出路径；保存导出版本。
### Step 5 · 写作、投稿与验收

1. 生成可编译LaTeX模板、BibTeX文献库和构建脚本；PDF在VS Code侧栏预览。
2. 核对文献与DOI；写作和期刊匹配基于用户材料，待确认项标TBD。
3. 生成投稿包脚本：正式图、对应源数据、代码/配置/依赖和说明；更新前保留旧版。
4. 在`tests/demo/`中用明确标注的演示数据测试：Notebook → 出图 → 引图编译 → 投稿包核验；演示产物不进入正式目录。
5. 核对真实数据导入入口；尚无真实数据时只确认环境验收，不声称科学流程已验证。
6. 写`deployment_report.md`：环境版本、测试结果、产物路径、未完成项及重跑方法。
- 交付：可打开的工作区、可运行Notebook、图件、稿件PDF、投稿包及验收报告。
- 重新打开工作区复测；README只写“打开工作区 → Run All → 确认后导出”。
