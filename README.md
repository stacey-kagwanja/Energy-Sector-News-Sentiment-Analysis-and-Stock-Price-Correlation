# Energy Sector News Sentiment Analysis & Stock Price Correlation

> 🏆 **Top 3 of 15 projects · 95% grade** — Machine Learning for Quantitative Investing Academy, Warwick Quant Society & Warwick Business School Society

This project investigates how news sentiment in the energy sector correlates with stock price movements, combining classical NLP techniques with a custom deep learning model.

---

## Overview

Energy markets are highly sensitive to macroeconomic events and news cycles. This project explores whether headline sentiment can serve as a meaningful signal for energy sector returns, using both a pre-trained financial NLP model and a custom-built LSTM classifier trained from scratch.

The analysis was conducted over a 59-day window using curated energy headlines and price data from the WENE ETF as a sector-wide proxy.

---

## Project Components

### 1. Sentiment & Stock Price Analysis
- Loaded a curated dataset of energy sector news headlines
- Retrieved energy sector returns using the **WENE ETF**
- Applied **FinBERT** (a pre-trained financial sentiment model) to classify each headline as *positive*, *negative*, or *neutral*
- Computed correlation between daily sentiment scores and same-day returns
- **Finding:** Only weak same-day correlation was observed, suggesting that lagged effects are more significant than immediate reactions

<img src="Sentiment%20vs%20Price%20Movement%20Correlation0.png" width="600"/>

### 2. Custom LSTM Sentiment Classifier
- Built and trained an **LSTM model** using frozen **GloVe word embeddings**
- Used FinBERT-generated labels as training targets (silver labelling)
- Achieved **60% accuracy** on a 3-class sentiment classification task
- Validated that sentiment is a learnable signal even with limited training data, while confirming that transfer learning (FinBERT) outperforms custom models at this data scale

<img src="Confusion%20Matrix%20Test%20Set0.png" width="600"/>

---

## Key Findings

- Same-day sentiment–return correlation is weak; lagged effects likely dominate
- Transfer learning (FinBERT) significantly outperforms a custom model trained on limited data
- Sentiment classification is feasible even with small datasets, but generalisation requires more data
- ETF-level analysis provides a cleaner signal than aggregating individual stocks

---

## Limitations

- Limited training data constrained LSTM performance
- Short project timeline prevented exploration of lag structures and confounding variables
- Scope was narrowed from individual stocks to ETF-level analysis due to API constraints

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Sentiment model | FinBERT (ProsusAI) |
| Custom model | LSTM with GloVe embeddings |
| Price data | WENE ETF |
| Language | Python |

---

## Installation

Clone the repository and install the required dependencies:
```bash
git clone https://github.com/stacey-kagwanja/Energy-Sector-News-Sentiment-Analysis-and-Stock-Price-Correlation.git
cd Energy-Sector-News-Sentiment-Analysis-and-Stock-Price-Correlation
pip install -r requirements.txt
```

---

## Usage

Download the Jupyter notebook (`Energy_News_Sentiment.ipynb`) and the `data` folder into the same directory, then open and run the notebook:
```
Energy_News_Sentiment.ipynb
```

This covers the full pipeline: loading headlines, running FinBERT sentiment classification, computing sentiment–return correlation, and training/evaluating the custom LSTM model.

---

## Project Context

Built as the final project for the **Machine Learning for Quantitative Investing Academy**, run by [Warwick Quant Society](https://www.linkedin.com/company/warwick-quant/) & [Warwick Business School Society](https://www.linkedin.com/company/warwick-business-school-society/).

The project brief was open-ended; our team proposed this topic inspired by real-time movements in energy markets driven by macroeconomic events. Due to API limitations mid-project, we pivoted from individual stock analysis to ETF-level returns and curated headline datasets — a constraint that shaped (and ultimately improved) our methodology.

---

## Authors

- Geovana Maziero Camarotto
- Sindhiya Subedi
- David Zhang
- Stacey Kagwanja
- Carmen Gavilanes Talayero

---

## Acknowledgements

- [FinBERT by ProsusAI](https://huggingface.co/ProsusAI/finbert)
- [GloVe word embeddings (Stanford NLP)](https://nlp.stanford.edu/projects/glove/)
- Warwick Quant Society and Warwick Business School Society — Machine Learning for Quantitative Investing Academy
