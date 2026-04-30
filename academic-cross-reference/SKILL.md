---
name: academic-cross-reference
description: Adds bidirectional hyperlinks between in-text citations and reference lists in Word documents. Invoke when user requests cross-referencing for academic papers or thesis documents.
---

# Academic Cross Reference

为学术论文自动添加参考文献交叉引用功能，实现正文角标与参考文献列表之间的双向跳转。

## 功能特性

1. **智能识别**：自动识别文档中的参考文献列表（识别「参考文献」标题及 `[1]`, `[2]` 等编号格式）
2. **书签添加**：为每篇参考文献添加内部书签标记
3. **超链接转换**：将正文中的引用角标 `[1]` 转换为可点击的超链接，点击即可跳转到对应参考文献
4. **格式保持**：保持原文档格式不变，仅添加超链接功能
5. **支持 GB/T 7714-2015** 标准引用格式

## 使用方法

### 方式一：直接调用

告诉 AI "为我的文档添加交叉引用"，AI 会自动执行脚本处理。

### 方式二：手动运行

```bash
cd /path/to/environmental-research-grandmaster/academic-cross-reference
python scripts/add_crossref.py <输入文件.docx> <输出文件.docx>
```

## 依赖安装

```bash
pip install python-docx
```

## 工作流程

1. 读取输入的 `.docx` 文件
2. 定位「参考文献」章节
3. 提取所有参考文献编号
4. 为每个参考文献添加 XML 书签（bookmarkStart/bookmarkEnd）
5. 遍历正文段落，找到所有 `[n]` 格式的引用角标
6. 将角标替换为带超链接的 XML 元素
7. 保存为新文件

## 注意事项

- 参考文献列表需以「参考文献」为标题
- 引用格式需为 `[1]`, `[2]` 等方括号数字格式
- 角标与参考文献编号必须一一对应
- 处理不会修改原文档内容，仅添加超链接功能
- 支持中英文混合文档

## 输出示例

处理后，点击正文中的 `[1]` 会直接跳转到文末对应的参考文献条目，方便读者查阅。
