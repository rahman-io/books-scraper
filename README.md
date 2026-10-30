# books-scraper

Scrapes all 1000 books from [books.toscrape.com](https://books.toscrape.com) (a sandbox site made for practicing web scraping) and saves them to Excel and CSV.

It goes through every category and follows the "next" links, so books on later pages are included too.

## Extracted data

For each book:

- title
- category
- price (GBP)
- availability
- rating (1-5)
- product url
- image url

Sample:

| title | category | price | availability | rating |
|---|---|---|---|---|
| Sharp Objects | Mystery | 47.82 | In stock | 4 |
| In a Dark, Dark Wood | Mystery | 19.63 | In stock | 1 |
| It's Only the Himalayas | Travel | 45.17 | In stock | 2 |

The Excel file has a second sheet with a summary per category (number of books, average/min/max price and average rating).

## Setup

```
pip install -r requirements.txt
```

## Usage

```
python scraper.py
```

On a Mac use `python3` instead of `python`.

It takes about a minute and saves `books.xlsx` and `books.csv` to the `output` folder.

Some options:

```
python scraper.py --category Travel   # only one category
python scraper.py --delay 1           # wait 1 second between requests (default 0.5)
python scraper.py --out data          # save somewhere else
```

## Tests

```
pip install pytest
python -m pytest
```

The tests use a small local copy of the site's html, so they don't send requests to the real website.

Built with requests, BeautifulSoup and openpyxl.
