# Ellie for Claude

Plan and manage your Ellie tasks: review, search, create, update, complete, and organize tasks through your connected account.

This package connects Claude to the hosted Ellie MCP service using Streamable HTTP and OAuth. It contains a plugin manifest and connection configuration. It has no local executable, hooks, embedded credentials, or account data.

## Requirements

- A Ellie account with access to the product's connector features.
- A Claude client with plugin and remote MCP support.
- Internet access to `https://mcp.ellieplanner.com/mcp` and the service's OAuth authorization server.

## Setup

1. Install this plugin through the plugin directory when it is listed. For local testing in Claude Code, clone or download this repository and launch `claude --plugin-dir /absolute/path/to/this/repository`.
2. In Claude Code, open `/mcp`, select the ellie server, and choose its authentication action. In Cowork, use the connection setup offered by the plugin.
3. Sign in to Ellie in the browser and review the requested account access before authorizing the connection.
4. Return to Claude and request a read-only operation first.

Installing the package does not grant access to an account by itself. Each person signs into their own Ellie account. Product subscription and connector eligibility requirements continue to apply.

## Example requests

- Show my Ellie tasks for today.
- Find my incomplete Ellie tasks containing launch.
- Create an Ellie task called Draft launch brief for tomorrow with a 45-minute estimate.

## Capabilities

The hosted MCP server supplies the current tool descriptions, schemas, and permissions. Its product tools include:

- `get_task`
- `get_tasks_by_date`
- `get_tasks_by_list`
- `get_tasks_by_label`
- `get_braindump`
- `search_tasks`
- `create_task`
- `update_task`
- `complete_task`
- `delete_task`
- `get_labels`
- `create_label`
- `get_lists`

Write tools modify the connected product account. Review the requested action and target before allowing a write. Verify a new or changed item with a read-back request. Task deletion is permanent. Use a dedicated sample account for tests that change data.

## Privacy policy

Ellie handles task titles, notes, dates, estimates, completion state, lists, and labels for the connected account. Users can place personal information in task text. Requested tool inputs go to Ellie, and tool results are returned to the Claude client.

This package itself does not add analytics, local data storage, or a separate proxy. Data handling by the hosted service is covered by the [Ellie privacy policy](https://www.ellieplanner.com/legal/privacy); data handling by Claude is covered by [Anthropic's privacy policy](https://www.anthropic.com/legal/privacy).

Do not put passwords, OAuth tokens, API keys, or private journal/task data in repository files or GitHub issues. Authenticate in the product's browser flow. Disconnect the integration in the product or Claude's connection settings when access is no longer needed.

## Support and security reports

For account help or a suspected security vulnerability, [contact Ellie](https://www.ellieplanner.com/contact). Send vulnerability details privately through that support channel rather than posting user data or credentials in public issues.

## Validation

Run `claude plugin validate . --strict` from the package directory. Package validation checks the plugin structure; it does not establish that OAuth and every hosted tool have been tested end to end.

Operated by Saint Yeti LLC. [Ellie](https://www.ellieplanner.com)

## License

The connector configuration and documentation are licensed under MIT. Brand artwork and trademarks are reserved. See [LICENSE](LICENSE) and [NOTICE](NOTICE) for scope. The private applications and hosted services are not included in this license.
