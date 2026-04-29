# Agent Skills（AI 工程技能包）

[English](README.md) | **中文**

**面向 AI 编程代理的生产级工程技能。**

这些技能将资深工程师在软件开发各阶段所用的工作流、质量关卡和最佳实践进行封装，让 AI 代理在每个开发阶段都能一致地遵循它们。

```
  定义            规划           构建          验证          评审            发布
 ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐
 │ 想法 │ ───▶ │ 规格 │ ───▶ │ 代码 │ ───▶ │ 测试 │ ───▶ │ 质检 │ ───▶ │ 上线 │
 │ 精炼 │      │ PRD  │      │ 实现 │      │ 调试 │      │ 关卡 │      │ 部署 │
 └──────┘      └──────┘      └──────┘      └──────┘      └──────┘      └──────┘
  /spec          /plan          /build        /test         /review       /ship
```

---

## 命令

7 条斜杠命令，映射到开发生命周期的各个阶段。每条命令都会自动激活相应的技能。

| 当你在做什么 | 命令 | 核心原则 |
|------------|------|---------|
| 定义要构建的内容 | `/spec` | 先写规格，再写代码 |
| 规划如何构建 | `/plan` | 小步骤，原子任务 |
| 增量构建 | `/build` | 每次只交付一个切片 |
| 证明它可用 | `/test` | 测试即证明 |
| 合并前评审 | `/review` | 提升代码健康度 |
| 简化代码 | `/code-simplify` | 清晰优于聪明 |
| 发布到生产 | `/ship` | 越快越安全 |

技能也会根据你正在做的事自动激活——设计 API 会触发 `api-and-interface-design`，构建 UI 会触发 `frontend-ui-engineering`，以此类推。

---

## 快速上手

<details>
<summary><b>Claude Code（推荐）</b></summary>

**Marketplace 安装：**

```
/plugin marketplace add addyosmani/agent-skills
/plugin install agent-skills@addy-agent-skills
```

> **SSH 报错？** Marketplace 通过 SSH 克隆仓库。如果你的 GitHub 未配置 SSH 密钥，可以[添加 SSH 密钥](https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)，或仅对 fetch 改用 HTTPS：
> ```bash
> git config --global url."https://github.com/".insteadOf "git@github.com:"
> ```

**本地 / 开发模式：**

```bash
git clone https://github.com/addyosmani/agent-skills.git
claude --plugin-dir /path/to/agent-skills
```

</details>

<details>
<summary><b>Cursor</b></summary>

将任意 `SKILL.md` 复制到 `.cursor/rules/`，或引用完整的 `skills/` 目录。详见 [docs/cursor-setup.md](docs/cursor-setup.md)。

</details>

<details>
<summary><b>Gemini CLI</b></summary>

作为原生技能安装以支持自动发现，或添加到 `GEMINI.md` 实现持久上下文。详见 [docs/gemini-cli-setup.md](docs/gemini-cli-setup.md)。

**从仓库安装：**

```bash
gemini skills install https://github.com/addyosmani/agent-skills.git --path skills
```

**从本地克隆安装：**

```bash
gemini skills install ./agent-skills/skills/
```

</details>

<details>
<summary><b>Windsurf</b></summary>

将技能内容添加到 Windsurf 规则配置中。详见 [docs/windsurf-setup.md](docs/windsurf-setup.md)。

</details>

<details>
<summary><b>OpenCode</b></summary>

通过 AGENTS.md 和 `skill` 工具实现代理驱动的技能执行。

详见 [docs/opencode-setup.md](docs/opencode-setup.md)。

</details>

<details>
<summary><b>GitHub Copilot</b></summary>

使用 `agents/` 中的代理定义作为 Copilot 人设，并将技能内容放入 `.github/copilot-instructions.md`。详见 [docs/copilot-setup.md](docs/copilot-setup.md)。

</details>

