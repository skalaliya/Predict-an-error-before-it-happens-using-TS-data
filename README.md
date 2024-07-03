# Machine Learning Environment Setup for Apple Silicon (M1 Pro) MacBook Pro

This guide provides step-by-step instructions to set up a machine learning environment on an Apple Silicon (M1 Pro) MacBook Pro using Conda and TensorFlow with Metal.

## Prerequisites

- An Apple Silicon (M1 Pro) MacBook Pro
- Conda package manager (Miniforge recommended for Apple Silicon)

## Setup Instructions

### Step 1: Install Miniforge

Miniforge is a community-driven distribution of Conda designed for Apple Silicon.

1. Download the Miniforge installer:

    ```sh
    curl -L -O https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh
    ```

2. Install Miniforge:

    ```sh
    bash Miniforge3-MacOSX-arm64.sh
    ```

3. Follow the prompts to complete the installation.

### Step 2: Create and Activate a Conda Environment

1. Create a new Conda environment named `tensor_v1` with Python 3.8:

    ```sh
    conda create -n tensor_v1 python=3.8
    ```

2. Activate the environment:

    ```sh
    conda activate tensor_v1
    ```

### Step 3: Install Dependencies Using Conda

1. Install the required dependencies:

    ```sh
    conda install -c conda-forge numpy pandas matplotlib seaborn scikit-learn scipy
    ```

### Step 4: Install TensorFlow with Metal

1. Install TensorFlow and the Metal plugin:

    ```sh
    pip install tensorflow-macos tensorflow-metal
    ```

### Step 5: Verify the Installation

1. Run a simple Python script to verify that TensorFlow is using the Metal backend:

    ```python
    import tensorflow as tf
    print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))
    ```

   The output should be:

    ```
    Num GPUs Available:  1
    ```

## Sample `requirements.txt`

Here is a sample `requirements.txt` file for reference:

```plaintext
tensorflow-macos
tensorflow-metal
numpy
pandas
matplotlib
seaborn
scikit-learn
scipy


Additional Notes
Ensure you have the latest version of pip and setuptools:

sh
Copy code
pip install --upgrade pip setuptools wheel
If you encounter any issues during the installation, try using the --no-cache-dir option with pip:

sh
Copy code
pip install --no-cache-dir -r requirements.txt
By following these instructions, you should be able to set up a compatible machine learning environment on your Apple Silicon MacBook Pro

Ensure pip and setuptools are Updated:

sh
Copy code
pip install --upgrade pip setuptools wheel

conda install -c conda-forge numpy pandas matplotlib seaborn scikit-learn scipy

import tensorflow as tf
print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))

Additional Troubleshooting
If you still encounter issues, you can manually install numpy first and then install the other dependencies:

Manually Install numpy:

sh
Copy code
pip install numpy
Install the Remaining Dependencies:

sh
Copy code
pip install pandas matplotlib seaborn scikit-learn scipy
Install TensorFlow with Metal:

sh
Copy code
pip install tensorflow-macos
pip install tensorflow-metal
Verification
After installation, verify that TensorFlow is using the Metal backend by running the following Python script:

python
Copy code
import tensorflow as tf
print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))
This should return the number of available GPUs, indicating that TensorFlow is correctly utilizing the GPU via Metal on your Apple Silicon MacBook Pro.

nstall the Required Dependencies:

Instead of specifying exact versions, we'll let pip find compatible versions for Apple Silicon. Remove the version constraints for numpy and other libraries in requirements.txt.

Here is the modified requirements.txt:

plaintext
Copy code
tensorflow-macos
tensorflow-metal
numpy
pandas
matplotlib
seaborn
scikit-learn
scipy