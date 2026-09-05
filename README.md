# devflow · 通用软件交付方法论 (Agent Skill Group)

一套**与具体技术栈、业务无关**的端到端软件研发方法论，沉淀为 15 个可被任意 AI Agent（QoderWork / Codex / Claude 等）加载调用的 skill。任何软件项目——Web 应用、内部工具、API 服务、移动端、数据系统——都能按这套流程从"模糊想法"走到"可交付成果"。

## 黄金法则：先对话，后执行

任何开发动作之前，必须先完成需求对话（`devflow-requirements`）并形成书面《需求结论纪要》。不允许跳过对话直接写代码。这是整套方法论的第一原则。

## 快速开始

把 `skills/` 下所有 `devflow*` 文件夹整体拷贝到你的 AI Agent 的 skills 目录即可。以 QoderWork 为例：

```bash
cp -R skills/devflow* ~/.qoderworkcn/skills/
```

拷贝后刷新 skill 列表，`devflow` 即可作为编排入口被触发（说"我要开发一个软件系统""按方法论开发""端到端交付流程"等）。其他 Agent 工具请拷贝到其对应的 skill 目录。

## 全流程管线（14 阶段 / 15 skill）

| 阶段 | Skill | 产出物 |
|---|---|---|
| 编排 | `devflow` | 总控入口，承载黄金法则与全局工程纪律 |
| 0 对话 | `devflow-requirements` | 需求结论纪要 |
| 1 需求 | `devflow-prd` | PRD 需求文档 |
| 2 产品 | `devflow-product-definition` | 角色 / 模块 / 功能矩阵 |
| 3 架构 | `devflow-architecture` | 架构设计 + 目录结构 + ADR |
| 4 原型 | `devflow-prototype` | 页面原型 / 线框 |
| 5 设计 | `devflow-design-style` | 设计 token + 美术规范 |
| 6 技术栈 | `devflow-tech-stack` | 选型方法 + 版本锁定清单 |
| 7 规范 | `devflow-code-conventions` | 语言无关代码约束 |
| 8 前端 | `devflow-frontend-dev` | 页面 + 组件实现规范 |
| 9 后端 | `devflow-backend-dev` | API + 业务逻辑规范 |
| 10 数据库 | `devflow-database` | 数据建模 + 变更 SOP |
| 11 测试 | `devflow-testing` | 分层测试策略 + 冒烟 + 报告 |
| 12 部署 | `devflow-deployment` | 部署流程 + 运维 |
| 13 文档 | `devflow-docs` | 交付文档（手册 / 报告 / 交接） |

> 阶段可并行：产品定义 / 架构 / 原型 / 设计 / 技术栈 / 数据库可在 PRD 确定后并行推进；前后端开发在数据模型和约定确定后并行。

## 全局工程纪律（所有子 skill 共同遵守）

- **文档先行**：每阶段产出物落盘，经确认再进入下一阶段。
- **事实落盘**：项目具体事实（技术栈版本、路径、命名、约定）写进《项目事实文件》（如 `DEVELOPMENT_GUIDE.md` / `AGENTS.md`），而非塞进通用方法论。
- **依赖方向单一**：分层清晰，禁止循环依赖。
- **边界即校验**：外部输入、跨层调用一律先校验。
- **写操作要原子**：多表 / 多步写入用事务。
- **可追溯**：关键流程写操作留痕（只增不改不删）。
- **不臆造**：未知信息用 `XXX` 占位，绝不瞎编事实性数据。

## 目录结构

```
devflow-agent-skills/
├── README.md
├── LICENSE                 # Apache-2.0
├── .gitignore
└── skills/
    ├── devflow/SKILL.md            # 编排入口
    ├── devflow-requirements/SKILL.md
    ├── devflow-prd/SKILL.md
    ├── ...（共 15 个）
    └── devflow-docs/SKILL.md
```

## 设计说明：方法论 vs 项目事实

这套 skill 刻意**不含**任何固定框架版本、项目路径、具体数据库 schema 或业务模型——那些属于"项目事实"，应该写进你自己项目的《项目事实文件》。方法论只固化"怎么做、按什么顺序做、守什么纪律"。

因此它可以复用到任意软件项目：加载 skill → 先做需求对话 → 把对话结论和项目技术事实写进你的 `AGENTS.md` / `DEVELOPMENT_GUIDE.md` → 按管线逐阶段推进。

## License

[Apache License 2.0](LICENSE)
