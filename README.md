# CRLab-universal_robot
This is a package for ur5 universal robot, already tested on a real ur5 robot with software version 3.5.1.

__Installation from Source__  
There are releases available for ROS Hydro and ROS Indigo. However, for the latest features and developments you might want to install from source.

First set up a catkin workspace (see [this tutorials](http://wiki.ros.org/catkin/Tutorials)).  
Then clone the repository into the src/ folder.
Make sure to source the correct setup file according to your workspace hierarchy, then use ```catkin_make``` to compile.

Note that this package depends on ur_msgs, hardware_interface, and controller_manager so it cannot directly be used with ROS versions prior to hydro. If you do not have hardware_interface and controller_manager, install ros_control. (see [this tutorials](http://wiki.ros.org/ros_control))

__Usage with real hardware__

If you would like to run this package to connect to the hardware, you only need to run the following launch file.
```
roslaunch ur_modern_driver ur5_bringup.launch robot_ip:=ROBOT_IP_ADDRESS
```

Where ROBOT_IP_ADDRESS is your UR arm's IP. The above launch file makes calls to both roscore and the launch file to the ur5_description.

You may want to run MoveIt to plan and execute actions on the arm. You can do so by simply entering the following commands after launching ```ur_modern_driver```:
```
roslaunch ur5_moveit_config ur5_moveit_planning_executing.launch
roslaunch ur5_moveit_config moveit_rviz.launch config:=true
```