<details>
  <summary><b>Kiro IDE & CLI</b></summary>
  Kiro 的技能存放在 ".kiro/skills/" 下，可在项目级或全局级使用。Kiro 同样支持 Agents.md。详见 Kiro 文档：https://kiro.dev/docs/skills/
</details>

<details>
<summary><b>Codex / 其他代理</b></summary>

技能均为纯 Markdown 格式——适用于任何接受系统提示或指令文件的代理。详见 [docs/getting-started.md](docs/getting-started.md)。

</details>

---

## 全部 20 个技能

上面的命令是入口点，其背后激活了以下 20 个技能——每个技能都是包含步骤、验证关卡和反合理化表格的结构化工作流。你也可以直接引用任何技能。

### 定义 - 明确要构建什么

| 技能 | 作用 | 使用时机 |
|------|------|---------|
| [idea-refine](skills/idea-refine/SKILL.md) | 结构化发散/收敛思维，将模糊想法转化为具体提案 | 有粗略概念需要深化探索时 |
| [spec-driven-development](skills/spec-driven-development/SKILL.md) | 在写任何代码前，编写涵盖目标、命令、结构、代码风格、测试和边界的 PRD | 启动新项目、新功能或重大变更时 |

### 规划 - 任务拆解

| 技能 | 作用 | 使用时机 |
|------|------|---------|
| [planning-and-task-breakdown](skills/planning-and-task-breakdown/SKILL.md) | 将规格拆解为带有验收标准和依赖排序的小型可验证任务 | 已有规格、需要可实现的最小单元时 |

### 构建 - 编写代码

| 技能 | 作用 | 使用时机 |
|------|------|---------|
| [incremental-implementation](skills/incremental-implementation/SKILL.md) | 薄垂直切片——实现、测试、验证、提交。功能标记、安全默认值、支持回滚的变更 | 任何涉及多于一个文件的变更 |
| [test-driven-development](skills/test-driven-development/SKILL.md) | 红-绿-重构，测试金字塔（80/15/5），测试规模，DAMP 优于 DRY，Beyonce 规则，浏览器测试 | 实现逻辑、修复 Bug 或变更行为时 |
| [context-engineering](skills/context-engineering/SKILL.md) | 在正确的时间为代理提供正确的信息——规则文件、上下文打包、MCP 集成 | 开启新会话、切换任务或输出质量下降时 |
| [source-driven-development](skills/source-driven-development/SKILL.md) | 将每个框架决策建立在官方文档基础上——验证、引用来源、标记未经验证的内容 | 希望获得任何框架或库的权威引用代码时 |
| [frontend-ui-engineering](skills/frontend-ui-engineering/SKILL.md) | 组件架构、设计系统、状态管理、响应式设计、WCAG 2.1 AA 无障碍 | 构建或修改面向用户的界面时 |
| [api-and-interface-design](skills/api-and-interface-design/SKILL.md) | 契约优先设计、Hyrum 定律、One-Version 规则、错误语义、边界验证 | 设计 API、模块边界或公共接口时 |

### 验证 - 证明它可用

| 技能 | 作用 | 使用时机 |
|------|------|---------|
| [browser-testing-with-devtools](skills/browser-testing-with-devtools/SKILL.md) | Chrome DevTools MCP 用于实时运行时数据——DOM 检查、控制台日志、网络追踪、性能分析 | 构建或调试任何在浏览器中运行的内容时 |
| [debugging-and-error-recovery](skills/debugging-and-error-recovery/SKILL.md) | 五步分类法：复现、定位、缩小范围、修复、防护。停止规则、安全回退 | 测试失败、构建中断或行为异常时 |

### 评审 - 合并前的质量关卡

