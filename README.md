<p align="center">
  <img width="700" height="400" src="https://github.com/storm-king/TrafficSignalPrioritizer/blob/master/DemoGif.gif">
</p>

# Traffic Signal Prioritizer
  This repository is for the Traffic Signal Prioritizer final project for the Computer Vision course at UNC Charlotte. We trained a Neural Network to detect both cars and pedestrians using the feed from existing traffic cameras provided by the CityCam dataset. We then passed the output of the network into a traffic signal controller algorithm that will determine the signal for both the traffic light and the crosswalk.

## Why Did We Choose This?
  In highly populated areas such as cities, pedestrian injuries and fatalities at crosswalks can definitely be an issue. Also, 
the most widely used traffic signals only use timers and inductive loops to change traffic lights. This causes unnecessary wait times for pedestrians and no possible way to detect a potential accident if a pedestrian crosses when he/she should not. With the technology that we have today, we should be able to use Computer Vision to control these stop lights and take the statistic based guessing out of the controller altogether. 

## Approach
  We decided to go with the RetinaNet neural network created by the company Fizyr to handle our object detection. We chose this specific model because there are several pretrained models available for download, and it greatly decreased our training time since we did not have to train from scratch. Our dataset also came with bounding boxes that include class labels for each frame so we just had to convert it into a properly formatted CSV file in order to train. For our traffic controller algorithm, since our project specifically aims at protecting and assisting pedestrians across the road, we used a Human-To-Car ratio to detect if the light should change. We also put a check in the algorithm to ensure that no pedestrians are on the crosswalk while the traffic light is green. If there are, then the light immediately changes in order to prevent accidents. 

## Results
  Our neural network was able to accurately predict pedestrians and vehicles with a mean average percentage of ~86%. Vehicles specifically were predicted with a ~90% accuracy while pedestrians were slightly harder to predict at a ~82% accuracy. Although these results were not as high as we would like for the safety of pedestrians, we feel that with a greater variability in data and more training that this model could be incredibly efficient. The model was trained 10 epochs at a time since training only 10 epochs required roughly three to four hours at a time. Overall the model was trained for 30 epochs. 
    The model outputted bounding boxes for each detected object along with a class label as 0 for vehicle or 1 for passenger (pedestrian). Using these results, our traffic controller algorithm determined what the state of both the traffic signal and the crosswalk signal should be and displayed the signs. The output of our system for a single frame is as follows:
![Results](https://github.com/storm-king/TrafficSignalPrioritizer/blob/master/Results.png?raw=true "Results")
