# Repolex Knowledge Graph of python/mypy_extensions

RDF knowledge graph data for [python/mypy_extensions](https://github.com/python/mypy_extensions), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download python/mypy_extensions
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── df7b7054e3e978cc62717871f16659e51ea8171d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── df7b7054e3e978cc62717871f16659e51ea8171d
│           └── chunk-001.nq.gz
├── blob
│   ├── 068d160f87468bcc0be6a5e74698ad78e03ec599.nq.gz
│   ├── 4b280a9b34ea4323eed15efd8e9df618bd63defb.nq.gz
│   ├── 6c403427e33a75379886fdb127e53f73399f7ac4.nq.gz
│   ├── 800236038d512be623dbc60e28a9d6dadd24ed6c.nq.gz
│   ├── 8303af22e679a537965e1f322fa0378dfcdc489d.nq.gz
│   ├── 8a56f3bdae96e84418a3da19f7760e4f7c53e73f.nq.gz
│   ├── a6135e8c9b7542498e5fabd8490ab4f3c4bda859.nq.gz
│   ├── ae7ce94c1d297806d4022abeda235e33e74a789b.nq.gz
│   └── bdb7786b2322c9d2ab970bbfba8771d6e8774723.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── df7b7054e3e978cc62717871f16659e51ea8171d.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[python/mypy_extensions](https://github.com/python/mypy_extensions)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
