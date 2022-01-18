# Writeup: Track 3D-Objects Over Time

### Step 1:Tracking - Track objects over time with a Kalman Filter.

![final2](https://user-images.githubusercontent.com/22205974/149880015-f7691858-2a60-4df6-9673-a4fdac374244.PNG)
![final1](https://user-images.githubusercontent.com/22205974/149880029-f412fb60-a888-4e13-bbda-5d8b4f462001.PNG)

### Step 2:Track Management - Initalize, update and delete tracks.

![final4 1](https://user-images.githubusercontent.com/22205974/149880766-0f65032b-1ef0-4a6c-8604-4745ec3c529d.PNG)

### Step 3:Data Association - Associate measurements to tracks with nearest neighbor association.
![final4 2](https://user-images.githubusercontent.com/22205974/149880914-7a9881e5-7721-4fbd-a824-afe76017fa16.PNG)

### Step 4:Sensor Fusion - Fuse measurements from lidar and camera.
![final6](https://user-images.githubusercontent.com/22205974/149880308-077fe0bd-18d9-4917-9a8e-10b017bc7229.PNG)

### 1. Write a short recap of the four tracking steps and what you implemented there (filter, track management, association, camera fusion). Which results did you achieve? Which part of the project was most difficult for you to complete, and why?

Filter:
Initialized Extended Kalman Filter. Initialized model matrix F() and covariance matrix Q(), to calculate the constant velocity. Implemented the residual and residual covariance.  
The measurement function evaluated at the current state, h(x), and the Jacobian H. Takes and updates state covariance matrix P in track object.

Track management:
Manage track list by updating old tracks, creating new tracks or deleting ghost tracks. Initialize empty track list(last=-1, numberoftracks=0). Take unassigned track list and drop the unassigned track score. Loop through all tracks in the list to decide if the track needs to be deleted based on track state, track covariance matrix P and the track score. Create new tracks from the unassigned measurement list.

Assocation:
Update unassigned track list, unassigned measurement list and match measurements to corresponding track. First intialized with an empty unassigned track list, association matrix, and measurement list. The track list from track management and sensor management are matched. Nearest neighbor. RMSE plot. 

Camera Fusion:
Camera measurements to update State X and state covariance matrix P. Produce output video.

### What part was the most difficult?
The part that was the most difficult was track management. I had multiple ghost tracks and I was not deleting initialized tracks.


### 2. Do you see any benefits in camera-lidar fusion compared to lidar-only tracking (in theory and in your concrete results)? 
The benefits in camera-lidar fusion compared to lidar only tracking is that cameras have more resolution and fps than lidar and the 3D image of Lidar is extremely accurate because lasers are not effected by shadows and sunlight. Lidar creates a visual map of its surroundings. Camera images provide dense texture while Lidar provides accurate depth. Cameras help correct Lidar false positives as detected in the Lidar BEV.


### 3. Which challenges will a sensor fusion system face in real-life scenarios? Did you see any of these challenges in the project?
A challenge sensor fusion systems face in real-life senarios is that, the sensor cannot perform in extreme weather conditions. In the project camera measurements were less accurate than lidar measurements.


### 4. Can you think of ways to improve your tracking results in the future?
In the future, using Joint Probablistic Data Association (JPDA) will improve the tracking results. Implementing measurement noise and process noise with non-zero mean, also tuning covariances are possible ways to improve tracking results.


