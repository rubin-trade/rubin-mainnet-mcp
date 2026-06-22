# Rubin MCP server (mainnet)

Trade crypto **perpetual futures and spot** on [Rubin](https://rubin.trade) — a self-custody decentralized exchange — directly from AI agents and assistants via the **Model Context Protocol (MCP)**.

Rubin runs a **hosted, remote MCP server** (streamable-HTTP). Connect any MCP client (Claude, Cursor, VS Code, etc.) and let agents place and manage orders and read live market and account data. You keep custody of your funds — trading is authorized by a scoped token you mint yourself.

- **Exchange / app:** https://rubin.trade
- **MCP & AI-trading docs:** https://code.rubin.trade/ai
- **Endpoint (mainnet):** `https://mcp.mainnet.rubin.trade/mcp` · transport `streamable-http`
- **Official MCP Registry:** [`trade.rubin/exchange`](https://registry.modelcontextprotocol.io/v0/servers?search=trade.rubin)

## Tools
- **Market data** — list markets, order book, candles, market stats, block height
- **Account** — balances, equity, positions, open orders, fills, PnL
- **Trading** — place / cancel limit & market orders, stop-loss, take-profit, cancel-all, batch-cancel

## Authentication
Send an `Authorization: Bearer <token>` header. Mint a free **MCP token** on the Rubin exchange:

> **https://rubin.trade → Trading Keys → MCP Token**

## Connect

**Claude Code / CLI**
```bash
claude mcp add --transport http rubin https://mcp.mainnet.rubin.trade/mcp \
  --header "Authorization: Bearer <YOUR_MCP_TOKEN>"
```

**Generic `mcp.json` (Claude Desktop / Cursor / others)**
```json
{
  "mcpServers": {
    "rubin": {
      "type": "streamable-http",
      "url": "https://mcp.mainnet.rubin.trade/mcp",
      "headers": { "Authorization": "Bearer <YOUR_MCP_TOKEN>" }
    }
  }
}
```

**VS Code (GitHub Copilot) — `.vscode/mcp.json`**
```json
{
  "servers": {
    "rubin": {
      "type": "http",
      "url": "https://mcp.mainnet.rubin.trade/mcp",
      "headers": { "Authorization": "Bearer <YOUR_MCP_TOKEN>" }
    }
  }
}
```

See [code.rubin.trade/ai](https://code.rubin.trade/ai) for ready-made snippets for every client.

## Manifest
[`server.json`](./server.json) — the MCP Registry manifest for this server.

## Links
- Exchange: https://rubin.trade
- Builder & MCP docs: https://code.rubin.trade
- Market data API (indexer): https://indexer.mainnet.rubin.trade

## License
[MIT](./LICENSE)
