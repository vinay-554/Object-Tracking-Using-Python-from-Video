# Real-Time Object Detection Using Caffe

This project demonstrates real-time object detection using a pre-trained Caffe model. The system captures video from a webcam, processes each frame to detect objects, and displays the results with bounding boxes and labels.

## Table of Contents
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Classes and Colors](#classes-and-colors)
- [FPS Counter](#fps-counter)
- [Example Output](#example-output)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This project uses OpenCV's deep learning module (`cv2.dnn`) to perform object detection with a pre-trained Caffe model. The application captures video from a webcam, detects objects in real-time, and displays the results with bounding boxes and labels.

## Requirements

- Python 3.6+
- OpenCV
- NumPy
- imutils

## Installation

1. **Clone the repository:**
   ```sh
   git clone https://github.com/your-username/object-detection-caffe.git
   cd object-detection-caffe
   ```

2. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

3. **Download the pre-trained Caffe model:**
   - Download `deploy.prototxt.txt` and `deploy.caffemodel` from the [Caffe Model Zoo](https://github.com/BVLC/caffe/wiki/Model-Zoo).
   - Place these files in the project directory.

## Usage

1. **Run the object detection script:**
   ```sh
   python detect.py -p deploy.prototxt.txt -m deploy.caffemodel -c 0.5
   ```

2. **Command-line arguments:**
   - `-p`, `--prototxt`: Path to Caffe 'deploy' prototxt file.
   - `-m`, `--model`: Path to Caffe pre-trained model.
   - `-c`, `--confidence`: Minimum probability to filter weak predictions (default: 0.2).

## How It Works

1. **Load the Model:**
   - The script loads the network structure and trained weights using the specified prototxt and caffemodel files.

2. **Initialize the Video Stream:**
   - The script starts capturing video from the webcam and initializes the FPS counter.

3. **Process Each Frame:**
   - Each frame is resized and converted to a blob format for the network.
   - The blob is fed to the network to obtain predictions.

4. **Draw Bounding Boxes and Labels:**
   - For each prediction with a confidence score above the threshold, a bounding box and label are drawn on the frame.

5. **Display the Results:**
   - The processed frame is displayed in a window. Press 'q' to exit the loop and close the window.

## Classes and Colors

The project defines a list of object classes that the model can detect. Each class is assigned a random color for drawing bounding boxes.

```python
CLASSES = ["aeroplane", "background", "bicycle", "bird", "boat", "bottle", "bus", "car", "cat", "chair", "cow", "diningtable", "dog", "horse", "motorbike", "person", "pottedplant", "sheep", "sofa", "train", "tvmonitor"]
COLORS = np.random.uniform(0, 255, size=(len(CLASSES), 3))
```

## FPS Counter

The FPS counter measures the performance of the object detection system, providing information about the elapsed time and approximate frames per second.

## Example Output

![Example Output](path-to-your-example-image.png)

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
