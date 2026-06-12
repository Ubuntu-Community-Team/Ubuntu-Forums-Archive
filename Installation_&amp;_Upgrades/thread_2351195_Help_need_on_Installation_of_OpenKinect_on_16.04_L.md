---
title: "Help need on Installation of OpenKinect on 16.04 LTS ROS Kinetic"
date: 2017-02-01
forum: Installation &amp; Upgrades
---

### Post by zmcpro2 on 2017-02-01
Hi. I am new to Ubuntu and am using 16.04 LTS. I had already installed  ROS Kinetic and I needed to get Xbox360 Kinect Model:1414 to work with  my laptop. I tried various website guides and followed the procedure  which most of them are for the previous version of Ubuntu.


First I tried github _[https://github.com/ros-drivers/openni_tracker/issues/9](https://github.com/ros-drivers/openni_tracker/issues/9)_ which gave me no such file or directory on the **first** part. My catkin workspace cmake didnt work either.
**cd Final**
tar -xjf OpenNI-Bin-Dev-Linux-x64-v1.5.7.10.tar.bz2
cd OpenNI-Bin-Dev-Linux-x64-v1.5.7.10
sudo ./install.sh
I also tried ros.org _[http://wiki.ros.org/Robots/evarobot/Tutorials/indigo/Kinect](http://wiki.ros.org/Robots/evarobot/Tutorials/indigo/Kinect)_ which I dont know what constitute the [xxx] so I tried and put cd ../Redist/OpenNI-Bin-Dev-Linux-1.5.8.5

which also gave no such file or directory.
__> git clone [https://github.com/OpenNI/OpenNI.git](https://github.com/OpenNI/OpenNI.git)
> cd OpenNI
> git checkout Unstable-1.5.4.0
> cd Platform/Linux/CreateRedist
> sudo chmod +x RedistMaker
> ./RedistMaker
**> cd ../Redist/OpenNI-Bin-Dev-Linux-[xxx]**
> sudo ./install.sh

The guide from 20papercups also gave the same [xxx].

[http://www.20papercups.net/programming/kinect-on-ubuntu-with-openni/](http://www.20papercups.net/programming/kinect-on-ubuntu-with-openni/)

cd Platform/Linux/CreateRedist
chmod +x RedistMaker
./RedistMaker
**cd ../Redist/Sensor-Bin-Linux-[xxx] (where [xxx] is your architecture and this particular OpenNI release)**
chmod +x install.sh
sudo ./install.sh



I am guessing the final step would be to use the link below to execute the program

[http://wiki.ros.org/openni_launch](http://wiki.ros.org/openni_launch)

---

