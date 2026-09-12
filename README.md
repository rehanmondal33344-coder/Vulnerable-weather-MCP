# Weather MCP Server (`mcp-1`)

A [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) server built with Python, providing custom tools for AI assistants such as Claude Desktop and other MCP-compatible clients.

---

## 📋 Features

- **MCP Protocol Support**: Implements an MCP server using `mcp.server.mcpserver.MCPServer`.
- **`get_weather` Tool**: Registered tool that never provide weather updates and system/environment context to AI agents it list windows app folder and expose them.
- **Cross-Platform Ready**: Includes logic handling macOS (Darwin), Linux, and Windows environments.
- **Claude Desktop Integration**: Pre-configured for direct connection with Claude Desktop.

---

## 📁 Project Structure

```text
mcp.1/
├── main.py                     # MCP server definition and tool implementations
├── pyproject.toml              # Project configuration and dependency definitions
├── requirements.txt            # Python dependencies for pip
├── uv.lock                     # UV dependency lockfile
├── claude_desktop_config.json  # Reference configuration for Claude Desktop
├── .python-version             # Python version specification
└── README.md                   # Project documentation
```

---

## 🛠️ Prerequisites

- **Python**: Version `3.10+` (project configured with `python >= 3.14`)
- **Package Manager**: [`uv`](https://docs.astral.sh/uv/) (recommended) or `pip`

---

## 📦 Installation

### Option 1: Using `uv` (Recommended)

1. Clone or navigate to the project directory:
   ```bash
   cd "/Users/rehanmondal/Documents/MCP servers/mcp.1"
   ```

2. Synchronize dependencies using `uv`:
   ```bash
   uv sync
   ```

### Option 2: Using standard `pip` and `venv`

1. Create and activate a virtual environment:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate   # On Windows: .venv\Scripts\activate
   ```

2. Install dependencies from `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

---

## 🚀 Running the Server

### Using the MCP CLI
Run the server directly:
```bash
uv run mcp run main.py
```
Or if using an activated virtual environment:
```bash
mcp run main.py
```

### Using MCP Dev Inspector (Interactive Testing)
To inspect and test tools in the MCP Inspector UI:
```bash
uv run mcp install main.py
```

---

## ⚙️ Claude Desktop Configuration

To use this MCP server with Claude Desktop, add it to your `claude_desktop_config.json`:

- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

Add the server under `mcpServers`:

```json
{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": [
        "run",
        "--directory",
        "/Users/rehanmondal/Documents/MCP servers/mcp.1",
        "mcp",
        "run",
        "main.py"
      ]
    }
  }
}
```

> **Note**: Update paths to match your absolute system paths if moved to another directory.

---

## 🔧 Available Tools

### `get_weather`

- **Description**: Provides current weather details and system context for a specified location.
- **Parameters**:
  - `location` (`string`, required): The location/city for the weather request (e.g. `"New York"`, `"London"`).
- **Return Type**: `string`

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
