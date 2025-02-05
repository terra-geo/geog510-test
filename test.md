---

# Mycotoxins in Food: Risks for Humans and Animals

"Understanding mycotoxins, their risks, and how to mitigate contamination in food."
![Food Safety](/images/veg_fruits.png)
---------------------------------------------------------------------------------------------------

# Mycotoxins in Food: Risks for Humans and Animals

## Introduction

Mycotoxins are toxic compounds naturally produced by certain types of fungi. These toxins can contaminate various food products, posing significant health risks to both humans and animals.

## Common Types of Mycotoxins

Some of the most prevalent mycotoxins include:

- **Aflatoxins**: Found in nuts, grains, and milk products.
- **Ochratoxin A**: Present in cereals, coffee, and wine.
- **Fumonisins**: Commonly found in corn.
- **Zearalenone**: Affects grains and causes reproductive issues in animals.
- **Deoxynivalenol (DON)**: Known as "vomitoxin," commonly found in wheat and barley.

## Health Risks

### For Humans

- Liver damage and cancer (especially from aflatoxins)
- Kidney toxicity
- Weakened immune system
- Neurological problems

### For Animals

- Reduced growth and feed efficiency
- Reproductive disorders
- Organ damage
- Immune suppression leading to infections

##  Mycotoxin Contamination Levels

The following table shows the regulatory limits of some mycotoxins in food and animal feed, along with their fungal sources:

| Mycotoxin      | Regulatory Limit (ppb) | Affected Food Products | Producing Fungi |
| -------------- | ---------------------- | ---------------------- | --------------- |
| Aflatoxins     | 20                     | Nuts, grains, dairy    | *Aspergillus flavus, Aspergillus parasiticus* |
| Ochratoxin A   | 5                      | Cereals, coffee, wine  | *Aspergillus ochraceus, Penicillium verrucosum* |
| Fumonisins     | 2000                   | Corn                   | *Fusarium verticillioides, Fusarium proliferatum* |
| Zearalenone    | 100                    | Grains                 | *Fusarium graminearum, Fusarium culmorum* |
| Deoxynivalenol | 1000                   | Wheat, barley          | *Fusarium graminearum, Fusarium culmorum* |

## Prevention and Control

- **Proper Storage**: Keep food dry and cool to prevent fungal growth.
- **Food Testing**: Regular screening for mycotoxins in food production.
- **Use of Binders**: Adding mycotoxin binders to animal feed to reduce absorption.
- **Regulatory Limits**: Government agencies set maximum allowable levels of mycotoxins in food and feed.
- **Proper Handling**: Ensure good agricultural and manufacturing practices to reduce contamination.

## Resources

For more information, check the following sources:

- [World Health Organization on Mycotoxins](https://www.who.int/news-room/fact-sheets/detail/mycotoxins)
- [Food and Agriculture Organization (FAO)](https://www.fao.org/mycotoxins/en/)
- [FDA Mycotoxin Regulations](https://www.fda.gov/food/chemicals/mycotoxins-food)

## Mycotoxin Detection using Python

Detecting outliers in datasets of different mycotoxin contamination levels:

```python
import numpy as np
import matplotlib.pyplot as plt

# Sample mycotoxin concentration data (in ppb) for different mycotoxins
mycotoxins = {
    "Aflatoxins": [5, 7, 6, 8, 200, 9, 10, 6, 5, 300, 7, 8, 9],
    "Ochratoxin A": [2, 3, 4, 2, 50, 3, 2, 3, 60, 4, 2],
    "Fumonisins": [500, 700, 800, 2000, 900, 1800, 700, 600, 2100],
    "Zearalenone": [30, 40, 35, 500, 45, 100, 50, 60],
    "Deoxynivalenol": [800, 900, 950, 1000, 1500, 1200, 1100, 3000]
}

# Function to detect outliers using z-score
def detect_outliers(data):
    mean = np.mean(data)
    std_dev = np.std(data)
    z_scores = [(x - mean) / std_dev for x in data]
    outliers = [data[i] for i in range(len(z_scores)) if abs(z_scores[i]) > 2]
    return outliers, mean

# Plot each mycotoxin contamination levels
fig, axs = plt.subplots(len(mycotoxins), 1, figsize=(8, 15))

for i, (name, data) in enumerate(mycotoxins.items()):
    outliers, mean = detect_outliers(data)
    ticks = range(len(data))
    
    axs[i].plot(ticks, data, marker='o', linestyle='none', label='Data Points')
    axs[i].axhline(mean, color='r', linestyle='dashed', linewidth=1, label='Mean')
    axs[i].set_title(name)
    axs[i].legend()

plt.tight_layout()
plt.show()

# Print detected outliers for each mycotoxin type
for name, data in mycotoxins.items():
    outliers, _ = detect_outliers(data)
    print(f"{name} - Detected outliers: {outliers}")
```

