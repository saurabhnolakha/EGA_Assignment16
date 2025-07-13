# 🤖 Agentic Query Assistant

A sophisticated multi-agent AI system that processes files and answers queries using specialized AI agents, MCP (Model Context Protocol) servers, and browser automation capabilities.

## 🚀 Features

### Multi-Agent Architecture
- **PlannerAgent**: Creates execution plans and task decomposition
- **RetrieverAgent**: Searches and retrieves information from various sources
- **ThinkerAgent**: Performs analytical reasoning and problem-solving
- **QAAgent**: Answers questions using retrieved information
- **DistillerAgent**: Summarizes and extracts key information from documents
- **FormatterAgent**: Formats and structures output data
- **CoderAgent**: Generates and executes code solutions
- **ClarificationAgent**: Handles user interactions and clarifications
- **SchedulerAgent**: Manages task scheduling and prioritization

### Core Capabilities
- 📁 **File Processing**: Automatic profiling and analysis of various file formats
- 🔍 **Web Search**: Intelligent web search with content extraction
- 📄 **Document Analysis**: PDF, HTML, and text document processing
- 🌐 **Browser Automation**: Full browser control with Playwright integration
- 💻 **Code Execution**: Safe Python code execution with sandboxing
- 🧠 **NetworkX Graph Orchestration**: DAG-based task execution and dependency management
- 🔧 **MCP Server Integration**: Extensible tool system via Model Context Protocol

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        Main Entry Point                         │
│                         (main.py)                              │
└─────────────────────┬───────────────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────────────┐
│                   Agent Loop 4                                 │
│              (agentLoop/flow.py)                               │
│          NetworkX Graph Orchestration                         │
└─────────────────────┬───────────────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────────────┐
│                Execution Context Manager                       │
│            (agentLoop/contextManager.py)                      │
│        Graph State Management & Execution                     │
└─────────────────────┬───────────────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────────────┐
│                  Agent Runner                                  │
│               (agentLoop/agents.py)                           │
│           Individual Agent Execution                          │
└─────────────────────┬───────────────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────────────┐
│                 MCP Servers                                    │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐              │
│  │  Documents  │ │ Web Search  │ │   Browser   │              │
│  │   Server    │ │   Server    │ │   Server    │              │
│  └─────────────┘ └─────────────┘ └─────────────┘              │
└─────────────────────────────────────────────────────────────────┘
```

## 📦 Installation

### Prerequisites
- Python 3.11+
- Node.js (for browser automation)
- Git

### Setup

1. **Clone the repository**:
```bash
git clone https://github.com/saurabhnolakha/EGA_Assignment16.git
cd EGA_Assignment16
```

2. **Install dependencies**:
```bash
# Install Python dependencies
pip install -e .

