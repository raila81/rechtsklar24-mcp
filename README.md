# Rechtsklar24 MCP server

Answers compliance questions for German online shops with the legal source for every value: when obligations apply (for example the withdrawal button under Section 356a BGB), the fine ceilings of laws such as the BFSG, the unit price (Grundpreis) under the PAngV, and facts from published studies. Answers are in German. Information, not legal advice.

- **Website:** [rechtsklar24.de](https://rechtsklar24.de)
- **Documentation:** [rechtsklar24.de/ki-assistenten.html](https://rechtsklar24.de/ki-assistenten.html)
- **Endpoint:** `https://rechtsklar24.de/mcp` (MCP Streamable HTTP, public, no authentication, no API key)

## Tools

- `get_obligation_dates`: dates from which shop obligations apply
- `get_fine_ceilings`: maximum fines per law
- `calculate_grundpreis`: unit price under the PAngV
- `get_study_facts`: figures from published studies with source

All tools are read-only and stateless. The server stores nothing it receives.

## Connect

Any MCP client that supports remote servers:

```json
{
  "mcpServers": {
    "rechtsklar24": {
      "type": "streamable-http",
      "url": "https://rechtsklar24.de/mcp?src=mcp"
    }
  }
}
```

Quick test:

```bash
curl -s -X POST 'https://rechtsklar24.de/mcp?src=mcp' -H 'Content-Type: application/json' -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

This repository holds the listing metadata only. The server itself is a hosted service run by the Rechtsklar24 website (https://rechtsklar24.de); see the documentation link above for privacy and terms.
