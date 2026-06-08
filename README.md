# Market Basket Analysis — Apriori & FP-Growth

Association rule mining on multi-retailer transaction data (Amazon, BestBuy, Nike, K-Mart, Supermarket) to surface high-confidence cross-sell and co-purchase patterns using Apriori and FP-Growth algorithms.

**Stack:** Python · mlxtend · scikit-learn · Pandas · Matplotlib · Jupyter

---

## Overview

This project applies frequent itemset mining and association rule learning to transactional data across five retail domains. The goal is to identify statistically significant item co-occurrence patterns that can inform product recommendation, shelf placement, and cross-sell strategy.

Two algorithms are implemented and compared:

- **Apriori** — breadth-first candidate generation; interpretable and well-suited for moderate dataset sizes
- - **FP-Growth** — compressed tree-based structure; significantly faster on large, sparse transaction sets
 
  - ---

  ## Datasets

  | Retailer | Description |
  |----------|-------------|
  | Amazon | E-commerce product transactions |
  | BestBuy | Consumer electronics purchases |
  | Nike | Apparel and footwear transactions |
  | K-Mart | General merchandise |
  | Supermarket | Grocery basket data |
  | LargeTransactionalData | High-volume dataset for scalability testing |

  All datasets contain transaction IDs and item name mappings, enabling both sparse matrix and list-based representations.

  ---

  ## Methodology

  1. **Preprocessing** — Transaction data loaded, deduplicated, and encoded into binary item matrices
  2. 2. **Frequent Itemset Mining** — Apriori and FP-Growth applied across varying `min_support` thresholds
     3. 3. **Rule Generation** — Association rules extracted with configurable `min_confidence` and `min_lift` filters
        4. 4. **Rule Analysis** — Rules ranked by lift to surface the strongest non-trivial co-occurrence signals
           5. 5. **Cross-Retailer Comparison** — Algorithm performance and rule quality compared across datasets
             
              6. ---
             
              7. ## Key Metrics
             
              8. | Metric | Definition |
              9. |--------|-----------|
              10. | Support | Fraction of transactions containing the itemset |
              11. | Confidence | P(consequent \| antecedent) |
              12. | Lift | Confidence / Expected confidence (lift > 1 = positive association) |
             
              13. ---
             
              14. ## Key Findings
             
              15. - FP-Growth achieved substantially lower runtime than Apriori on the large transactional dataset, with identical rule output — confirming its advantage for sparse, high-volume data.
                  - - Cross-sell rules with lift > 2.0 were consistently found across all five retailer datasets, indicating generalizable co-purchase patterns.
                    - - Support threshold sensitivity analysis revealed that lowering `min_support` below 0.02 significantly increased rule volume while introducing low-quality associations — highlighting the need for lift-based filtering.
                     
                      - ---

                      ## Repository Structure

                      ```
                      Market-Basket-Analysis-Apriori-FPGrowth/
                      ├── data/
                      │   └── raw/                         # Transaction CSVs and item name files (per retailer)
                      ├── notebooks/
                      │   └── RulesAssociation.ipynb       # Full analysis with visualizations
                      ├── src/
                      │   └── RulesAssociation.py          # Standalone Python script
                      ├── reports/
                      │   └── RulesAssociation.html        # Full experiment report
                      └── README.md
                      ```

                      ---

                      ## Technologies

                      | Library | Purpose |
                      |---------|---------|
                      | mlxtend | Apriori, FP-Growth, and association rule generation |
                      | Pandas | Data loading, preprocessing, and rule filtering |
                      | scikit-learn | Data encoding utilities |
                      | Matplotlib | Support/confidence/lift visualization |
                      | Jupyter | Interactive analysis and reporting |

                      ---

                      ## Setup

                      ```bash
                      git clone https://github.com/psalarc/Market-Basket-Analysis-Apriori-FPGrowth.git
                      cd Market-Basket-Analysis-Apriori-FPGrowth
                      pip install pandas mlxtend scikit-learn matplotlib jupyter
                      jupyter notebook notebooks/RulesAssociation.ipynb
                      ```