# Install Playwright browsers
playwright install
```

3. **Environment setup**:
```bash
cp .env.example .env
# Edit .env with your API keys (Google AI, etc.)
```

4. **Configure MCP servers**:
```bash
# Edit config/mcp_server_config.yaml to adjust file paths
# Update the 'cwd' paths to match your local setup
```

## 🎮 Usage

### Basic Usage

1. **Start the application**:
```bash
python main.py
```

2. **File Input** (Optional):
```
📁 File Input (optional):
Enter file paths (one per line), or press Enter to skip:
Example: /path/to/file.csv
📄 File path: /path/to/your/document.pdf
📄 File path: 
```

3. **Query Input**:
```
🤔 Your Question:
What are the key insights from the uploaded document?
```

4. **Processing**:
The system will automatically:
- Create an execution plan
- Profile uploaded files
- Execute specialized agents
- Retrieve information from web/documents
- Generate comprehensive answers

### Advanced Features

#### Browser Automation
The system includes full browser automation capabilities:
- Web page navigation
- Form filling
- Content extraction
- PDF generation
- Screenshot capture

#### Code Execution
Safe Python code execution with:
- Sandboxed environment
- Variable injection
- Multi-variant execution
- Error handling

#### File Processing
Supports multiple file formats:
- PDF documents
- CSV/Excel files
- Text files
- Images
- Web pages

## 🔧 Configuration

### Agent Configuration
Edit `config/agent_config.yaml` to customize:
- Agent models (Gemini, GPT-4, etc.)
- MCP server assignments
- Prompt templates

### MCP Server Configuration
Edit `config/mcp_server_config.yaml` to:
- Add/remove MCP servers
- Configure server endpoints
- Set working directories

### Prompt Customization
Modify prompts in the `prompts/` directory:
- `planner_prompt.txt` - Task planning
- `retriever_prompt.txt` - Information retrieval
- `thinker_prompt.txt` - Analytical reasoning
- And more...

## 📁 Project Structure

```
├── agentLoop/          # Core agent orchestration
│   ├── agents.py       # Agent runner and execution
│   ├── contextManager.py  # Graph state management
│   ├── flow.py         # Main orchestration logic
│   └── visualizer.py   # Execution visualization
├── action/             # Code execution engine
│   ├── executor.py     # Python code execution
│   └── execute_step.py # Step execution logic
├── browserMCP/         # Browser automation
│   ├── browser/        # Browser management
│   ├── dom/            # DOM processing
│   └── mcp_tools.py    # Browser tools
├── config/             # Configuration files
│   ├── agent_config.yaml
│   └── mcp_server_config.yaml
├── mcp_servers/        # MCP server implementations
│   ├── mcp_server_2.py # Document processing
│   ├── mcp_server_3.py # Web search
│   └── multiMCP.py     # MCP orchestration
├── prompts/            # Agent prompts
├── utils/              # Utility functions
└── main.py            # Application entry point
```

## 🔌 MCP Servers

### Documents Server (`mcp_server_2.py`)
- PDF processing
- Web content extraction
- Document search and indexing
- Content summarization

### Web Search Server (`mcp_server_3.py`)
- Internet search capabilities
- Web page content extraction
- Real-time information retrieval
- Search result ranking

### Browser Server (Optional)
- Full browser automation
- Interactive web browsing
- Form submission
- Screenshot capture

## 🧪 Development

### Adding New Agents
1. Create prompt file in `prompts/`
2. Add agent configuration in `config/agent_config.yaml`
3. Agent runner will automatically detect and use it

### Adding New MCP Servers
1. Create new server script in `mcp_servers/`
2. Add configuration in `config/mcp_server_config.yaml`
3. Update agent configurations to use new tools

### Testing
```bash
# Run basic tests
python -m pytest tests/

# Test MCP servers
python tests/basic_test.py
```

## 🎯 Example Use Cases

### Document Analysis
```
Files: research_paper.pdf, data.csv
Query: "What are the key findings and how do they relate to the data?"
```

### Web Research
```
Query: "Find recent developments in AI and summarize the key trends"
```

### Code Generation
```
Query: "Create a Python script to analyze the CSV data and generate visualizations"
```

### Multi-step Analysis
```
Files: financial_report.pdf
Query: "Analyze the financial performance and create a summary presentation"
```

## 📊 Session Management

The system automatically saves:
- Execution graphs
- Agent outputs
- Cost tracking
- Performance metrics

Sessions are stored in `memory/session_summaries_index/`

## 🔍 Monitoring & Debugging

### Execution Visualization
Real-time DAG visualization shows:
- Task dependencies
- Execution status
- Performance metrics
- Error states

### Logging
Comprehensive logging includes:
- Agent execution details
- MCP server interactions
- Cost tracking
- Performance metrics

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add tests for new functionality
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [Browser Use](https://github.com/browser-use/browser-use) for browser automation components
- [Model Context Protocol](https://github.com/modelcontextprotocol) for extensible tool integration
- NetworkX for graph orchestration
- Rich for terminal UI components

## 🆘 Support

For issues and questions:
1. Check the [Issues](https://github.com/saurabhnolakha/EGA_Assignment16/issues) section
2. Review the configuration files
3. Check MCP server logs in terminal output
4. Ensure all dependencies are properly installed

## 🔮 Future Enhancements

- [ ] Multi-modal input support (images, audio)
- [ ] Custom agent development framework
- [ ] Advanced caching mechanisms
- [ ] Distributed execution support
- [ ] Web interface
- [ ] REST API endpoints
- [ ] Enhanced security features
- [ ] Performance optimization tools 