| 技能 | 作用 | 使用时机 |
|------|------|---------|
| [code-review-and-quality](skills/code-review-and-quality/SKILL.md) | 五轴评审，变更规模（约 100 行），严重性标签（Nit/Optional/FYI），评审速度规范，拆分策略 | 合并任何变更之前 |
| [code-simplification](skills/code-simplification/SKILL.md) | Chesterton 之栅栏、500 行规则，在保持精确行为的前提下降低复杂性 | 代码能运行但难以阅读或维护时 |
| [security-and-hardening](skills/security-and-hardening/SKILL.md) | OWASP Top 10 防护、认证模式、密钥管理、依赖审计、三层边界系统 | 处理用户输入、认证、数据存储或外部集成时 |
| [performance-optimization](skills/performance-optimization/SKILL.md) | 先度量的方法——Core Web Vitals 目标、分析工作流、包体积分析、反模式检测 | 存在性能要求或怀疑出现性能回退时 |

### 发布 - 有信心地部署

| 技能 | 作用 | 使用时机 |
|------|------|---------|
| [git-workflow-and-versioning](skills/git-workflow-and-versioning/SKILL.md) | 主干开发、原子提交、变更规模（约 100 行）、提交即存档点模式 | 进行任何代码变更时（始终适用） |
| [ci-cd-and-automation](skills/ci-cd-and-automation/SKILL.md) | Shift Left、越快越安全、功能标记、质量关卡流水线、失败反馈循环 | 建立或修改构建和部署流水线时 |
| [deprecation-and-migration](skills/deprecation-and-migration/SKILL.md) | 代码即负债思维、强制性与建议性弃用、迁移模式、僵尸代码清除 | 下线旧系统、迁移用户或淘汰功能时 |
| [documentation-and-adrs](skills/documentation-and-adrs/SKILL.md) | 架构决策记录（ADR）、API 文档、内联文档规范——记录*为什么* | 做出架构决策、变更 API 或交付功能时 |
| [shipping-and-launch](skills/shipping-and-launch/SKILL.md) | 发布前检查清单、功能标记生命周期、分阶段发布、回滚流程、监控设置 | 准备部署到生产环境时 |

---

## 代理人设

预配置的专家人设，用于定向评审：

| 代理 | 角色 | 视角 |
|------|------|------|
| [code-reviewer](agents/code-reviewer.md) | 资深 Staff 工程师 | 五轴代码评审，标准为"Staff 工程师会批准这个吗？" |
| [test-engineer](agents/test-engineer.md) | QA 专家 | 测试策略、覆盖率分析和 Prove-It 模式 |
| [security-auditor](agents/security-auditor.md) | 安全工程师 | 漏洞检测、威胁建模、OWASP 评估 |

---

## 参考检查清单

技能按需引用的快速参考材料：

| 参考 | 涵盖内容 |
|------|---------|
| [testing-patterns.md](references/testing-patterns.md) | 测试结构、命名、Mock、React/API/E2E 示例、反模式 |
| [security-checklist.md](references/security-checklist.md) | 提交前检查、认证、输入验证、Headers、CORS、OWASP Top 10 |
| [performance-checklist.md](references/performance-checklist.md) | Core Web Vitals 目标、前后端检查清单、度量命令 |
| [accessibility-checklist.md](references/accessibility-checklist.md) | 键盘导航、屏幕阅读器、视觉设计、ARIA、测试工具 |

---

## 技能的工作原理

每个技能都遵循统一的结构：

```
┌─────────────────────────────────────────────────┐
│  SKILL.md                                       │
│                                                 │
│  ┌─ 前置元数据 ──────────────────────────────┐  │
│  │ name: lowercase-hyphen-name               │  │
│  │ description: 引导代理完成 [任务]。        │  │
│  │              在以下情况使用…              │  │
│  └───────────────────────────────────────────┘  │
│  Overview（概述）    → 此技能的作用             │
│  When to Use（时机） → 触发条件                 │
│  Process（流程）     → 分步工作流               │
│  Rationalizations   → 常见借口 + 反驳           │
│  Red Flags（红旗）   → 出错的信号               │
│  Verification（验证）→ 证据要求                 │
└─────────────────────────────────────────────────┘
```

