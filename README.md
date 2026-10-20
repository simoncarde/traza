# TRAZA

> An evidence-driven data science platform for analyzing job-market skills, portfolio gaps, and career pathways.

TRAZA is a personal data science project that studies the relationship between labor-market demand, technical skills, portfolio evidence, and potential career pathways.

The project starts with reproducible data analysis and is designed to evolve toward a skill graph, evidence engine, recommendation system, and eventually AI-assisted retrieval.

## Project status

**Phase:** Architecture / foundation

Current focus:
- data ingestion
- data quality
- transformation with Polars
- analytical storage with Parquet and DuckDB
- reproducible exploratory analysis

## Architecture

```text
Data Sources
     |
     v
Ingestion
     |
     v
Cleaning & Normalization
     |
     v
Analytics
  |       |
  v       v
Skill   Statistics
Graph
  |
  v
Evidence Engine
  |
  v
Recommendation Engine
  |
  v
AI / RAG layer
  |
  v
Application
```

The AI layer is intentionally downstream of the data foundation. TRAZA should be able to produce useful analytical results before introducing LLMs or embeddings.

## Repository structure

```text
traza/
├── app/                  # User-facing application
├── data/
│   ├── raw/              # Original source data; never modify in place
│   ├── interim/          # Intermediate transformations
│   └── processed/        # Analysis-ready datasets
├── docs/
│   ├── decisions/        # Architecture and technical decisions
│   ├── architecture.md
│   ├── data-sources.md
│   └── methodology.md
├── notebooks/            # Exploration and research notebooks
├── src/traza/
│   ├── analytics/        # Statistical and analytical operations
│   ├── cleaning/         # Data cleaning and validation
│   ├── config/           # Application configuration
│   ├── evidence/         # Portfolio evidence analysis
│   ├── graph/            # Skill/role/project relationships
│   ├── ingestion/        # Source loading
│   ├── recommendations/  # Recommendation logic
│   └── skills/           # Skill extraction and normalization
├── tests/
└── pyproject.toml
```

## Development

Create and activate a virtual environment, then install the project with development dependencies:

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -e ".[dev]"
```

Run tests:

```bash
pytest
```

Run linting:

```bash
ruff check .
```

Format code:

```bash
ruff format .
```

## Data principles

TRAZA separates raw, intermediate, and processed data.

- `data/raw/`: source files are preserved as received.
- `data/interim/`: temporary or partially transformed data.
- `data/processed/`: validated datasets used for analysis.

Source provenance, licensing, collection date, and known limitations will be documented before a dataset becomes part of the analytical pipeline.

## License

TRAZA is released under the MIT License.
