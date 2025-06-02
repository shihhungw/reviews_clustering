# Negative Review Analysis of Google Play Apps Using K-Means Clustering

This project analyzes user complaints from low-star (1–2) Google Play app reviews across six categories (Games, Government, Communication, Delivery, Payment, Shopping). We built an NLP pipeline to tokenize, clean, and cluster user reviews using K-Means, extracting critical improvement suggestions for app developers.

## 🔍 Motivation

With thousands of reviews per app, manually identifying major user concerns is infeasible. Our system automates this process, providing developers with structured insights into the most common sources of user dissatisfaction. Though designed for app reviews, this framework is generalizable to consumer feedback analysis in fintech, customer service, and product development.

## 🧠 Model & Pipeline

We developed an unsupervised NLP pipeline that includes:

- **Scraper**: [`google-play-scraper`](https://github.com/JoMingyu/google-play-scraper) to collect reviews from selected apps
- **Review Filtering**: Only 1- and 2-star reviews were retained
- **Preprocessing**:
  - Remove non-traditional Chinese text (e.g., numbers, emojis, English)
  - Tokenize into 2–6 grams
  - Eliminate low-frequency and redundant n-grams
- **Clustering**:
  - Vectorization using term frequency
  - K-Means clustering (optimal k selected using the "knee" method)
  - Cluster labeling via top log-likelihood ratio terms

## 📈 Results

Our system successfully extracted meaningful clusters from each app's negative reviews. Common issues across app categories include:

- **Games**: installation errors, crashes, login failures
- **Government Apps**: device verification and notification bugs
- **Communication Apps**: updates, login/logout issues
- **Delivery Apps**: order cancellations, courier behavior
- **Payment Apps**: card binding, verification problems
- **Shopping Apps**: return logistics, search/filter flaws

## 🧩 Dataset

Due to platform restrictions, we do **not** release the raw scraped data. However, the dataset was built by scraping reviews from high-download apps in each category (>10k installs), with about 2–5 apps selected per category. Each review includes:

- Review ID, user name, score, text content
- Upvotes, app version, review/reply timestamp, and developer response (if available)

You may replicate this process using the same open-source scraper or by substituting with publicly available reviews.

## 🧠 Reflection

This project taught me how unsupervised learning and n-gram tokenization can surface interpretable insights from unstructured text. In broader AI-finance applications, similar techniques can be applied to analyze customer complaints, investor sentiment, or regulatory texts at scale.

## 📌 Requirements

- Python 3.7+
- `google-play-scraper`
- `scikit-learn`
- `jieba` (or other Chinese tokenizer)
- `pandas`, `numpy`, `matplotlib`
