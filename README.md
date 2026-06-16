# hypervisor-dashboard (system agent)

TellMesh control plane UI (:8788) — observer, renderer, and approval-gated URI controller.

| Layer | Location |
|-------|----------|
| Contract | [`hypervisor_dashboard.yaml`](hypervisor_dashboard.yaml) |
| Deployment entry | `agents.system.hypervisor_dashboard.main:app` |
| Implementation | `hypervisor_dashboard_agent/` (this directory) |

```text
hypervisor-dashboard -> /www chat UI, /api/uri/call, SSE events
urish                  -> uri ask, uri agent, uri dashboard create
hypervisor             -> run-agent, policy, deployments
```

## Install

```bash
pip install -e .
# from monorepo:
hypervisor run-agent hypervisor-dashboard.local --detach --wait-healthy
```

## Run

```bash
hypervisor run-agent hypervisor-dashboard.local --detach --wait-healthy
uvicorn agents.system.hypervisor_dashboard.main:app --host 0.0.0.0 --port 8788
```

## Endpoints

| Path | Role |
|------|------|
| `GET /www/` | static chat UI from repo `www/` |
| `GET /ui/agents` | agent list |
| `POST /api/ask` | `urish ask` NL planning |
| `POST /api/uri/call` | policy-gated URI execution |
| `GET /api/events` | observable events stream |

## Examples

| Example | Path |
|---------|------|
| Dashboard capabilities | [`tellmesh/examples/22_dashboard_agent`](../tellmesh/examples/22_dashboard_agent) |
| Golden path | [`tellmesh/examples/30_golden_path`](../tellmesh/examples/30_golden_path) |

## Links

- [TODO](TODO.md)
- [urish](../urish) · [hypervisor](../hypervisor)
- Org status: [`../TODO_STATUS.md`](../TODO_STATUS.md)


## License

Licensed under Apache-2.0.