**关键设计选择：**

- **流程，而非散文。** 技能是代理遵循的工作流，而非阅读的参考文档。每个技能都有步骤、检查点和退出条件。
- **反合理化。** 每个技能都包含一张代理常用的跳过步骤借口表（如"我之后再加测试"），以及有据可查的反驳论点。
- **验证不可妥协。** 每个技能都以证据要求结尾——测试通过、构建输出、运行时数据。"看起来没问题"永远不够。
- **渐进式披露。** `SKILL.md` 是入口点，支撑性参考资料仅在需要时加载，将 Token 消耗降至最低。

---

## 项目结构

```
agent-skills/
├── skills/                            # 20 个核心技能（每个目录一个 SKILL.md）
│   ├── idea-refine/                   #   定义
│   ├── spec-driven-development/       #   定义
│   ├── planning-and-task-breakdown/   #   规划
│   ├── incremental-implementation/    #   构建
│   ├── context-engineering/           #   构建
│   ├── source-driven-development/     #   构建
│   ├── frontend-ui-engineering/       #   构建
│   ├── test-driven-development/       #   构建
│   ├── api-and-interface-design/      #   构建
│   ├── browser-testing-with-devtools/ #   验证
│   ├── debugging-and-error-recovery/  #   验证
│   ├── code-review-and-quality/       #   评审
│   ├── code-simplification/          #   评审
│   ├── security-and-hardening/        #   评审
│   ├── performance-optimization/      #   评审
│   ├── git-workflow-and-versioning/   #   发布
│   ├── ci-cd-and-automation/          #   发布
│   ├── deprecation-and-migration/     #   发布
│   ├── documentation-and-adrs/        #   发布
│   ├── shipping-and-launch/           #   发布
│   └── using-agent-skills/            #   元信息：如何使用此技能包
├── agents/                            # 3 个专家人设
├── references/                        # 4 个补充检查清单
├── hooks/                             # 会话生命周期钩子
├── .claude/commands/                  # 7 条斜杠命令（Claude Code）
├── .gemini/commands/                  # 7 条斜杠命令（Gemini CLI）
└── docs/                              # 各工具的配置指南
```

---

## 为什么需要 Agent Skills？

AI 编程代理默认选择最短路径——这往往意味着跳过规格、测试、安全评审以及使软件可靠所需的实践。Agent Skills 为代理提供结构化工作流，执行与资深工程师带给生产代码相同的规范。

每个技能都凝结了来之不易的工程判断：*何时*写规格、*测试什么*、*如何*评审，以及*何时*发布。这些不是通用提示词——它们是将生产级工作与原型级工作区分开的、有主见的、流程驱动的工作流。

技能内置了来自 Google 工程文化的最佳实践——包括[《Google 软件工程》](https://abseil.io/resources/swe-book)和 Google [工程实践指南](https://google.github.io/eng-practices/)中的概念。你会在 API 设计中看到 Hyrum 定律，在测试中看到 Beyonce 规则和测试金字塔，在代码评审中看到变更规模和评审速度规范，在简化中看到 Chesterton 之栅栏，在 Git 工作流中看到主干开发，在 CI/CD 中看到 Shift Left 和功能标记，以及一个将代码视为负债的专用弃用技能。这些不是抽象原则——它们直接嵌入代理所遵循的分步工作流中。

---

## 贡献

技能应当**具体**（可操作的步骤，而非模糊建议）、**可验证**（有证据要求的明确退出条件）、**经过实战检验**（基于真实工作流）且**精简**（只包含引导代理所需的内容）。

详见 [docs/skill-anatomy.md](docs/skill-anatomy.md) 中的格式规范和 [CONTRIBUTING.md](CONTRIBUTING.md) 中的贡献指南。

---

## 许可证

MIT——你可以在自己的项目、团队和工具中使用这些技能。
