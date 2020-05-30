## Requirements
The code depends on keras, h5py, numpy, cv2, scipy and moviepy, all of which can be easily installed using pip:
```shell
pip install keras h5py numpy scipy opencv-python moviepy
```  
Keras was used with the TensorFlow backend. 

## Dataset
One speaker's videos are downloaded from the [GRID Corpus](http://spandh.dcs.shef.ac.uk/gridcorpus/),

Next, strip the audio part of each video and save as the same filename with extension `.mpg` replaced with `.wav`.  
The supplied `strip_audio.sh` script can be used (requires `ffmpeg`).
```shell
cd dataset
sh strip_audio.sh
```


#### Preprocess data
```shell
cd ../code
python process_data.py
```

## Training a new model from scratch
```shell
python train.py
```
Training one entire GRID speaker (1000 videos) with the supplied settings takes ~12 hours on one Titan Black GPU.

#### Generate video samples with reconstructed audio
```shell
python gen_samples.py
```
Samples will appear under `../results/samples/`

## Use the model to predict and generate samples
python predict.py --weight_path <path_to_weights>
python gen_samples.py --respath '../pretrained_results'

Samples will appear under `../pretrained_results/samples/`


