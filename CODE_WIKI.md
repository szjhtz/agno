# Agno Code Wiki

## 项目概述

### 项目简介
Agno 是一个用于构建、运行和管理智能代理软件的完整运行时框架。该项目提供了一套丰富的工具和库，使开发者能够快速构建具有记忆、知识、安全护栏等功能的智能代理系统。

**项目信息：**
- 项目名称：agno
- 版本：2.5.16
- 主要用途：构建、运行和管理代理型软件
- 开发语言：Python (>=3.7, <4)
- 许可证：Apache Software License

### 核心价值主张
Agno 解决了代理型软件开发的三个根本性转变：

1. **新的交互模型** - 将流式处理和长时间运行的执行作为一等公民行为
2. **新的治理模型** - 提供审批工作流、人工干预、审计日志和运行时强制实施
3. **新的信任模型** - 在引擎本身中内置信任机制，包括安全护栏、评估集成和可追踪性

## 目录结构

### 核心源代码
```
libs/agno/agno/
├── agent/              # 单代理实现
├── team/               # 多代理团队实现
├── workflow/           # 工作流实现
├── os/                 # AgentOS 运行时
├── models/             # 模型集成 (Anthropic, OpenAI, Google等)
├── tools/              # 工具集 (100+ 集成)
├── knowledge/          # 知识管理和RAG
├── memory/             # 记忆管理
├── learn/              # 学习能力
├── db/                 # 数据库集成
├── vectordb/           # 向量数据库集成
├── guardrails/         # 安全护栏
├── hooks/              # 钩子系统
├── approval/           # 审批系统
├── scheduler/          # 调度器
├── tracing/            # 可追踪性
├── api/                # API 实现
├── client/             # 客户端实现
├── skills/             # 技能系统
├── reasoning/          # 推理能力
├── compression/        # 上下文压缩
├── culture/            # 文化知识管理
├── registry/           # 组件注册表
├── remote/             # 远程组件支持
├── run/                # 运行时管理
├── session/            # 会话管理
├── media/              # 多媒体支持
├── metrics/            # 指标收集
├── eval/               # 评估系统
├── utils/              # 工具函数
├── exceptions.py       # 异常定义
├── filters.py          # 过滤器
├── media.py            # 媒体处理
├── metrics.py          # 指标
├── table.py            # 表格
└── __init__.py         # 包初始化
```

### 主要辅助库
```
libs/
├── agno/               # 核心库
└── agno_infra/         # 基础设施库 (AWS, Docker等)
```

### 示例和文档
```
cookbook/               # 丰富的示例代码库
├── 00_quickstart/      # 快速入门示例
├── 01_demo/            # 演示示例
├── 02_agents/          # 代理深入学习
├── 03_teams/           # 团队示例
├── 04_workflows/       # 工作流示例
├── 05_agent_os/        # AgentOS 示例
├── 06_storage/         # 存储示例
├── 07_knowledge/       # 知识管理示例
├── 08_learning/        # 学习示例
├── 09_evals/           # 评估示例
├── 10_reasoning/       # 推理示例
├── 11_memory/          # 记忆示例
├── 90_models/          # 模型集成示例
├── 91_tools/           # 工具使用示例
├── 92_integrations/    # 第三方集成示例
└── 93_components/      # 组件示例
```

## 核心架构

### 三层架构
Agno 采用三层架构设计：

1. **框架层** - 构建代理、团队和工作流，包含记忆、知识、安全护栏和100+ 集成
2. **运行时层** - 使用无状态、会话范围的 FastAPI 后端在生产环境中提供服务
3. **控制平面层** - 使用 AgentOS UI 测试、监控和管理系统

### 核心概念

#### 1. 代理 (Agent)
单个智能代理单元，具有以下特性：
- 可配置的大语言模型
- 工具调用能力
- 会话管理
- 记忆管理
- 知识检索 (RAG)
- 安全护栏
- 推理能力
- 多模态支持

