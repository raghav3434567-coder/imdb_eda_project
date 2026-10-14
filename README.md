# IMDB Movie Data Analysis

An exploratory data analysis (EDA) of the top 1,000 IMDB movies (2006-2016) using **Python, pandas, NumPy, Matplotlib and Seaborn**. The notebook ranks movies by rating, revenue, votes, Metascore and runtime, compares long and short films, tracks trends by year, and evaluates directors.

## Project Structure

```
.
├── IMDB_project.ipynb        # Analysis notebook
├── 7-IMDB-Movie-Data.csv     # Dataset (1,000 rows x 12 columns)
├── IMDB_Project_Report.pdf   # Detailed project report
└── README.md                 # This file
```

> The notebook reads the CSV from `./drive/MyDrive/7-IMDB-Movie-Data.csv` (Google Colab with Drive mounted). To run locally, place the CSV next to the notebook and change the path to `7-IMDB-Movie-Data.csv`.

## Dataset

| Column | Description |
|---|---|
| Rank | Position in the IMDB list (1-1000) |
| Title | Movie title |
| Genre | Up to three comma-separated genres |
| Description | Short plot summary |
| Director | Director name |
| Actors | Main cast |
| Year | Release year (2006-2016) |
| Runtime (Minutes) | Length of the film |
| Rating | IMDB user rating (1.9 to 9.0) |
| Votes | Number of user votes |
| Revenue (Millions) | Box-office revenue in USD millions |
| Metascore | Critic score (0-100) |

## What the Notebook Does

1. Loads the data and removes duplicate rows.
2. Cleans `Revenue (Millions)` and `Metascore`: converts to numeric, fills missing values with 0, casts to integer.
3. Computes summary statistics.
4. Builds top-10 lists by rating, revenue, Metascore, runtime and votes.
5. Compares the five longest movies against movies under 180 minutes (rating, votes, revenue, Metascore).
6. Plots votes, revenue, rating, Metascore and movie count by year with Seaborn bar plots.
7. Ranks directors by average rating (644 unique directors).
8. Computes the Rating-Revenue correlation (0.22) with a scatter plot.
9. Adds a `Category` column: Excellent (8+), Good (6-8), Average (4-6), Bad (under 4).

## Key Results

| Metric | Result |
|---|---|
| Rows / columns | 1,000 / 12 |
| Mean rating / runtime | 6.72 / 113 min |
| Highest rated | The Dark Knight (9.0) |
| Highest revenue | Star Wars: The Force Awakens (936M) |
| Most votes | The Dark Knight (1,791,916) |
| Highest Metascore | Boyhood (100) |
| Longest movie | Grindhouse (191 min) |
| Rating vs revenue correlation | 0.22 (weak) |
| Highest average rating by year | 2007 (7.13) |
| Most movies in a year | 2016 (297) |

## How to Run

```bash
pip install numpy pandas matplotlib seaborn jupyter
jupyter notebook IMDB_project.ipynb
```

Python 3.12+ is recommended, because the notebook nests same-type quotes inside f-strings.

## Known Limitations

- Missing revenue and Metascore values are filled with **0**, which drags down averages and affects rankings. Leaving them as `NaN` is more accurate.
- The "longer than 180 minutes" group is just the 5 longest movies (three of them exactly 180 min), so those comparisons rest on a tiny sample.
- Year bar plots show the **mean** per year, not totals, so statements like "most revenue in 2009" refer to average revenue per movie.
- Average rating per director includes directors with a single film and is not a measure of consistency.
- A cell that drops the column `average_rating` refers to a column that does not exist in the dataset.

See `IMDB_Project_Report.pdf` for details and recommended fixes.

## Tech Stack

Python, pandas, NumPy, Matplotlib, Seaborn, Jupyter / Google Colab
