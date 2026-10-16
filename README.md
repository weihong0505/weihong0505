<div align="center">

# 魏毅鸿 · Yihong Wei

**大一 · 金融工程 · 广州城市理工学院** ｜ 方向：LLM 工程 / AI 应用

把本地大模型、多智能体工作流和自动化管线，做成**真能跑、能复现、能审计**的东西。

</div>

---

## 项目

| 仓库 | 一句话 | 技术 |
|---|---|---|
| [**ai-collaboration-notes**](https://github.com/weihong0505/ai-collaboration-notes) | **一个人 + 多个 AI 代理的工程方法论**：怎么让产出可证伪、审查有对账压力、失败无法静默。提炼自 41 份项目复盘（约 44 万字符） | 方法论 · 对抗性审查 · 失败模式 |
| [**local-llm-forensics**](https://github.com/weihong0505/local-llm-forensics) | 不加载模型，从 GGUF 头与 Ollama manifest 判断「这个模型到底是什么」；并测量人格漂移、上下文行为、指令优先级 | GGUF · Ollama · 因子式探针 · 长程召回 |
| [**npu-decision-engine**](https://github.com/weihong0505/npu-decision-engine) | 量化 Intel NPU 跑 LLM 推理到底值不值 | OpenVINO · ONNX · INT4 · 基准工程 |
| [**ai-audiovisual-perception**](https://github.com/weihong0505/ai-audiovisual-perception) | 给纯文本 LLM 装本地「眼睛和耳朵」：多路连续录制 + 片段级时序理解 + 检索问答 | faster-whisper · Qwen2.5-VL · SQLite FTS5 · Ollama |
| [**compliance-gated-content-pipeline**](https://github.com/weihong0505/compliance-gated-content-pipeline) | 模型无权下裁决：确定性许可证引擎 + LLM 生成 + 对抗性复核 + 人工审核门 | Python · 状态机 · 规则引擎 · LLM API |
| [**quant-investing**](https://github.com/weihong0505/quant-investing) | A 股量化方法论知识库：因子检验方法论 / 回测工程规范 / **全 A 5,179 只 × 116 个月因子检验** | Python · 面板数据 · PIT 审计 · 去偏夏普 |
| [**wx-announcer**](https://github.com/weihong0505/wx-announcer) | 微信 4.x 群公告助手：监听 @所有人 → AI 提炼 → 转发（打包 exe） | Python · UIAutomation · PyInstaller |

---

## 几个我比较在意的结论

> **四个核心因子（EP / BP / ROE_TTM / GPM）在全 A 5,179 只 × 116 个月上全部淘汰。**
> 含 GPM 那种「几乎完美的不显著」（p = 0.8291）。报告里专门写了「未做选择性报告」。
> —— [quant-investing / 全 A 因子检验](https://github.com/weihong0505/quant-investing)

> **一个致命 bug 曾让回测结论翻转：** `nav2.index = nav1.index[:len(nav2)]` 使 2x 成本序列
> 整体早标一个月，丢掉 2019-02 的 +22.0%。由独立对抗性审查抓出，**首版错误结论保留在报告里备审计**。
> —— 同上，`reports/backtest_v21/report.md` §6

> **架构保证要分层声称：「写入点受控」≠「判定正确」。**
> —— compliance-gated-content-pipeline，三轮独立评审里最有价值的一次纠偏

> **NPU 适合静态形状的编码器前向（比 CPU 快约 3×），不适合自回归解码（比 CPU 慢约 5.5×）。**
> —— npu-decision-engine，附完整复现脚本与溯源字段

> **FTS5 的 `MATCH` 短语直接拼接用户输入可被引号注入。**
> —— ai-audiovisual-perception，由独立对抗性审查实测出，按 TDD 修复并补回归测试

---

## 工作方式

每个项目都强制留一份 `REVIEW.md`，逐轮记录 **做了什么 / 关键决策 / 踩了什么坑 / 下一步**，
累计 **80+ 份、约 90 万字符**。所以任何一个项目，我都能完整讲出
「从发现问题 → 设计方案 → 交付 → 发现自己的错 → 修掉」的全过程。

- **独立对抗性审查是默认动作，不是可选项** —— 它替我在多个项目里抓出过 load-bearing 缺陷
- **审查结论不照单全收**：曾用中国结算三份原文裁决，推翻一次审查意见（表种错配）
- **写失败，不藏失败**：`npu-decision-engine` 里那行「189 ms（历史值，**现不可复现**）」留在表里不删
- 改代码前先备份快照；结论必须可复现：脚本 + 溯源字段 + 归档原始结果

---

<sub>📮 正在找 **远程 AI 工程 / AI 应用 / AI 产品** 实习 ｜ 每周可投入 15 小时，全程远程</sub>
