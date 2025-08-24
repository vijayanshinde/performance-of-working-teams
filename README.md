---
# Underachiever Detection / Performance-of-Working-Teams
Track, Analyse, and Predict the Productivity Performance of the Working teams in their factories 


---
# Productivity Predictor

A binary classifier predicting underperforming teams in garment manufacturing.

**Goal**: Identify teams likely to miss productivity targets (prioritizing recall to minimize false negatives).

---
## Key Features
- **Target**: Binary classification (`1` = actual productivity < target)
- **Focus**: Optimized for **recall** (minimizing missed underperformers)
- **Data**: 1197 observations, 14 features (department, overtime, incentive, etc.)
- **Critical Features**: 
  - Overtime (>25k min) 
  - Idle time (>250 min) 
  - Incentives (>2500 BDT)


---
## Methodology
1. **Preprocessing**:
   - Imputed missing `wip` with 0
   - Cleaned categorical data (e.g., trimmed `department` spaces)
   - Standardized numerical features
   
2. **Feature Selection**:
   - Forward stepwise selection
   - Removed multicollinear features (e.g., `smv`, `over_time`)

3. **Models Tested**:
   ```mermaid
   graph LR
   A[Linear Models] --> B[Logistic Regression]
   A --> C[Linear SVM]
   D[Non-Linear Models] --> E[Naive Bayes]
   D --> F[Random Forest]
   D --> G[Gradient Boosting]


4. **Evaluation**:
   - Nested cross-validation
   - Primary metric: **Recall** (detection rate of underperformers)

---
## Results
**Best Model**: Naive Bayes  
- **Recall**: 73.0% (detects 73% of underperformers)  
- **Key Features**: `wip`, `incentive`, `no_of_style_change`  

Performance gain from feature selection:  
| Model              | Recall Gain |
|--------------------|-------------|
| Naive Bayes        | +7%         |
| Logistic Regression| +12%        |
| Linear SVM         | +38%        |

---
## How to Use
1. Install requirements:  
   ```bash
   pip install -r requirements.txt
   ```
2. Run analysis:  
   ```bash
   python main.py
   ```
---
## Data Source
[Garment Productivity Dataset](https://archive.ics.uci.edu/dataset/665/garment+productivity) (UCI Machine Learning Repository)



---

### Key Highlights:
1. **Problem Focus**: Clear emphasis on detecting underperformers (business impact)
2. **Visual Aids**: Mermaid diagram for models + performance gain table
3. **Actionable Insights**:  
   - Critical thresholds (e.g., overtime >25k min = risk)  
   - Feature importance for business decisions
4. **Reproducibility**: Simple run instructions
5. **Conciseness**: Avoids jargon, uses bullet points and short sections
---


