# Run robot arm package using Ros studio development
## Prerequisites 
1. Registre in [ROS Development Studio](https://www.theconstructsim.com/rds-ros-development-studio/?utm_source=youtube&utm_medium=ros_q_a_150).
2. Create a New Rosject.
     * choose melodic in Ros Distro .
     * choose any name.
     * If you want it private click on Make it private.
     * Click on create, now you can test robot arm package.

## Catkin workspace
A catkin workspace is a directory (folder) in which you can create or modify existing catkin packages. The catkin structure simplifies the build and installation process for your [ROS](http://wiki.ros.org/catkin/Tutorials) packages.

Type the following commands to clone the [repository](https://github.com/smart-methods/arduino_robot_arm ) inside the src folder which is in catkin_ws and add a package of arduino_robot_arm.
```
 $ cd ~/catkin_ws/src
 $ sudo apt install git
 $ git clone https://github.com/smart-methods/arduino_robot_arm 

```
Then install all the dependencies.
```
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
$ sudo apt-get install ros-melodic-moveit
$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control

```
``
NOTE: You might faced an error in the two last commands, don't worry there is a solution.
``

You need to update 
```
$ sudo apt update
```
Then compile the package 
```
$ catkin_make
```
**Now the pakage is installed .**

## Run robot arm package by Rviz & Gazebo simulation
- When run the following command RVIZ will open up and show the robot arm.
```
$ roslaunch robot_arm_pkg check_motors.launch
```

https://user-images.githubusercontent.com/74800962/125542688-90f6707b-a53a-46fb-95e0-55b16db7d452.mov

- After run the following command Gazebo will open up and show the robot arm .
```
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
```

https://user-images.githubusercontent.com/74800962/125542699-9a0f1c22-37ed-4dd3-af8e-8f240b9c7e01.mov


## Control RViz and gazebo at the same time 
As normal when running RViz and gazebo at the same time, change motors angles on RViz doesn't change on gazebo, so I need to connect them. 

Before running the command -to connect them- ,you need to give it execution permissions
```
$ cd catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts
$ sudo chmod +x joint_states_to_gazebo.py
```
Then run it
```
$ rosrun robot_arm_pkg joint_states_to_gazebo.py
```
Now you can control the arm by Rviz and Gazebo at the same time!
#### Output Sample


https://user-images.githubusercontent.com/74800962/125543952-4b34b691-97c2-4b0b-be16-c1c2678c259b.mov




