cmake_minimum_required(VERSION 2.8.3)

project(robotcar_to_rosbag)

## Find catkin and any catkin packages
find_package(catkin REQUIRED COMPONENTS 
	roscpp 
	rospy 
	rosbag
	std_msgs 
	sensor_msgs
	cv_bridge_4 
	genmsg 
	message_generation 
)

find_package(OpenCV REQUIRED)
## Declare a catkin package
catkin_package(
	# INCLUDE_DIRS include
	CATKIN_DEPENDS roscpp rospy geometry_msgs sensor_msgs std_msgs rosbag cv_bridge_4
	)


## Build talker and listener
include_directories(
	${catkin_INCLUDE_DIRS}
	${roscpp_INCLUDE_DIRS}
	${rospy_INCLUDE_DIRS}
	${OpenCV_INCLUDE_DIRS}
)

add_executable(robotcar_node src/robotcar_to_rosbag.cc)
target_link_libraries(robotcar_node ${catkin_LIBRARIES} ${OpenCV_LIBRARIES} -lstdc++fs)
add_dependencies(robotcar_node roscpp std_msgs sensor_msgs cv_bridge_4 geometry_msgs)
