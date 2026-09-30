# 🍎 Fruit Image Classification Using CNN

A deep learning project that uses a Convolutional Neural Network (CNN)
to recognize fruit from an image. You give it a picture of a fruit,
and the model tells you which fruit it is and how confident it is.

---

## 📋 Objective

Build a CNN-based image classification model that takes an image as input
and predicts which fruit it is, along with a confidence score.

**Input:** an image of a fruit (e.g. apple.jpg)
**Output:** fruit name + confidence (e.g. "Apple, 99.99%")

---

## 🍏 Fruit Classes (4)

The model learns to tell these 4 fruits apart:

| Class      | Train images | Test images |
|------------|--------------|-------------|
| Apple      | ~540         | 231         |
| Banana     | ~450         | 166         |
| Orange     | ~450         | 160         |
| Strawberry | ~450         | 164         |

Total: 2160 training + 721 test images.

---

## 📂 Dataset

- **Name:** Fruits-360
- **Source:** Kaggle — `moltean/fruits`
- **Version used:** 100x100 pixel images
- The dataset is already split into `Training` and `Test` folders.
- The full dataset has 100+ fruits; only 4 were selected for this project.
- Each fruit's images live in their own folder (folder name = class name).

---

## 🧠 What is a CNN (Concept)

A CNN is a type of neural network designed for images. It looks at an
image in small pieces and detects patterns (edges, colors, shapes) —
similar to how the human eye works. This is why it performs better than
a plain ANN for image recognition.

Model layers:

| Layer         | Purpose |
|---------------|---------|
| Rescaling     | Converts pixel values (0–255) to 0–1 |
| Conv2D        | Extracts features (patterns) from the image |
| MaxPooling2D  | Shrinks the image size while keeping key info |
| Flatten       | Turns the grid into a single line |
| Dense (4)     | Final decision — outputs a score for each of the 4 classes |

---

## ⚙️ Project Steps

1. **Data download** — get the dataset into Colab via the Kaggle API
2. **Unzip** — extract the zip file
3. **Select classes** — put the 4 fruits into `dataset/train` and `dataset/test`
4. **Load data** — load in batches using `image_dataset_from_directory`
5. **Build model** — a Sequential CNN (layers above)
6. **Compile** — optimizer: `adam`, loss: `sparse_categorical_crossentropy`,
   metric: `accuracy`
7. **Train** — train the model for 5 epochs
8. **Predict** — name + confidence on a new image
9. **Classification Report** — precision, recall, f1 per fruit

---

## 📊 Results

- **Training accuracy:** 100%
- **Test (validation) accuracy:** 100%
- **Sample prediction:** Apple — 99.99% confidence

**Classification Report:**
          precision    recall  f1-score   support

Apple 1.00 1.00 1.00 231
Banana 1.00 1.00 1.00 166
Orange 1.00 1.00 1.00 160
Strawberry 1.00 1.00 1.00 164
accuracy 1.00 721


> Note: The 100% accuracy is because Fruits-360 images are very clean
> (plain background, consistent angle). Accuracy would likely be lower
> on messy real-world photos.

---

## 🛠️ Tools / Libraries

- Python
- TensorFlow / Keras (building and training the CNN)
- scikit-learn (Classification Report)
- NumPy
- Google Colab (with free GPU)

---

## ▶️ How to Run

1. Open the notebook in Google Colab
2. Go to **Runtime → Change runtime type → GPU**
3. Have your Kaggle API key (`kaggle.json`) ready
4. Run the cells in order (Step 1 to 9)
5. In the prediction cell, set the path to your own image to test it

---

## 🚀 Future Improvements

- Add more fruits (classes)
- Data augmentation (rotate, zoom images) so it works better on
  real-world photos
- Save the model to a file (`.keras`) to avoid retraining
- A small web app (e.g. Streamlit) where users upload an image and see the result
