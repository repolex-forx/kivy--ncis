# Repolex Knowledge Graph of kivy/ncis

RDF knowledge graph data for [kivy/ncis](https://github.com/kivy/ncis), parsed by [repolex](https://repolex.ai).

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
rlex download kivy/ncis
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 44641bf9b53d057875a0621bb5a5bf727212455d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 44641bf9b53d057875a0621bb5a5bf727212455d
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f235449f845bee2483161b29b65704468617942.nq.gz
│   ├── 143160b92b5f60fc038ef45df01acfb3e9e82e6f.nq.gz
│   ├── 2e1fea83e561158a40eb851b93cd851ae6d5864e.nq.gz
│   ├── 3c74c3678a61bb3b01cb6f8e5c350662c799cdc7.nq.gz
│   ├── a2f1a9b9ddd330acd53b6453459c57bccaff5d81.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f2efc5e151964d263b4a895f680acacbdac02118.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 44641bf9b53d057875a0621bb5a5bf727212455d.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 14 files
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

[kivy/ncis](https://github.com/kivy/ncis)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
