# Café-restaurant sales analysis

A business analysis of 13 months of point-of-sale data from an independent café-restaurant in
the Netherlands, delivered as a single self-contained, bilingual (EN/NL), interactive HTML report.

**[▶ Open the live report](https://sahandhaghighi.github.io/cafe-restaurant-analysis/)**

> The business is de-identified: no name, no city, no exact opening date, and the handful of
> dishes that would identify it are relabelled. All euro amounts, item counts and totals are
> replaced by shares, growth rates and index numbers, and the figures inside the file itself are
> scaled by a constant, so absolute revenue cannot be read back from the source. Menu prices are
> public information and are shown as they are.

![The report's opening page](screenshot-hero.png)

---

## The question

The owner had thirteen months of till exports and no reporting on top of them. What does the
data say about what sells, what the price round in March 2026 actually earned, which items are
not worth keeping, and how the cost base compares with the sector?

## The data

| Source | What it covers |
|---|---|
| 14 monthly DISH POS sales exports | 17 July 2025 – 31 August 2026, ~250 till buttons |
| Article and turnover-group exports | product master data, till grouping |
| The restaurant's own hours sheet | April – August 2026, per employee per day |
| The restaurant's public menu | 137 menu lines in 10 sections |

Two things had to be fixed before any analysis: the monthly exports were pulled with an end
time of 06:00 on the last day of each month, so the last day of every month is missing (~3.5%
of sales, quantified against the till's full-period total); and the ~250 till buttons had to be
mapped onto the 137 menu lines by hand, merging duplicates such as a pancake and its topping,
or Coca-Cola and Coca-Cola Zero.

## Scope and limits

This is a **first-pass report built on monthly, item-level sales data** — that is all the till
exports contain. It is worth being explicit about what that does and does not allow.

**What the data supports well**
month-by-month revenue and volume, seasonality, menu concentration, per-item and per-section
performance, price changes inferred from the data, and a like-for-like measurement of what the
price round earned.

**What is missing, and what it costs**

| Missing | What cannot be answered |
|---|---|
| Receipt-level data | average spend per guest, basket composition, guest counts |
| Sales per hour or per day | staffing against demand, opening-hour decisions |
| Purchase prices / food cost | margin per dish, the real profit ranking, the value of dropping an item |
| Staff hours before April 2026 | the winter wage ratio, a full-year labour picture |
| Management hours | the true labour cost; the figure shown is a floor, not the real number |
| Cost lines other than rent and staff | a complete profit and loss |

The report is built to say so. Where a figure is an assumption rather than a measurement it is
marked as one, unknown cost lines are left blank instead of estimated, and each finding carries
its own confidence level. The last page of the report lists the exports that would answer the
open questions.

## What the report covers

1. **Overview** — revenue, items and seasonality across 13 months, with period filters.
2. **The menu** — Pareto concentration, section-by-section and item-by-item performance, and a
   drill-down for every one of the 137 menu lines.
3. **Pricing** — price rounds detected from the data itself, the revenue the March 2026 round
   actually produced, a volume check on whether guests bought less, and a what-if calculator
   for the items whose price never moved.
4. **Findings** — six ranked findings, each with its evidence, a recommended action and a
   stated confidence level.
5. **Staff hours** — wage cost as a share of net revenue, revenue and staff cost per opening
   hour, and the shape of the working week.
6. **Cost structure** — the two cost lines that are actually known, set against published
   sector benchmarks.

![Menu concentration](screenshot-pareto.png)

## Selected findings

- **Drink prices never moved.** The items whose price has not changed since opening are close
  to half of everything sold. The March 2026 round raised 100 other items and left these alone.
- **The price round worked.** Menu revenue for April–August 2026 ran **+7.8%** above the same
  items sold at February 2026 prices. Comparing August with August — the only month open in
  both years — the items that went up grew *faster* (+46.8%) than the items that did not
  (+35.5%), so there is no sign that guests stopped buying them.
- **A small group of dishes earns above its weight.** Four dishes bring in a share of revenue
  well above their share of items sold.
- **Concentration is extreme.** 14.6% of the menu produces half of menu revenue; 86 items share
  the last 19.8%. Twelve food items sell fewer than three a month.
- **Staff cost is the binding constraint.** Wages, all employer charges included, run far above
  the sector norm; after staff and rent, only a third of net revenue is left for purchasing,
  energy, marketing and overhead combined.

![Findings](screenshot-findings.png)

## Method notes

- Every number in the report is computed from the raw exports; nothing is typed in by hand.
- Price rounds are inferred, not given: the average amount per item sold, per till button per
  month, reveals the month a price changed.
- The price effect is a like-for-like comparison — the same items at their February 2026 price
  — so new items and menu changes do not inflate it.
- Cost benchmarks are cited per line (Sligro *kengetallen 2025*, Rabobank September 2025, CBS
  sector figures published by Firmfocus).

![Cost structure](screenshot-costs.png)

## The report itself

One HTML file, no build step, no dependencies, no tracking. Every section is exactly one screen
tall and scroll-snaps to the next. It works on a phone, follows the system light/dark setting,
and switches between English and Dutch. Charts are hand-written inline SVG.

## Repository

```
index.html                 the report (open it in any browser)
screenshot-*.png           stills used in this README
```

The underlying till exports are the business's own data and are not published here.

## Tools

Python (pandas, openpyxl) for the analysis, hand-written HTML/CSS/JS for the report, Playwright
for automated layout and regression checks across two screen sizes and both languages.

---

*Built by [Sahand Haghighi](https://www.linkedin.com/in/YOUR-HANDLE/) — business analyst,
8 years in retail and e-commerce.*
