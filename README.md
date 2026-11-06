# Repolex Knowledge Graph of sphinx-contrib/yasfb

RDF knowledge graph data for [sphinx-contrib/yasfb](https://github.com/sphinx-contrib/yasfb), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/yasfb
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 328b4c55b2756f371e4d96d05dd984d8ebc286ff
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 328b4c55b2756f371e4d96d05dd984d8ebc286ff
│           └── chunk-001.nq.gz
├── blob
│   ├── 32a122cd8aa60c3191f10efc6ee9ed1722290e04.nq.gz
│   ├── 465041c0e10cbea500905826b9766b3591a8008f.nq.gz
│   ├── 69d3017e8c60f5918c9d827e19f7f4bd0dcaa41c.nq.gz
│   ├── a54e4c8844ba2eecedb4628a32e2abb090330f7c.nq.gz
│   ├── aa2d8a019471397f0a10d3e4700dcf4f8e141a71.nq.gz
│   ├── bb44e2efb5c775b2ce2fb4d5c1e6a9d061de3933.nq.gz
│   ├── d1ee9235c75d70cd0edc63e2f9e625b0b1e1d7b0.nq.gz
│   └── ed4c844d6a65b668aa26c8781d02d97d7a9b2ae1.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 328b4c55b2756f371e4d96d05dd984d8ebc286ff.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 16 files
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

[sphinx-contrib/yasfb](https://github.com/sphinx-contrib/yasfb)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
