# Repolex Knowledge Graph of block/picocert

RDF knowledge graph data for [block/picocert](https://github.com/block/picocert), parsed by [repolex](https://repolex.ai).

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
rlex download block/picocert
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 71817556db80ae174eb6ff58e6f666444e546249
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 71817556db80ae174eb6ff58e6f666444e546249.nq.gz
│   └── repolex
│       └── 71817556db80ae174eb6ff58e6f666444e546249
│           └── chunk-001.nq.gz
├── blob
│   ├── 0372385454d33b55377b28fc9b7ec747b33bfcf0.nq.gz
│   ├── 1f9ee8b9aebdf47c9ebbdca4ccc253c84e751e70.nq.gz
│   ├── 3109b78306d74fe48d53374ce71f2522e87e11fd.nq.gz
│   ├── 39f01e5157e961763bf3d416ce17cc8c8ccbaa4b.nq.gz
│   ├── 3b571f7fa30e4bcee5e4f525eddf13eae135ee31.nq.gz
│   ├── 432dc3d37a51b9f95ac2a13eee9e2e6537a53894.nq.gz
│   ├── 480ac49649fe45dedf3147858acebde487b01275.nq.gz
│   ├── 5a4947a55a6a138f070dcb23bcdcfbb7a6fec25d.nq.gz
│   ├── 6bccf43368fd7c96d9c659562a5142b8b8cb98a1.nq.gz
│   ├── 76018a1d88eb2027578dca037ef7ecd17d5b0942.nq.gz
│   ├── 76b73d0f05db2d19a6aece3f99bb5d3119281236.nq.gz
│   ├── 7cca444741fd409c88e65e0580c67496965f6d0a.nq.gz
│   ├── b3147efdf1537d895dfce8d41f70cdd351d8e8e2.nq.gz
│   ├── be2930a71dd7d968188dd1c8ac3f7c68ea85bb32.nq.gz
│   └── e9b6c2ecfab1fdca849bb57ce02bc82633028a10.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 71817556db80ae174eb6ff58e6f666444e546249.nq.gz
├── filetree
│   └── 71817556db80ae174eb6ff58e6f666444e546249.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

14 directories, 24 files
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

[block/picocert](https://github.com/block/picocert)

---
*Parsed on 2026-10-01 by [repolex](https://repolex.ai)*
