# 🎨 Air-Canvas-project

> Draw in the air using just your webcam and a colored object\! This interactive application, built with Python and OpenCV, tracks a specific color in real-time and uses its movement to draw on a digital canvas.

*(You should create your own GIF and replace the link above to showcase your project\!)*

-----

## ✨ Features

  * **Real-time Drawing**: See your creations come to life instantly on a separate canvas.
  * **Color-Based Tracking**: Uses HSV color space for robust object detection.
  * **Live Color Calibration**: An intuitive "Color detectors" window with trackbars allows you to easily calibrate the application to track any colored object.
  * **Multiple Drawing Colors**: Choose between **Blue**, **Green**, **Red**, and **Yellow** to draw with.
  * **Active Color Indicator**: A visual highlight shows which drawing color is currently selected.
  * **Clear Canvas Function**: A dedicated button to wipe the canvas clean and start over.
  * **Interactive UI**: All controls (color selection, clear) are integrated directly into the live camera feed.

-----

## 🛠️ Technology Stack

  * **Python 3.x**
  * **OpenCV**: For camera access, computer vision, and GUI elements.
  * **NumPy**: For efficient numerical operations and image array manipulation.

-----

## 🚀 Getting Started

Follow these instructions to get a copy of the project up and running on your local machine.

### Prerequisites

  * Python 3.7 or higher
  * A webcam connected to your computer

### Installation

1.  **Clone the repository:**

    ```sh
    git clone https://github.com/vickysuraj01/Air-Canvas-project.git
    cd Air-Canvas-project
    ```

2.  **Install the required Python packages:**
    It's recommended to use a virtual environment.

    ```sh
    # Create and activate a virtual environment (optional but recommended)
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

    # Install dependencies
    pip install opencv-python numpy
    ```

-----

## 🏃 How to Run the Application

Once the installation is complete, run the main script from your terminal:

```sh
python Air-canvas.py
```

*Make sure you name your Python file `Air-canvas.py` or change the command accordingly.*

The application will launch, and you will see three windows:

1.  **Tracking**: Your live webcam feed with the UI overlay.
2.  **Paint**: The clean canvas where your drawings will appear.
3.  **Color detectors**: A control panel with sliders to configure the marker color.

-----

## 🎨 How to Use

1.  **Calibrate the Marker Color**:

      * Hold the object you want to use as a marker (e.g., a blue pen cap) in front of the webcam.
      * Adjust the **Hue**, **Saturation**, and **Value** sliders in the **"Color detectors"** window.
      * Watch the **"mask"** window. Your goal is to make your object appear as a solid **white** shape on a completely **black** background. This isolates the color for tracking.

    > **Tip**: For a **blue** object, start with a Hue range of approximately `100-130`.

2.  **Select a Drawing Color**:

      * Once the marker is being tracked (a yellow circle will appear around it), move it to the top of the **"Tracking"** window.
      * Hover over one of the color rectangles (**BLUE**, **GREEN**, **RED**, **YELLOW**).
      * The selected color will be highlighted with a white border, indicating it's now the active drawing color.

3.  **Start Drawing\!**

      * Move your marker into the main area of the screen (below the buttons).
      * The application will draw a line following the path of your marker.

4.  **Clear the Canvas**:

      * To erase everything, move your marker over the **"CLEAR ALL"** button. The canvas in the **"Paint"** window will be reset.

5.  **Stop a Line**:

      * To stop drawing a continuous line, simply move your marker out of the camera's view for a moment and then bring it back.

6.  **Quit the Application**:

      * Press the **'q'** key on your keyboard while any of the OpenCV windows are active.

-----

## 🔧 How It Works

1.  **Video Capture**: The application captures video frames from the default webcam.
2.  **Color Space Conversion**: Each frame is converted from the BGR color space to **HSV (Hue, Saturation, Value)**. HSV is more effective for color detection as it separates color (Hue) from lighting and intensity.
3.  **Masking**: Based on the HSV range set by the trackbars, a binary mask is created. Pixels within the range become white, and all others become black.
4.  **Contour Detection**: The code applies morphological transformations (erosion and dilation) to reduce noise in the mask and then finds the contours of the white areas.
5.  **Centroid Tracking**: It identifies the largest contour, calculates its center (centroid), and uses this point as the marker's position.
6.  **Action Handling**:
      * If the centroid's position is within the UI button area, it triggers an action (change color or clear).
      * If the centroid is in the drawing area, its coordinates are stored in a list (`deque`) corresponding to the currently selected color.
7.  **Drawing Lines**: The application iterates through the list of stored points and draws lines between them on both the live feed and the separate paint canvas, creating the final artwork.

-----

----------------------------------------Suraj Gupta---------------------------------------------
