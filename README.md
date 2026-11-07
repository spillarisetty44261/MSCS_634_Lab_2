# MSCS 634 – Lab 2: KNN and RNN Classification

## Purpose

The purpose of this lab was to use the Wine Dataset from sklearn to compare two classifiers: K-Nearest Neighbors (KNN)
and Radius Neighbors (RNN). I tested different k values for KNN and different radius values for RNN to see how they
affect accuracy.

## Files

- `MSCS_634_Lab_2.ipynb` – Jupyter Notebook with the code, results, and plots
- `README.md` – summary of the lab

## Results

| k (KNN) | Accuracy |
|---|---|
| 1 | 77.8% |
| 5 | 80.6% |
| 11 | 80.6% |
| 15 | 80.6% |
| 21 | 80.6% |

| Radius (RNN) | Accuracy |
|---|---|
| 350 | 72.2% |
| 400 | 69.4% |
| 450 | 69.4% |
| 500 | 69.4% |
| 550 | 66.7% |
| 600 | 66.7% |

## Key Insights

- KNN did better than RNN for every value tested. The best KNN accuracy was 80.6% (k = 5) and the best RNN accuracy
  was 72.2% (r = 350).
- For KNN, k = 1 had the lowest accuracy. Accuracy improved at k = 5 and stayed the same after that.
- For RNN, accuracy went down as the radius got bigger. Even the smallest radius included more than half of the
  training data, so predictions leaned toward the most common class.
- The `proline` feature has a much larger range than the other features, so it has the biggest effect on distance.
  When I scaled the features as an extra test, both models improved a lot (up to 97–100%).

## Challenges and Decisions

- The radius values given in the lab (350–600) only work with the original, unscaled data, so I used unscaled data for
  the main part of the lab and tried scaling separately.
- RNN gives an error if a test point has no neighbors inside the radius, so I used `outlier_label="most_frequent"`
  to handle that.
- The classes are slightly uneven, so I used a stratified 80/20 split.
- The test set only has 36 samples, so one wrong prediction changes accuracy by about 2.8%.
