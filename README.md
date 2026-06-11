# 🎬 Netflix Global Content Analysis

> An advanced exploratory data analysis of Netflix's catalog — uncovering content trends, global production patterns, genre evolution, and platform growth using Python and 12 visualizations.

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat-square&logo=pandas)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-3F4F75?style=flat-square&logo=plotly)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Questions Answered](#-questions-answered)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Setup & Installation](#-setup--installation)
- [How to Run](#-how-to-run)
- [Visualizations](#-visualizations)
- [Key Findings](#-key-findings)
- [Tech Stack](#-tech-stack)
- [License](#-license)

---

## 🎯 Project Overview

This project performs a deep-dive analysis of Netflix's global content catalog (~8,800 titles) to answer 18 analytical questions across 6 themes:

| Theme | Questions |
|-------|-----------|
| 📦 Content Composition | Type split, rating distribution, catalog makeup |
| 🎭 Genre Evolution | Genre trends, Movie vs TV genre bias, genre-rating mix |
| 🌍 Global Geography | Top producing countries, co-production patterns |
| 📈 Platform Growth | Yearly expansion, monthly patterns, release lag |
| ⏱ Duration & Format | Runtime distribution, genre runtimes, season lengths |
| 🎬 Talent | Prolific directors, multi-genre directors |

---

## ❓ Questions Answered

### Content Composition
1. How is the catalog split between Movies and TV Shows?
2. How has the Movies vs TV ratio shifted year over year?
3. What content ratings dominate — family vs adult content?

### Genre Evolution
4. Which genres grew fastest after 2016?
5. Are certain genres exclusive to Movies or TV Shows?
6. What is the genre mix per content rating?

### Global Geography
7. Which countries produce the most Netflix content?
8. Do countries specialize in Movies or TV Shows?
9. What is the volume of content per country visually on a map?

### Platform Growth
10. How did the catalog size grow year by year (2010–2021)?
11. Which months see the highest number of new additions?
12. What is the typical lag between a title's release year and when it lands on Netflix?

### Duration & Format
13. What is the typical runtime distribution for Netflix movies?
14. Do different genres have meaningfully different runtimes?
15. How many seasons do TV shows typically run?

### Talent
16. Who are the 20 most prolific directors on Netflix?
17. How do movie runtimes vary across the top genres?

---

## 📊 Dataset

**Source:** [Netflix Movies and TV Shows — Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows)  
**Author:** Shivam Bansal  
**Size:** ~8,800 rows × 12 columns  
**Coverage:** Titles available on Netflix up to mid-2021

### Columns

| Column | Type | Description | Issues |
|--------|------|-------------|--------|
| `show_id` | str | Unique title identifier | Clean |
| `type` | str | `Movie` or `TV Show` | Clean |
| `title` | str | Title name | Clean |
| `director` | str | Director name(s) | 2,634 nulls |
| `cast` | str | Comma-separated cast list | 825 nulls |
| `country` | str | Country/countries of production | 831 nulls, multi-value |
| `date_added` | str | Date added to Netflix | Needs parsing |
| `release_year` | int | Original release year | Clean |
| `rating` | str | Content rating (TV-MA, PG-13, etc.) | 4 nulls |
| `duration` | str | `90 min` or `3 Seasons` | Needs parsing |
| `listed_in` | str | Comma-separated genre tags | Multi-value |
| `description` | str | Synopsis | Clean (unused) |

> ⚠️ **Note:** The dataset is not included in this repository. Download it from Kaggle and place it in `data/` (see Setup below).

---

## 📁 Project Structure

```
netflix_project/
│
├── README.md                        ← Project documentation (this file)
├── .gitignore                       ← Files excluded from version control
├── requirements.txt                 ← Python dependencies
│
├── data/
│   └── netflix_titles.csv           ← ⚠️ Download from Kaggle (not in repo)
│
├── charts/                          ← Auto-generated when notebook runs
│   ├── 01_donut.png                 ← Movies vs TV split
│   ├── 02_area_growth.png           ← Catalog growth over time
│   ├── 03_stacked_genres.png        ← Genre trends year-over-year
│   ├── 04_heatmap_genre_type.png    ← Genre × type matrix
│   ├── 05_choropleth.html           ← [Interactive] Country map
│   ├── 06_lollipop_countries.png    ← Top 15 countries
│   ├── 07_histogram_runtime.png     ← Movie runtime distribution
│   ├── 08_boxplot_genre.png         ← Runtime by genre
│   ├── 09_calendar_heatmap.png      ← Monthly content additions
│   ├── 10_scatter_lag.html          ← [Interactive] Release lag scatter
│   ├── 11_bar_directors.png         ← Top 20 directors
│   └── 12_treemap_ratings.html      ← [Interactive] Rating treemap
│
└── notebooks/
    └── netflix_analysis.ipynb       ← Main analysis notebook (40 cells)
```

---

## ⚙️ Setup & Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager
- A [Kaggle account](https://www.kaggle.com) (free) to download the dataset

### 1. Clone the repository

```bash
git clone https://github.com/your-username/netflix_project.git
cd netflix_project
```

### 2. Create a virtual environment (recommended)

```bash
# Create
python -m venv venv

# Activate — Mac/Linux
source venv/bin/activate

# Activate — Windows
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the dataset

**Option A — Kaggle website:**
1. Go to https://www.kaggle.com/datasets/shivamb/netflix-shows
2. Click **Download**
3. Unzip and move `netflix_titles.csv` into `data/`

**Option B — Kaggle API:**
```bash
pip install kaggle
# Place your kaggle.json API key at ~/.kaggle/kaggle.json
kaggle datasets download -d shivamb/netflix-shows --unzip -p data/
```

---

## ▶️ How to Run

```bash
# Make sure you're in the project root and venv is active
cd netflix_project

# Launch Jupyter
jupyter notebook

# Then open: notebooks/netflix_analysis.ipynb
# Run all cells: Kernel → Restart & Run All
# Or cell-by-cell: Shift + Enter
```

All 12 charts will be saved automatically to the `charts/` folder.

---

## 📈 Visualizations

| # | Chart Type | Question answered | Output |
|---|-----------|-------------------|--------|
| 01 | Donut chart | Movies vs TV split | PNG |
| 02 | Stacked area | Catalog growth 2010–2021 | PNG |
| 03 | Stacked bar | Top 8 genres year-over-year | PNG |
| 04 | Heatmap | Genre × type bias matrix | PNG |
| 05 | Choropleth map | Content production by country | **HTML** |
| 06 | Lollipop chart | Top 15 producing countries | PNG |
| 07 | Histogram | Movie runtime distribution | PNG |
| 08 | Box plot | Runtime variance by genre | PNG |
| 09 | Calendar heatmap | Monthly addition patterns | PNG |
| 10 | Scatter plot | Release year vs year added | **HTML** |
| 11 | Horizontal bar | Top 20 prolific directors | PNG |
| 12 | Treemap | Rating distribution by type | **HTML** |

Interactive charts (`.html`) can be opened in any browser for hover, zoom, and drill-down functionality.

---

## 🔍 Key Findings

> Findings populate after you run the notebook. Expected results based on the dataset:

- **~70% Movies, ~30% TV Shows** — Movies dominate the catalog
- **Dramas and Documentaries** are the top two genres and have grown steadily since 2016
- **United States, India, and UK** are the top 3 content-producing countries
- **2019–2020** was Netflix's peak content addition period
- **Median movie runtime is ~98 minutes** — close to the classic 90-min format
- **TV-MA** is the most common rating — Netflix skews toward adult content
- Most content is added within **0–3 years** of its original release

---

## 🛠 Tech Stack

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | ≥ 1.5 | Data loading, cleaning, grouping |
| `numpy` | ≥ 1.23 | Numerical operations |
| `matplotlib` | ≥ 3.6 | Static chart rendering |
| `seaborn` | ≥ 0.12 | Statistical visualizations |
| `plotly` | ≥ 5.11 | Interactive HTML charts |
| `kaleido` | ≥ 0.2 | Saving Plotly charts as PNG |
| `jupyter` | ≥ 1.0 | Notebook environment |

---

## 📄 License

This project is licensed under the **MIT License** — feel free to use, modify, and share.

The dataset is sourced from Kaggle under its own terms. See [Kaggle's dataset page](https://www.kaggle.com/datasets/shivamb/netflix-shows) for usage rights.

---

## 🙋 Contributing

Pull requests are welcome. For major changes, open an issue first to discuss what you'd like to change.

---

*Built as part of a data analysis learning project.*
