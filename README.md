# yolov7-instance-segmentation

## Coming Soon
- Development of streamlit dashboard for Instance-Segmentation with Object Tracking

## Code Medium Blog
- https://chr043416.medium.com/train-yolov7-segmentation-on-custom-data-b91237bd2a29

## Steps to run Code

- Clone the repository
```
git clone https://github.com/RizwanMunawar/yolov7-segmentation.git
```
- Goto the cloned folder.
```
cd yolov7-segmentation
```
- Create a virtual envirnoment (Recommended, If you dont want to disturb python packages)
```
### For Linux Users
python3 -m venv yolov7seg
source yolov7seg/bin/activate

### For Window Users
python3 -m venv yolov7seg
cd yolov7seg
cd Scripts
activate
cd ..
cd ..
```
- Upgrade pip with mentioned command below.
```
pip install --upgrade pip
```
- Install requirements with mentioned command below.
```
pip install -r requirements.txt
```
- Download weights from [link](https://github.com/RizwanMunawar/yolov7-segmentation/releases/download/yolov7-segmentation/yolov7-seg.pt) and store in "yolov7-segmentation" directory.

- Run the code with mentioned command below.
```
#for segmentation with detection
python3 segment/predict.py --weights yolov7-seg.pt --source "videopath.mp4"

#for segmentation with detection + Tracking
python3 segment/predict.py --weights yolov7-seg.pt --source "videopath.mp4" --trk

#save the labels files of segmentation
python3 segment/predict.py --weights yolov7-seg.pt --source "videopath.mp4" --save-txt
```

- Output file will be created in the working directory with name <b>yolov7-segmentation/runs/predict-seg/exp/"original-video-name.mp4"</b>

### RESULTS
<table>
  <tr>
    <td>Car Semantic Segmentation</td>
     <td>Car Semantic Segmentation</td>
     <td>Person Segmentation + Tracking</td>
     </tr>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62513924/190402435-931f0ee3-9af1-4399-8222-1028d5afbd1a.png" width=640 height=180></td>
    <td><img src="https://user-images.githubusercontent.com/62513924/190402752-521b7815-bea8-4cef-8b36-54fb7a962244.png" width=640 height=180></td>
    <td><img src="https://user-images.githubusercontent.com/62513924/191729411-a8d8b5e2-bdbf-4c0e-bd1b-a52e23f7c9d3.png" width=640 height=180></td>
  </tr>
  </tr>
 </table>


## Custom Training

- Move your (segmentation custom labelled data) inside "yolov7-segmentation\data" folder by following mentioned structure.



![ss](https://user-images.githubusercontent.com/62513924/190388927-62a3ee84-bad8-4f59-806f-1185acdc8acb.png)



- Go to the <b>data</b> folder, create a file with name <b>custom.yaml</b> and paste the mentioned code below inside that.

```
train: "path to train folder"
val: "path to validation folder"
# number of classes
nc: 1
# class names
names: [ 'car']
```

- Download weights from the <a href= "https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-seg.pt">link</a> and move to <b>yolov7-segmentation</b> folder.
- Go to the terminal, and run mentioned command below to start training.
```
python3 segment/train.py --data data/custom.yaml \
                          --batch 4 \
                          --weights "yolov7-seg.pt"
                          --cfg yolov7-seg.yaml \
                          --epochs 10 \
                          --name yolov7-seg \
                          --img 640 \
                          --hyp hyp.scratch-high.yaml
```

## Custom Model Detection Command
```
python3 segment/predict.py --weights "runs/yolov7-seg/exp/weights/best.pt" --source "videopath.mp4"
```

## RESULTS
<table>
  <tr>
    <td>Car Semantic Segmentation</td>
     <td>Car Semantic Segmentation</td>
     <td>Person Segmentation + Tracking</td>
     </tr>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62513924/190402435-931f0ee3-9af1-4399-8222-1028d5afbd1a.png" width=640 height=180></td>
    <td><img src="https://user-images.githubusercontent.com/62513924/190410343-ada838c6-e505-4248-8a76-fbc5996e091e.png" width=640 height=180></td>
    <td><img src="https://user-images.githubusercontent.com/62513924/191729411-a8d8b5e2-bdbf-4c0e-bd1b-a52e23f7c9d3.png" width=640 height=180></td>
  </tr>
  </tr>
 </table>


