# object-detection

we can real time detection on your webcam 
```
cap = cv2.VideoCapture(1)

# check if the video is opened correctly
if not cap.isOpened():
    cap = cv2.VideoCapture(0)
if not cap.isOpened():
    raise IOError("Cannot open webcam")
    
font_scale = 3
font = cv2.FONT_HERSHEY_PLAIN

while True :
    ret, frame = cap.read()
    ClassIndex, confidece, bbox = model.detect(frame, confThreshold=0.55)
    print(ClassIndex)
    if (len(ClassIndex) != 0):
        for ClassInd, conf, boxes in zip (ClassIndex.flatten(), confidece.flatten(), bbox):
            if (ClassInd <= 80):
                cv2.rectangle(frame, boxes,(255,0,0),2)
                cv2.putText(frame, classLabels[ClassInd - 1], (boxes[0]+10, boxes[1]+40), font, fontScale = font_scale, color = (0, 255,0), thickness = 3)
                
    cv2.imshow("Object Detection Tutorial", frame)
    if cv2.waitKey(2) & 0xFF == ord('q'):
        break
        
cap.release()
cv2.destroyAllWindows()
```
### see my result :

![90240](https://user-images.githubusercontent.com/72302421/171662462-5a13bf59-79cd-4dd4-b660-785879172c53.jpg)

#### source from youtube : DeepLearning_by_PhDScholar
