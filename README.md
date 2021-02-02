# udacity_mapmyworld
Git repository for Project 4 - Map My World! of [Udacity Robotics Software Engineer nanodegree](https://www.udacity.com/course/robotics-software-engineer--nd209).

## Description
By using RTABMAP functions in ROS and driving the robot via teleop, this project aims at generating a map of a 3D Gazebo world.

## Content
- my_robot: main package with RTABMAP functionalities
- teleop_twist_keyboard: package to drive the robot via teleop
- ball_chaser: leftover package from Project 1; not revelant here
- pgm_map_creator: leftover package from Project 3; not revelant here

## Pre-requisites
This project requires a Linux machine with Gazebo and ROS (including catkin and RViz), as well as all of their dependencies. 
Git is also recommended to clone this repository.

## Installation
Please follow the procedure below to be able to correctly build the project:
```
git clone https://github.com/quesiu/udacity_mapmyworld.git
cd /<YOUR_LOCAL_PATH>/udacity_mapmyworld
mkdir catkin_ws
mv Project_4/ catkin_ws/src
cd catkin_ws/src
```

## Build
Do the following to build the project:
```
cd /<YOUR_LOCAL_PATH>/udacity_mapmyworld/catkin_ws
catkin_make
```

## Usage
Do the following to be able to drive the robot and build the map:
- Open a first terminal to launch the world and robot:
```
cd /<YOUR_LOCAL_PATH>/udacity_mapmyworld/catkin_ws
source devel/setup.bash
roslaunch my_robot world.launch
```
- Open a second terminal to launch the odometry script:
```
cd /<YOUR_LOCAL_PATH>/udacity_mapmyworld/catkin_ws
source devel/setup.bash
rosrun teleop_twist_keyboard teleop_twist_keyboard.py 
```
- Open a third terminal to launch the map generation:
```
cd /<YOUR_LOCAL_PATH>/udacity_mapmyworld/catkin_ws
source devel/setup.bash
roslaunch my_robot mapping.launch 
```
- It is then possible to drive the around using teleop (*i*, *j*, *k*, *l* keys). The map will build itself.

## Vizualize your generated rtabmap.db
After the map is generating and that terminal 3 is killed (CTRL+C), simply type the following command in a Terminal:
```
rtabmap-databaseViewer ~/.ros/rtabmap.db
```

## Unzip and vizualize rtabmap.db
As the rtabmap.db file is too heavy to be uploaded directly to Github, please unzip it and move it if you want to vizualize it:
```
cd /<YOUR_LOCAL_PATH>/udacity_mapmyworld/
cat rtabmap.db.tar.bz2.parta* > map.tar.bz2
tar -xf map.tar.bz2
cp rtabmap.db.tar.gz /root/.ros/
```
Then, please use the following command to vizualize the content of the file:
```
rtabmap-databaseViewer ~/.ros/rtabmap.db
```

## Example
Result generated after driving the robot around in the newly updated building
![Generated 3D Map](https://github.com/quesiu/udacity_mapmyworld/blob/main/Generated3DMap.png)

## Support
If you have some questions or need some support, please use the [Discussions](https://github.com/quesiu/udacity_mapmyworld/discussions) section.

## License
GNU General Public License v3.0
