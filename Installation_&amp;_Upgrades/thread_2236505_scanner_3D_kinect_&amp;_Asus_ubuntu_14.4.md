---
title: "scanner 3D kinect &amp; Asus ubuntu 14.4"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by david259 on 2014-07-27
good peers have to say that the new version of this new drive is giving problems with MRPT programs and websites RTABmap: 

[https://code.google.com/p/rtabmap/wiki/Installation](https://code.google.com/p/rtabmap/wiki/Installation) # ROS_version 
[http://www.mrpt.org/](http://www.mrpt.org/) 

the new version of this driver created with conflicts, in many programs, both in one or another fail, use ubuntu 14.4, ROS indigo, PCL OPENCV 1.7 and 2.4.9, PYTHON 2.7, my personal opion is that this whole thing messy, lack COORDINATION for the two pack of robotics, and comment on web of peers, that there must be a driver for: kinect and asus, generalized to work with any program needs to install additional packages, which we believe these conflicts that fail to app store, leave the link to the comments of the web, where colleagues can see console errors with this pack giving robotics, also have to say that the program compiles fine, but when we are at the interface gives errors 

RTABmap [https://code.google.com/p/rtabmap/wiki/RGBDExample](https://code.google.com/p/rtabmap/wiki/RGBDExample) 

RTABmap (ROS) error >> max @ max-To-be-filled-by-OEM: ~ $ roslaunch openni_launch openni.launch 
[openni.launch] is neither a launch file in package [openni_launch] nor is [openni_launch] file name to launch 
The traceback for the exception was written to the log file 
Traceback (most recent call last): 
   File "/ opt / ros / indigo / bin / roslaunch", line 35, in <module> 
     roslaunch.main () 
   File "/ opt/ros/indigo/lib/python2.7/dist-packages/roslaunch/__init__.py", line 292, in main 
     logger.error (traceback.format_exc ()) 
UnboundLocalError: local variable 'logger' referenced before assignment 
max @ max-To-be-filled-by-O-M-E: ~ $ 

MRPT has a very good guide in app and very functional there till we install the ROS kinect driver stop working, buggy console like this 

  ~ $ '/ Usr/bin/kinect-3d-slam' 
Waiting for sensor initialization ... 
Warning: Calibration file [kinect_calib.cfg] not found -> Using default params. 
Calling CKinect :: initialize () ... OK 
[CSemaphore :: waitForSignal] named'' In semaphore, error: Interrupted system call to 
[WxSubsystem :: createOneInstanceMainThread] Timeout waiting wxApplication to start up! 
Waiting for grabbing thread to exit ... 
Bye! 

  app store error when I try to install the old driver OpenNI 

installArchives () failed: (Reading database ... 
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25% 
(Reading database ... 30% 
(Reading database ... 35% 
(Reading database ... 40% 
(Reading database ... 45% 
(Reading database ... 50% 
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65% 
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95% 
(Reading database ... 100% 
(Reading database ... 264260 files and directories currently installed.) 
Preparing to unpack ... / libopenni-sensor-pointclouds0_5.1.0.41.1-1_amd64.deb ... 
Unpacking libopenni-sensor-pointclouds0 (5.1.0.41.1-1) ... 
dpkg: error processing archive / var/cache/apt/archives/libopenni-sensor-pointclouds0_5.1.0.41.1-1_amd64.deb (- unpack): 
  trying to overwrite '/ usr/lib/libXnDDK.so.0', que is also in package libopenni-sensor-primesense0 5.1.0.41-3 + trusty1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Preparing to unpack ... / libopenni-sensor-PointClouds-dev_5.1.0.41.1-1_amd64.deb ... 
Unpacking libopenni-sensor-PointClouds-dev (5.1.0.41.1-1) ... 
dpkg: error processing archive / var/cache/apt/archives/libopenni-sensor-pointclouds-dev_5.1.0.41.1-1_amd64.deb (- unpack): 
  trying to overwrite '/ usr / lib / pkgconfig / ps-engine.pc', que is also in package libopenni-sensor-PrimeSense-dev 5.1.0.41-3 + trusty1 
Errors Were Encountered while processing: 
  / var/cache/apt/archives/libopenni-sensor-pointclouds0_5.1.0.41.1-1_amd64.deb 
  / var/cache/apt/archives/libopenni-sensor-pointclouds-dev_5.1.0.41.1-1_amd64.deb 
Error in function:

I think the diagram of the packages in the app store would have to be ordered as follows 

science and engineering> computing> MRPT-GUI> kinect> OpenNI & Freenect >> asus> openNI2 

science and engineering> computing> RTABmap-GUI> kinect> OpenNI & Freenect >> asus> openNI2 

science and engineering> computing> RTABmap-ROS-GUI> kinect> OpenNI & Freenect >> asus> openNI2 

so we will not create conflicts or driver failures with OpenNI (ROS) and OpenNI

---

