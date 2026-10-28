# Repolex Knowledge Graph of explosion/spacy-stanza

RDF knowledge graph data for [explosion/spacy-stanza](https://github.com/explosion/spacy-stanza), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/spacy-stanza
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b57f3482582535f2f07afb0e4ed01df650925d9d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── b57f3482582535f2f07afb0e4ed01df650925d9d
│           └── chunk-001.nq.gz
├── blob
│   ├── 03abc8b51f267d7d4b06db04f96d67ba2f7c6655.nq.gz
│   ├── 335ff57966a2613a3125a07905ebb0ca1e44673f.nq.gz
│   ├── 37f77c60f9236be556499225f09cb67c00eb4795.nq.gz
│   ├── 5cb3fb9371e8866b9fb61be8ab5ad0cfbc307adc.nq.gz
│   ├── 6026308a209bdc8e17cb630e742626bdde0065a0.nq.gz
│   ├── 67441d5fd3eb35feb78b063e6685d6ddfe51ecae.nq.gz
│   ├── 6eebb3e7a4e83184818ee588fb345462cfe39c36.nq.gz
│   ├── 84150ed9ebf7fae814310db69a20ea2ed0406388.nq.gz
│   ├── 8b8dd31642e94954cf4412e35cf0de3a430047d7.nq.gz
│   └── b23c7b128d0a894b61bab2680c5dad16cc15aa89.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── b57f3482582535f2f07afb0e4ed01df650925d9d.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[explosion/spacy-stanza](https://github.com/explosion/spacy-stanza)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
