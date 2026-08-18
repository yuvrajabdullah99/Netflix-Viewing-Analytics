# 🔴 Watch Next: A Netflix Viewing Analytics Suite

Two data-driven tools built from real subscriber viewing behavior: a personalized "watch next" recommender, and a title correlation matrix that visualizes which shows get watched together. Both are powered by the same underlying analysis of per-subscriber viewing time.

---

## 📌 Overview

Rather than recommending by genre tags alone, this project measures actual co-viewing behavior: how much time subscribers who watch one show also spend watching another. That signal is turned into a Pearson correlation matrix, which powers two complementary tools:

1. **Watch Next** — an interactive recommender: check off what you've watched, get ranked suggestions with plain-language reasons
2. **Title Correlation Matrix** — a heatmap view of the full correlation matrix, built for a content-strategy audience to see which titles share an audience at a glance

The project also includes the Excel workbook that takes raw viewing logs through cleaning, aggregation, and correlation analysis to produce the data both tools run on.

## 🗂️ Dataset

`Netflix_App_Workbook.xlsx` tracks viewing activity for **2,000 subscribers** across **9 shows**, with 18,000 raw records including:

| Field | Description |
|---|---|
| Subscriber ID | Unique viewer identifier |
| Show Name | Title watched |
| Episodes Watched | Number of episodes viewed (fractional, reflecting partial viewing) |
| Episode Length (m) | Average episode runtime in minutes |

**Shows covered:** Big Bang Theory, Queen Of Tears, It's Okay To Not Be Okay, You, Dexter, Dahmer, Stranger Things, Dark, Umbrella Academy.

## 🛠️ How It Was Built

1. **Raw data** — per-subscriber, per-show viewing logs (`Raw data` sheet)
2. **Calculated column** — Episodes Watched × Episode Length converted into Total Minutes Watched per subscriber, per show
3. **Pivot table** — minutes reshaped into a subscriber × show matrix
4. **Descriptive analysis** — average minutes watched calculated per show across all subscribers
5. **Final data** — the clean, pivoted subscriber × show matrix used for correlation analysis
6. **Correlation matrix** — Pearson correlation of total minutes watched computed between every pair of shows, revealing which titles are watched together
7. **App build** — the correlation matrix, genre tags, and average viewing stats embedded directly into two self-contained HTML pages (no server, no external calls)

## 🖥️ Deliverables

### 1. Watch Next (`Netflix_Recommendation_App.html`)
- Check off titles you've already watched from the list on the left
- The app averages each unwatched title's Pearson correlation against every title you've checked, scales that from **−1…+1** onto a **0–100 match score**, and ranks recommendations accordingly
- Each recommendation shows its match score, genre tags, and a plain-language reason (e.g. *"Because you watched Dark (94% correlated viewing time)"*)
- One click marks a recommended title as watched and instantly re-ranks the list

### 2. Title Correlation Matrix (`Netflix_Correlation_Matrix.html`)
- Renders the full 9×9 correlation matrix as an interactive heatmap, titles on both axes
- Titles are ordered by genre group (sitcom, K-drama romance, crime & thriller, supernatural) rather than alphabetically, so titles that share an audience sit together on the diagonal
- A diverging color scale (cool blue → dark neutral → Netflix red) runs from −1 (unrelated audiences) to +1 (watched together), with the exact correlation value printed in each cell
- Includes a plain-language explanation of the method and a genre key
- Fully accessible — an equivalent data table is available for screen readers

Both apps are single, self-contained HTML files — no server, build step, or external dependencies required. Just open them in a browser.

## 📁 Repository Structure

```
Netflix-Viewing-Analytics/
├── Netflix_App_Workbook.xlsx        # Raw data through correlation analysis
├── Netflix_Recommendation_App.html  # Interactive "watch next" recommender
├── Netflix_Correlation_Matrix.html  # Title correlation heatmap
└── README.md
```

## 🚀 Usage

1. Download the two `.html` files
2. Open either one directly in any modern browser (Chrome, Edge, Firefox, Safari) — double-click, or drag into a browser window
3. In **Watch Next**, check off the titles you've watched, then review your ranked recommendations — click **Mark watched** on any suggestion to add it to your list and refresh the results; use **Clear all** to reset
4. In the **Correlation Matrix**, hover any cell to see the exact correlation value and title pairing, or reference it alongside Watch Next to understand *why* the recommender suggests what it does

## 🧰 Skills Highlighted

- Excel: data cleaning, calculated fields, pivot tables, descriptive statistics
- Correlation analysis (Pearson)
- Front-end development: vanilla JS, responsive/accessible HTML & CSS, SVG data visualization
- Recommendation system design
- Data visualization and UX for data-driven tools

## 👤 Author

**Abdullah Al Yubraj**
📧 yuvrajabdullah99@gmail.com
