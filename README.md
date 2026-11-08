# CalligraVision: AI-Powered Chinese Calligraphy Stroke & Proportion Analyzer

Final project for the Building AI course

## Summary

CalligraVision is an AI-powered tool designed to help calligraphy learners analyze handwritten Chinese characters, providing instant feedback on stroke order, proportions, and structure. Created as a Building AI course project.

---

## Background

Learning Chinese character calligraphy is a rewarding yet challenging discipline. Beginners often struggle with:
- **Incorrect stroke order:** Writing strokes in the wrong sequence disrupts the natural flow and balance of the character.
- **Proportion and spacing errors:** Balancing radicals within grid boundaries requires meticulous practice.
- **Lack of immediate feedback:** Traditional self-study makes it difficult to identify subtle structural mistakes without a teacher present.

My personal motivation stems from exploring the intricate rules of character construction and wanting to bridge traditional art forms with modern computer vision and machine learning.

---

## How is it used?

CalligraVision is used by students and self-taught learners practicing Chinese calligraphy at home or in the classroom. 

**The workflow:**
1. The user writes a character on paper or a digital tablet.
2. The user captures an image or uploads a scan of the written character.
3. The AI model processes the image, segments the individual strokes, and compares them against standard exemplar datasets.
4. The system highlights structural discrepancies and suggests corrections for stroke sequence and proportions.

![Calligraphy Example](https://upload.wikimedia.org/wikipedia/commons/3/36/Chinese_calligraphy_Mi_Fu.jpg)

<img src="https://upload.wikimedia.org/wikipedia/commons/3/36/Chinese_calligraphy_Mi_Fu.jpg" width="300">

---

## Data sources and AI methods

The project relies on image datasets of standard script (Kaishu) calligraphy and annotated stroke-order datasets.

| Data Source | Description |
| ----------- | ----------- |
| CASIA Chinese Handwriting Database | Offline and online Chinese character handwriting datasets |
| Custom Exemplar Set | Digitized standard model characters with labeled stroke sequences |

### AI Techniques Used:
* **Convolutional Neural Networks (CNNs):** For image classification and stroke feature extraction.
* **Sequence Modeling (RNNs / Transformers):** For tracking and validating stroke order over time.

```python
import numpy as np

def analyze_strokes(user_strokes, standard_strokes):
    # Calculate structural deviation between user and standard character
    deviations = [np.abs(u - s) for u, s in zip(user_strokes, standard_strokes)]
    mean_error = np.mean(deviations)
    
    # Return feedback score
    return max(0.0, 100.0 - (mean_error * 10))

print("Stroke analysis completed successfully.")
