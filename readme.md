cd download
wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
sha256sum Anaconda3-2020.02-Linux-x86_64.sh
bash Anaconda3-2020.02-Linux-x86_64.sh

# https://docs.anaconda.com/anaconda/install/linux/

conda create --name tnfl python=3.6
conda activate tnfl 

# download model directory and checkout
git clone https://github.com/tensorflow/models
cd models
git checkout 57e0752


# conda packages install
conda install tensorflow-gpu==1.13.1
conda install -c conda-forge shapely
conda install protobuf

git clone https://github.com/sourav164/tnfl_install.git
pip install -r requirements.txt

# from object detection 
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1TXhM0l3LWqb4YIyFwjRwWdYRFUJzdfd8' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1TXhM0l3LWqb4YIyFwjRwWdYRFUJzdfd8" -O images.zip && rm -rf /tmp/cookies.txt



protoc object_detection/protos/*.proto --python_out=.
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
