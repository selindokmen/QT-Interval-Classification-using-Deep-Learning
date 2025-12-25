QT interval: time between Q wave onset (R) and T wave end in ECG. Prolonged QT increases risk of dangerous arrhythmias and sudden cardiac
death. Goal: detection of prolonged QT intervals using deep learning. Task: Binary Classification (Prolonged vs Normal)

Dataset Overview
● Source: https://www.physionet.org/content/qtdb/1.0.0/
○ 105 ECG records from real patients
○ 2-channel ECG signals (MLII, V1)
○ Sampling frequency: 250 Hz
○ Length: around 15 mins each
● Annotations Used:
○ Manual (q1c): expert-marked waveform boundaries (high quality)
○ Automatic (pu): algorithm-detected boundaries (broader coverage
● We have created a balanced dataset:
○ 30000 Normal + 30000 Prolonged samples
○ Created via undersampling and oversampling
○ Final Database: 60000 ECG signal windows

Solution: Model Architecture
● Model type: 1D CNN (Convolutional Neural Network)
● Input: 3 features (samples, time_steps, channels) as required for CNN, but
our initial input was (samples, time_steps)
● Architecture:
○ Input layer: 500 neurons
○ Hidden layer: 64 neurons (in each layer) (ReLU activation)
○ Output layer: 1 neuron (Sigmoid activation)
● Loss function: Binary Crossentropy
● Optimizer: Adam
● Metric: Accuracy

Solution: Training Details
● Dataset balancing:
○ Balanced dataset created (30,000 Normal / 30,000 Prolonged)
● Train/Test Split:
○ 80% training
○ 20% testing
● Epochs: 50
● Batch size: 32
● Normalization:
○ Z-score Normalization applied before training
● Callbacks:
○ EarlyStopping (to prevent overfitting)