**主要文件：** [libs/agno/agno/agent/agent.py](file:///workspace/libs/agno/agno/agent/agent.py)

#### 2. 团队 (Team)
多个代理的协作集合，具有以下特性：
- 团队成员管理
- 协作模式配置
- 任务分配
- 共享状态

**主要文件：** [libs/agno/agno/team/team.py](file:///workspace/libs/agno/agno/team/team.py)

#### 3. 工作流 (Workflow)
结构化的执行流程，具有以下特性：
- 步骤定义
- 条件分支
- 循环执行
- 并行处理
- 路由选择

**主要文件：** [libs/agno/agno/workflow/workflow.py](file:///workspace/libs/agno/agno/workflow/workflow.py)

#### 4. AgentOS
生产环境运行时，具有以下特性：
- FastAPI 后端
- RESTful API
- WebSocket 支持
- 数据库集成
- 可追踪性
- 认证和授权
- 调度器

**主要文件：** [libs/agno/agno/os/app.py](file:///workspace/libs/agno/agno/os/app.py)

## 主要模块职责

### 1. 代理模块 (agent/)
负责单个智能代理的核心功能。

#### 关键文件：
- `agent.py` - 主 Agent 类定义
- `_run.py` - 代理执行逻辑
- `_session.py` - 会话管理
- `_storage.py` - 持久化存储
- `_tools.py` - 工具管理
- `_messages.py` - 消息处理
- `_hooks.py` - 钩子系统
- `_managers.py` - 管理器实现
- `_response.py` - 响应处理
- `_cli.py` - 命令行界面

### 2. 团队模块 (team/)
负责多代理团队的协作功能。

#### 关键文件：
- `team.py` - 主 Team 类定义
- `mode.py` - 团队协作模式
- `task.py` - 任务定义
- `_run.py` - 团队执行逻辑
- `_session.py` - 团队会话管理
- `_storage.py` - 团队持久化

### 3. 工作流模块 (workflow/)
负责结构化工作流的执行。

#### 关键文件：
- `workflow.py` - 主 Workflow 类定义
- `step.py` - 步骤定义
- `steps.py` - 多步骤管理
- `condition.py` - 条件步骤
- `loop.py` - 循环步骤
- `parallel.py` - 并行步骤
- `router.py` - 路由步骤
- `agent.py` - 工作流代理
- `types.py` - 类型定义

### 4. AgentOS 模块 (os/)
提供生产环境运行时功能。

#### 关键文件：
- `app.py` - 主 AgentOS 类
- `config.py` - 配置定义
- `auth.py` - 认证
- `managers.py` - 管理器
- `mcp.py` - MCP 协议支持
- `router.py` - 路由
- `schema.py` - 模式定义
- `scopes.py` - 作用域
- `settings.py` - 设置
- `utils.py` - 工具函数
- `interfaces/` - 接口实现
- `middleware/` - 中间件
- `routers/` - API 路由

### 5. 模型模块 (models/)
集成多种大语言模型提供商。

#### 支持的模型：
- Anthropic (Claude)
- OpenAI (GPT系列)
- Google (Gemini)
- Azure OpenAI
- AWS Bedrock
- Mistral
- Cohere
- Groq
- Ollama
- Together
- VLLM
- 以及更多...

#### 关键文件：
- `base.py` - 基础模型类
- `message.py` - 消息定义
- `response.py` - 响应处理
- `fallback.py` - 降级配置
- `metrics.py` - 指标
- `defaults.py` - 默认配置

### 6. 工具模块 (tools/)
提供100+ 预构建工具集成。

#### 工具分类：
- **Web 搜索** - Tavily, DuckDuckGo, SerpAPI等
- **数据库** - PostgreSQL, MySQL, SQLite, Redis等
- **API 集成** - GitHub, GitLab, Jira, Slack, Discord等
- **文件处理** - PDF, Excel, CSV, Docx等
- **云服务** - AWS, GCP, Azure等
- **金融** - Yahoo Finance, Alpha Vantage等
- **AI/ML** - DALL-E, Stable Diffusion等
- **以及更多**

#### 关键文件：
- `decorator.py` - 工具装饰器
- `function.py` - 函数工具
- `toolkit.py` - 工具包基类
- `tool_registry.py` - 工具注册表
- `mcp/` - MCP 工具集成
- `google/` - Google 服务工具

### 7. 知识模块 (knowledge/)
提供知识管理和 RAG 功能。

#### 关键组件：
- **知识源** - 文档加载、网页抓取等
- **分块策略** - 固定大小、递归、语义等
- **嵌入器** - OpenAI, Cohere, HuggingFace等
- **重排器** - Cohere, Infinity等
- **检索器** - 向量搜索、混合搜索等

#### 关键文件：
- `knowledge.py` - 主 Knowledge 类
- `content.py` - 内容管理
- `filesystem.py` - 文件系统知识
- `protocol.py` - 知识协议
- `remote_knowledge.py` - 远程知识
- `chunking/` - 分块策略
- `embedder/` - 嵌入器
- `reader/` - 文档读取器
- `loaders/` - 加载器
- `reranker/` - 重排器
- `document/` - 文档处理

### 8. 记忆模块 (memory/)
提供用户记忆管理功能。

#### 关键文件：
- `manager.py` - MemoryManager 类
- `strategies/` - 记忆策略
  - `base.py` - 基础策略
  - `summarize.py` - 摘要策略
  - `types.py` - 类型定义

### 9. 学习模块 (learn/)
提供学习和自我改进能力。

#### 关键文件：
- `machine.py` - LearningMachine 类
- `config.py` - 配置
- `curate.py` - 学习内容整理
- `schemas.py` - 模式定义
- `stores/` - 存储实现
  - `decision_log.py` - 决策日志
  - `entity_memory.py` - 实体记忆
  - `learned_knowledge.py` - 学习知识
  - `user_memory.py` - 用户记忆
  - `user_profile.py` - 用户画像

### 10. 数据库模块 (db/)
提供多种数据库集成。

#### 支持的数据库：
- SQLite
- PostgreSQL
- MySQL
- MongoDB
- Redis
- JSON 文件
- SurrealDB
- DynamoDB
- Firestore
- GCS
- 以及更多...

#### 关键文件：
- `base.py` - 基础数据库类
- `filter_converter.py` - 过滤器转换
- `utils.py` - 工具函数
- `schemas/` - 数据库模式
  - `knowledge.py`
  - `memory.py`
  - `metrics.py`
  - `culture.py`
  - `evals.py`
- `sqlite/` - SQLite 实现
- `mysql/` - MySQL 实现
- `redis/` - Redis 实现
- `json/` - JSON 实现

### 11. 向量数据库模块 (vectordb/)
提供向量数据库集成。

#### 支持的向量数据库：
- ChromaDB
- Qdrant
- Pinecone
- Weaviate
- Milvus
- PGVector (PostgreSQL)
- LanceDB
- MongoDB
- Cassandra
- ClickHouse
- SurrealDB
- 以及更多...

#### 关键文件：
- `base.py` - 基础向量数据库类
- `search.py` - 搜索功能
- `distance.py` - 距离计算
- `score.py` - 评分
- `chroma/` - ChromaDB 实现
- `qdrant/` - Qdrant 实现
- `pineconedb/` - Pinecone 实现
- `pgvector/` - PGVector 实现
- `weaviate/` - Weaviate 实现

### 12. 安全护栏模块 (guardrails/)
提供内容安全和验证功能。

#### 关键文件：
- `base.py` - 基础护栏类
- `openai.py` - OpenAI 内容审核
- `pii.py` - PII 检测
- `prompt_injection.py` - 提示注入检测

### 13. 审批模块 (approval/)
提供审批工作流功能。

#### 关键文件：
- `decorator.py` - 审批装饰器
- `types.py` - 类型定义

### 14. 调度器模块 (scheduler/)
提供定时任务调度功能。

#### 关键文件：
- `manager.py` - 调度器管理器
- `poller.py` - 轮询器
- `executor.py` - 执行器
- `cron.py` - Cron 表达式处理
- `cli.py` - 命令行界面

### 15. 可追踪性模块 (tracing/)
提供 OpenTelemetry 集成。

#### 关键文件：
- `exporter.py` - 追踪导出器
- `schemas.py` - 模式定义
- `setup.py` - 设置

### 16. 推理模块 (reasoning/)
提供分步推理能力。

#### 关键文件：
- `manager.py` - 推理管理器
- `step.py` - 推理步骤
- `anthropic.py` - Anthropic 推理
- `openai.py` - OpenAI 推理
- `gemini.py` - Gemini 推理
- `helpers.py` - 辅助函数

### 17. 钩子模块 (hooks/)
提供钩子系统。

#### 关键文件：
- `decorator.py` - 钩子装饰器

### 18. 技能模块 (skills/)
提供技能系统。

#### 关键文件：
- `skill.py` - Skill 类
- `agent_skills.py` - 代理技能
- `errors.py` - 错误定义
- `utils.py` - 工具函数
- `validator.py` - 验证器

### 19. API 模块 (api/)
提供 RESTful API 实现。

#### 关键文件：
- `api.py` - API 基类
- `agent.py` - 代理 API
- `team.py` - 团队 API
- `workflow.py` - 工作流 API
- `os.py` - AgentOS API
- `evals.py` - 评估 API
- `schemas/` - API 模式
  - `agent.py`
  - `team.py`
  - `workflows.py`
  - `os.py`
  - `response.py`
  - `evals.py`
  - `utils.py`

### 20. 客户端模块 (client/)
提供客户端实现。

#### 关键文件：
- `os.py` - AgentOS 客户端
- `a2a/` - Agent-to-Agent 通信
  - `client.py`
  - `schemas.py`
  - `utils.py`

## 关键类与函数

### Agent 类
核心代理类，提供单个智能代理的所有功能。

**位置：** [libs/agno/agno/agent/agent.py](file:///workspace/libs/agno/agno/agent/agent.py#L69)

**主要属性：**
- `model` - 使用的大语言模型
- `name` - 代理名称
- `id` - 代理唯一标识符
- `db` - 数据库连接
- `tools` - 可用工具列表
- `knowledge` - 知识源
- `memory_manager` - 记忆管理器
- `session_state` - 会话状态
- `system_message` - 系统提示
- `instructions` - 指令列表
- `description` - 代理描述

**主要方法：**
```python
# 同步执行
def run(
    self,
    input: Union[str, List, Dict, Message, BaseModel, List[Message]],
    *,
    stream: bool = False,
    stream_events: Optional[bool] = None,
    session_id: Optional[str] = None,
    session_state: Optional[Dict[str, Any]] = None,
    **kwargs
) -> Union[RunOutput, Iterator[RunOutputEvent]]:
    """执行代理并返回结果"""

# 异步执行
async def arun(
    self,
    input: Union[str, List, Dict, Message, BaseModel, List[Message]],
    *,
    stream: bool = False,
    **kwargs
) -> Union[RunOutput, AsyncIterator[RunOutputEvent]]:
    """异步执行代理"""

# 会话管理
def get_session(self, session_id: Optional[str] = None, user_id: Optional[str] = None) -> Optional[AgentSession]:
    """获取会话"""

def save_session(self, session: AgentSession) -> None:
    """保存会话"""

# 存储
def save(self, *, db: Optional[BaseDb] = None, stage: str = "published") -> Optional[int]:
    """保存代理到数据库"""

@classmethod
def load(cls, id: str, *, db: BaseDb) -> Optional[Agent]:
    """从数据库加载代理"""

# 工具
def add_tool(self, tool: Union[Toolkit, Callable, Function, Dict]) -> None:
    """添加工具"""

# CLI
def print_response(self, input: Any, **kwargs) -> None:
    """在控制台打印响应"""
```

### Team 类
多代理团队类，协调多个代理的协作。

**位置：** [libs/agno/agno/team/team.py](file:///workspace/libs/agno/agno/team/team.py#L73)

**主要属性：**
- `members` - 团队成员列表 (Agent 或 Team)
- `model` - 团队协调模型
- `name` - 团队名称
- `id` - 团队唯一标识符
- `mode` - 团队协作模式
- `respond_directly` - 是否直接响应
- `delegate_to_all_members` - 是否委派给所有成员
- `max_iterations` - 最大迭代次数

**主要方法：**
```python
# 执行
def run(self, input: Any, *, stream: bool = False, **kwargs) -> Union[TeamRunOutput, Iterator]:
    """执行团队"""

async def arun(self, input: Any, *, stream: bool = False, **kwargs) -> Union[TeamRunOutput, AsyncIterator]:
    """异步执行团队"""

# 成员管理
def initialize_team(self, debug_mode: Optional[bool] = None) -> None:
    """初始化团队"""
```

### Workflow 类
工作流类，定义结构化的执行流程。

**位置：** [libs/agno/agno/workflow/workflow.py](file:///workspace/libs/agno/agno/workflow/workflow.py#L212)

**主要属性：**
- `name` - 工作流名称
- `id` - 工作流唯一标识符
- `steps` - 工作流步骤
- `db` - 数据库连接
- `agent` - 工作流代理
- `session_state` - 会话状态

**主要方法：**
```python
# 执行
def run(self, input: Any, *, stream: bool = False, **kwargs) -> Union[WorkflowRunOutput, Iterator]:
    """执行工作流"""

async def arun(self, input: Any, *, stream: bool = False, **kwargs) -> Union[WorkflowRunOutput, AsyncIterator]:
    """异步执行工作流"""

# 会话管理
def get_session(self, session_id: Optional[str] = None) -> Optional[WorkflowSession]:
    """获取工作流会话"""

# 存储
def save(self, *, db: Optional[BaseDb] = None, stage: str = "published") -> Optional[int]:
    """保存工作流"""

@classmethod
def load(cls, id: str, *, db: BaseDb) -> Optional[Workflow]:
    """加载工作流"""
```

### Step 类
工作流中的单个步骤。

**位置：** [libs/agno/agno/workflow/step.py](file:///workspace/libs/agno/agno/workflow/step.py)

**主要类型：**
- `Step` - 单个步骤
- `Steps` - 多个步骤序列
- `Condition` - 条件分支
- `Loop` - 循环
- `Parallel` - 并行执行
- `Router` - 路由选择

### AgentOS 类
生产环境运行时类，提供 API 服务。

**位置：** [libs/agno/agno/os/app.py](file:///workspace/libs/agno/agno/os/app.py#L190)

**主要属性：**
- `agents` - 代理列表
- `teams` - 团队列表
- `workflows` - 工作流列表
- `knowledge` - 知识库列表
- `db` - 数据库连接
- `registry` - 组件注册表
- `tracing` - 是否启用追踪
- `authorization` - 是否启用认证
- `scheduler` - 是否启用调度器

**主要方法：**
```python
def get_app(self) -> FastAPI:
    """获取 FastAPI 应用"""

def resync(self, app: FastAPI) -> None:
    """重新同步 AgentOS"""

def get_routes(self) -> List[Any]:
    """获取所有路由"""
```

### Knowledge 类
知识管理类，提供 RAG 功能。

**位置：** [libs/agno/agno/knowledge/knowledge.py](file:///workspace/libs/agno/agno/knowledge/knowledge.py)

**主要属性：**
- `name` - 知识名称
- `content` - 知识内容
- `vector_db` - 向量数据库
- `contents_db` - 内容数据库
- `embedder` - 嵌入器
- `chunking_strategy` - 分块策略
- `reranker` - 重排器

**主要方法：**
```python
def add(self, content: Any) -> None:
    """添加内容到知识库"""

def search(self, query: str, num_documents: int = 5) -> List[Dict]:
    """搜索知识库"""

async def asearch(self, query: str, num_documents: int = 5) -> List[Dict]:
    """异步搜索知识库"""
```

### MemoryManager 类
记忆管理器类。

**位置：** [libs/agno/agno/memory/manager.py](file:///workspace/libs/agno/agno/memory/manager.py)

**主要方法：**
```python
def add_memory(self, user_id: str, memory: str) -> str:
    """添加记忆"""

def search_memories(self, user_id: str, query: str) -> List[UserMemory]:
    """搜索记忆"""

def get_memories(self, user_id: str) -> List[UserMemory]:
    """获取所有记忆"""
```

### LearningMachine 类
学习机类，提供自我改进能力。

**位置：** [libs/agno/agno/learn/machine.py](file:///workspace/libs/agno/agno/learn/machine.py)

### Model 基类
所有模型的基类。

**位置：** [libs/agno/agno/models/base.py](file:///workspace/libs/agno/agno/models/base.py)

**主要实现：**
- `AnthropicClaude` - Anthropic Claude 模型
- `OpenAIChat` - OpenAI GPT 模型
- `GoogleGemini` - Google Gemini 模型
- 以及更多...

### BaseDb 基类
所有数据库的基类。

**位置：** [libs/agno/agno/db/base.py](file:///workspace/libs/agno/agno/db/base.py)

**主要实现：**
- `SqliteDb` - SQLite 数据库
- `PostgresDb` - PostgreSQL 数据库
- `MongoDb` - MongoDB 数据库
- `RedisDb` - Redis 数据库
- 以及更多...

### BaseVectorDb 基类
所有向量数据库的基类。

**位置：** [libs/agno/agno/vectordb/base.py](file:///workspace/libs/agno/agno/vectordb/base.py)

**主要实现：**
- `ChromaDb` - ChromaDB
- `Qdrant` - Qdrant
- `PineconeDb` - Pinecone
- 以及更多...

## 依赖关系

### 核心依赖
```toml
# 核心库
docstring-parser
gitpython
h11>=0.16.0
httpx[http2]
packaging
pydantic-settings
pydantic
python-dotenv
python-multipart
pyyaml
rich
typer
typing-extensions
```

### 可选依赖组

#### AgentOS 运行时
```toml
agno[os] = [
    "fastapi[standard]",
    "uvicorn",
    "sqlalchemy",
    "PyJWT",
    "opentelemetry-sdk",
    "openinference-instrumentation-agno",
    "croniter>=1.3",
    "pytz>=2023.3"
]
```

#### 模型集成
```toml
# Anthropic
agno[anthropic] = ["anthropic"]

# OpenAI
agno[openai] = ["openai"]

# Google
agno[google] = ["google-genai>=1.52.0"]

# AWS Bedrock
agno[aws-bedrock] = ["boto3", "aioboto3"]

# Azure
agno[azure] = ["azure-ai-inference", "aiohttp"]

# Mistral
agno[mistral] = ["mistralai"]

# Cohere
agno[cohere] = ["cohere"]

# Groq
agno[groq] = ["groq"]

# Ollama
agno[ollama] = ["ollama"]

# Together
agno[together] = ["together"]
```

#### 工具集成
```toml
# Web 搜索
agno[tavily] = ["tavily-python"]
agno[ddg] = ["ddgs"]
agno[exa] = ["exa_py"]

# 数据库
agno[postgres] = ["psycopg-binary"]
agno[duckdb] = ["duckdb"]

# 文件处理
agno[pdf] = ["pypdf", "rapidocr_onnxruntime"]
agno[docx] = ["python-docx"]
agno[excel] = ["openpyxl", "xlrd"]

# API 集成
agno[github] = ["PyGithub"]
agno[gitlab] = ["python-gitlab", "httpx"]
agno[slack] = ["slack_sdk>=3.40.0"]
agno[discord] = [...]

# MCP
agno[mcp] = ["mcp>=1.9.2"]
```

#### 存储
```toml
# SQL
agno[sql] = ["sqlalchemy"]
agno[sqlite] = ["sqlalchemy", "aiosqlite"]
agno[postgres] = ["psycopg-binary"]
agno[async_postgres] = ["asyncpg"]
agno[mysql] = ["pymysql", "asyncmy"]

# NoSQL
agno[async_mongo] = ["pymongo>=4.9", "motor"]
agno[redis] = ["redis", "redisvl>=0.12.1"]

# 云存储
agno[gcs] = ["google-cloud-storage"]
agno[firestore] = ["google-cloud-firestore"]
```

#### 向量数据库
```toml
agno[chromadb] = ["chromadb"]
agno[qdrant] = ["qdrant-client"]
agno[pinecone] = ["pinecone==5.4.2"]
agno[weaviate] = ["weaviate-client"]
agno[milvusdb] = ["pymilvus>=2.5.10"]
agno[pgvector] = ["pgvector"]
agno[lancedb] = ["lancedb>=0.26.0", "tantivy"]
```

#### 可观测性
```toml
agno[opentelemetry] = ["opentelemetry-sdk", "opentelemetry-exporter-otlp"]
agno[arize] = ["arize-phoenix", ...]
agno[langfuse] = ["langfuse"]
agno[weave] = ["weave"]
```

#### 调度器
```toml
agno[scheduler] = ["croniter>=1.3", "pytz>=2023.3"]
```

## 项目运行方式

### 安装

#### 基础安装
```bash
pip install agno
```

#### 完整安装 (包含 AgentOS)
```bash
pip install "agno[os]"
```

#### 特定功能安装
```bash
# 安装带 OpenAI 支持
pip install "agno[openai]"

# 安装带 Anthropic 支持
pip install "agno[anthropic]"

# 安装带 AgentOS 和多个模型
pip install "agno[os,openai,anthropic]"
```

### 快速开始

#### 1. 基础代理
```python
from agno.agent import Agent
from agno.models.openai import OpenAIChat

agent = Agent(
    model=OpenAIChat(id="gpt-4"),
    description="你是一个有用的助手。"
)

agent.print_response("你好！")
```

#### 2. 带工具的代理
```python
from agno.agent import Agent
from agno.models.anthropic import Claude
from agno.tools.duckduckgo import DuckDuckGoTools

agent = Agent(
    model=Claude(id="claude-3-sonnet-4-6"),
    tools=[DuckDuckGoTools()],
    show_tool_calls=True
)

agent.print_response("搜索今天的新闻")
```

#### 3. 带记忆的代理
```python
from agno.agent import Agent
from agno.models.openai import OpenAIChat
from agno.db.sqlite import SqliteDb
from agno.memory import MemoryManager

agent = Agent(
    model=OpenAIChat(id="gpt-4"),
    db=SqliteDb(db_file="agent.db"),
    memory_manager=MemoryManager(),
    enable_agentic_memory=True,
    add_history_to_context=True
)

agent.print_response("我的名字是 Alice")
agent.print_response("我叫什么名字？")  # 会记住！
```

#### 4. 带知识的代理 (RAG)
```python
from agno.agent import Agent
from agno.models.anthropic import Claude
from agno.knowledge import Knowledge
from agno.vectordb.chroma import ChromaDb

knowledge = Knowledge(
    content=["path/to/documents"],
    vector_db=ChromaDb()
)

agent = Agent(
    model=Claude(id="claude-3-sonnet-4-6"),
    knowledge=knowledge,
    add_knowledge_to_context=True
)

agent.print_response("根据文档回答问题")
```

#### 5. 代理团队
```python
from agno.agent import Agent
from agno.team import Team
from agno.models.openai import OpenAIChat

researcher = Agent(
    name="研究员",
    model=OpenAIChat(id="gpt-4"),
    role="负责研究和收集信息"
)

writer = Agent(
    name="作家",
    model=OpenAIChat(id="gpt-4"),
    role="负责撰写报告"
)

team = Team(
    name="研究团队",
    members=[researcher, writer],
    mode="round_robin"
)

team.print_response("写一份关于 AI 的报告")
```

#### 6. 工作流
```python
from agno.workflow import Workflow, Step
from agno.agent import Agent
from agno.models.openai import OpenAIChat

# 定义步骤
step1 = Step(
    name="分析",
    agent=Agent(model=OpenAIChat(id="gpt-4"), instructions="分析输入")
)

step2 = Step(
    name="生成",
    agent=Agent(model=OpenAIChat(id="gpt-4"), instructions="生成输出")
)

# 创建工作流
workflow = Workflow(
    name="分析工作流",
    steps=[step1, step2]
)

# 执行工作流
workflow.print_response("处理这个任务")
```

#### 7. AgentOS (生产环境)
```python
from agno.agent import Agent
from agno.models.anthropic import Claude
from agno.db.sqlite import SqliteDb
from agno.os import AgentOS

# 创建代理
agent = Agent(
    name="助手",
    model=Claude(id="claude-3-sonnet-4-6"),
    db=SqliteDb(db_file="agno.db"),
    add_history_to_context=True
)

# 创建 AgentOS
agent_os = AgentOS(
    agents=[agent],
    db=SqliteDb(db_file="agno.db"),
    tracing=True
)

# 获取 FastAPI 应用
app = agent_os.get_app()

# 运行服务
# uvicorn main:app --reload
```

### 使用 uvx 快速运行
```bash
export ANTHROPIC_API_KEY="your-api-key"

uvx --python 3.12 \
  --with "agno[os]" \
  --with anthropic \
  --with mcp \
  fastapi dev agno_assist.py
```

## 配置选项

### 环境变量
```bash
# 模型 API 密钥
OPENAI_API_KEY=your-openai-key
ANTHROPIC_API_KEY=your-anthropic-key
GOOGLE_API_KEY=your-google-key

# 数据库
DATABASE_URL=postgresql://user:pass@host/db

# AgentOS
AGNO_TELEMETRY=false  # 禁用遥测
OS_SECURITY_KEY=your-security-key
JWT_VERIFICATION_KEY=your-jwt-key

# 调试
AGNO_DEBUG=true
```

### 代理配置
```python
agent = Agent(
    # 模型
    model=OpenAIChat(id="gpt-4"),
    fallback_models=[OpenAIChat(id="gpt-3.5-turbo")],
    
    # 基础
    name="我的代理",
    description="一个有用的代理",
    
    # 会话
    session_id="my-session",
    session_state={"key": "value"},
    add_session_state_to_context=True,
    
    # 历史
    add_history_to_context=True,
    num_history_runs=5,
    
    # 工具
    tools=[...],
    tool_call_limit=10,
    
    # 知识
    knowledge=...,
    add_knowledge_to_context=True,
    
    # 记忆
    memory_manager=...,
    enable_agentic_memory=True,
    
    # 推理
    reasoning=True,
    reasoning_model=...,
    
    # 系统提示
    system_message="...",
    instructions=[...],
    
    # 响应
    output_schema=MyPydanticModel,
    markdown=True,
    stream=True,
    
    # 调试
    debug_mode=True,
    telemetry=True
)
```

## 测试

### 运行测试
```bash
# 单元测试
pytest tests/unit/

# 集成测试
pytest tests/integration/

# 系统测试
cd tests/system
./run_tests.sh
```

### 测试文件位置
- `libs/agno/tests/unit/` - 单元测试
- `libs/agno/tests/integration/` - 集成测试
- `libs/agno/tests/system/` - 系统测试

## Cookbook 示例

项目包含丰富的示例代码，位于 [cookbook/](file:///workspace/cookbook) 目录：

- `00_quickstart/` - 快速入门
- `01_demo/` - 演示应用
- `02_agents/` - 代理深入教程
  - `02_input_output/` - 输入输出处理
  - `03_context_management/` - 上下文管理
  - `05_state_and_session/` - 状态和会话
  - `06_memory_and_learning/` - 记忆和学习
  - `07_knowledge/` - 知识管理
  - `08_guardrails/` - 安全护栏
  - `09_hooks/` - 钩子系统
  - `10_human_in_the_loop/` - 人工干预
  - `11_approvals/` - 审批工作流
  - `12_multimodal/` - 多模态
  - `13_reasoning/` - 推理
  - `14_advanced/` - 高级功能
  - `15_dependencies/` - 依赖管理
  - `16_skills/` - 技能
  - `17_fallback_models/` - 降级模型
- `03_teams/` - 团队示例
- `04_workflows/` - 工作流示例
- `05_agent_os/` - AgentOS 示例
  - `advanced_demo/` - 高级演示
  - `approvals/` - 审批
  - `background_tasks/` - 后台任务
  - `client/` - 客户端
  - `client_a2a/` - Agent-to-Agent
  - `customize/` - 自定义
  - `dbs/` - 数据库集成
  - `interfaces/` - 接口
  - `knowledge/` - 知识
  - `mcp_demo/` - MCP 演示
  - `middleware/` - 中间件
  - `os_config/` - 配置
  - `remote/` - 远程
  - `scheduler/` - 调度器
  - `tracing/` - 追踪
  - `workflow/` - 工作流
- `06_storage/` - 存储示例
- `07_knowledge/` - 知识深入教程
- `08_learning/` - 学习示例
- `09_evals/` - 评估示例
- `10_reasoning/` - 推理示例
- `11_memory/` - 记忆示例
- `90_models/` - 模型示例
- `91_tools/` - 工具示例
- `92_integrations/` - 集成示例
- `93_components/` - 组件示例

## 贡献指南

请参阅 [CONTRIBUTING.md](file:///workspace/CONTRIBUTING.md) 了解如何贡献代码。

## 许可证

Apache Software License - 详见 [LICENSE](file:///workspace/LICENSE) 文件。

## 相关链接

- **官方网站:** https://agno.com
- **文档:** https://docs.agno.com
- **GitHub:** https://github.com/agno-agi/agno
- **Discord:** https://www.agno.com/discord

## 总结

Agno 是一个功能全面的代理型软件开发框架，提供了从单个代理到复杂多代理系统的完整解决方案。其核心优势包括：

1. **丰富的集成** - 100+ 工具、50+ 模型、多种数据库和向量数据库
2. **生产就绪** - AgentOS 提供完整的 API、认证、可追踪性和监控
3. **灵活的架构** - 支持代理、团队和工作流三种构建模式
4. **企业特性** - 安全护栏、审批工作流、审计日志等
5. **活跃的社区** - 丰富的示例、文档和支持

无论您是构建简单的聊天机器人还是复杂的企业级代理系统，Agno 都提供了所需的所有工具和基础设施。
