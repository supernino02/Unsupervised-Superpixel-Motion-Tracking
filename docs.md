# Project Documentation

## Setup & Execution

1. First, make sure you have the required dependencies installed. You can install them using the provided `requirements.txt` file by running:
   ```bash
   pip install -r requirements.txt
   ```
2. Open the `notebook.ipynb` using Jupyter Notebook, JupyterLab, or Visual Studio Code.
3. Because the heavy processing required for analyzing entire video sequences frame-by-frame is time-consuming, the repository relies on cached results. The notebook will automatically retrieve the videos preloaded inside the directory structure, avoiding the need to re-execute the detection from scratch.
4. There is a static PDF version of the notebook provided as a quick reference without the active layout or video widgets.

## Files and Directory Structure

### `notebook.ipynb`
The main notebook where the execution takes place. It features an Object-Oriented sequence comprising wrapper functions, superpixel generation, distance kernels, graph matching algorithms, and object spatial trackers.

### `images/`
Contains the raw input frames divided into different scenarios to evaluate the custom computer vision pipeline's robustness on various moving targets.
* `dancer/`, `peoples/`, `stennis/`: Various subsets containing the extracted static frames (such as `.ppm`). These are utilized to compute distance masks, test SLIC segmentation, and visually evaluate kernel thresholds in the notebook.
* `video/`: Sequence images showcasing the actual video components evaluated in the preliminary steps.

### `video_exports/`
The repository's cache system stores fully processed videos herein to save computation time.
* `basic/`: Contains the initial unrefined detection passes (simple superpixel mapping and bounding-box rendering) for sets like `peoples`, `subway`, and `tennis`.
* `interpolated/`: Features the detection outputs after applying smoothing and interpolation parameters to steady the bounding-boxes dynamically.
* `metadata.json` files: Inside these outputs directories, the metadata files document configuration parameters (e.g., number of segments, kernel weights) and tracking coordinates used over the span of the corresponding video.
