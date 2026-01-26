# Sign Language Detector

A real-time Sign Language detection system that recognizes hand gestures and translates them into text. This project uses **MediaPipe** for hand tracking and landmark extraction, and a **Random Forest Classifier** (via Scikit-Learn) for gesture recognition.

## Features

- **Data Collection:** Easily collect your own dataset of hand gestures using your webcam.
- **Automated Labeling:** Processes images to extract hand landmarks (21 points per hand) for efficient training.
- **Model Training:** Trains a lightweight Random Forest classifier on the extracted landmarks.
- **Real-Time Inference:** Detects and classifies hand signs in real-time through the webcam.
- **Web Interface:** Includes a Flask-based web application for easy interaction.

## Tech Stack

- **Python**
- **OpenCV** (Image processing and video capture)
- **MediaPipe** (Hand tracking and landmark extraction)
- **Scikit-Learn** (Machine Learning model - Random Forest)
- **NumPy** (Numerical operations)
- **Flask** (Web framework)

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### 1. Collect Data
If you want to train the model on your own gestures, use the `collect_imgs.py` script.
- It creates a directory structure in `./data` for each class.
- By default, it collects data for 3 classes (0, 1, 2) with 100 images each.
- Press `Q` to start collecting for a class.

```bash
python collect_imgs.py
```

### 2. Create Dataset
Process the collected images to extract hand landmarks and save them into a pickle file (`data.pickle`).

```bash
python create_dataset.py
```

### 3. Train the Classifier
Train the Random Forest model using the processed data. The trained model will be saved as `model.p`.

```bash
python train_classifier.py
```

### 4. Run Inference
You can run the real-time inference using either the desktop script or the web application.

**Desktop Application:**
Displays a window with the webcam feed, landmarks, and prediction.
- Press `S` to save the current predicted character to a sentence.
- Press `Space` to add a space.
- Press `Q` to quit.

```bash
python inference_classifier.py
```

**Web Application:**
Starts a Flask server. Open your browser at `http://127.0.0.1:5000` to see the detection in action.

```bash
python app.py
```

## Project Structure

- `collect_imgs.py`: Script to capture images for training.
- `create_dataset.py`: Converts images to landmark features.
- `train_classifier.py`: Trains the Random Forest model.
- `inference_classifier.py`: Runs real-time detection on the desktop.
- `app.py`: Flask web app for detection.
- `model.p`: The trained model file (generated after training).
- `data.pickle`: Processed dataset (generated after processing).
- `requirements.txt`: Python dependencies.
