---
title: "Errors in installing libyaml-cpp-dev"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by Shishir_Kolathaya on 2015-05-18
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I am using ubuntu 14.04 LTS. I was trying to install libyaml-cpp-dev in my computer and it did not work. Here is the list of sources:[/COLOR]

[COLOR=#000000]# See [/COLOR][http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes)[COLOR=#000000] for how to upgrade to[/COLOR]


[COLOR=#000000]# newer versions of the distribution.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty main restricted[/COLOR]


[COLOR=#000000]## Major bug fix updates produced after the final release of the[/COLOR]
[COLOR=#000000]## distribution.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-updates main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-updates main restricted[/COLOR]


[COLOR=#000000]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/COLOR]
[COLOR=#000000]## team. Also, please note that software in universe WILL NOT receive any[/COLOR]
[COLOR=#000000]## review or updates from the Ubuntu security team.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty universe[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-updates universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-updates universe[/COLOR]


[COLOR=#000000]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/COLOR]
[COLOR=#000000]## team, and may not be under a free licence. Please satisfy yourself as to [/COLOR]
[COLOR=#000000]## your rights to use the software. Also, please note that software in [/COLOR]
[COLOR=#000000]## multiverse WILL NOT receive any review or updates from the Ubuntu[/COLOR]
[COLOR=#000000]## security team.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty multiverse[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-updates multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-updates multiverse[/COLOR]


[COLOR=#000000]## N.B. software from this repository may not have been tested as[/COLOR]
[COLOR=#000000]## extensively as that contained in the main release, although it includes[/COLOR]
[COLOR=#000000]## newer versions of some applications which may provide useful features.[/COLOR]
[COLOR=#000000]## Also, please note that software in backports WILL NOT receive any review[/COLOR]
[COLOR=#000000]## or updates from the Ubuntu security team.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-backports main restricted universe multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] trusty-backports main restricted universe multiverse[/COLOR]


[COLOR=#000000]deb [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] trusty-security main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] trusty-security main restricted[/COLOR]
[COLOR=#000000]deb [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] trusty-security universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] trusty-security universe[/COLOR]
[COLOR=#000000]deb [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] trusty-security multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] trusty-security multiverse[/COLOR]


[COLOR=#000000]## Uncomment the following two lines to add software from Canonical's[/COLOR]
[COLOR=#000000]## 'partner' repository.[/COLOR]
[COLOR=#000000]## This software is not part of Ubuntu, but is offered by Canonical and the[/COLOR]
[COLOR=#000000]## respective vendors as a service to Ubuntu users.[/COLOR]
[COLOR=#000000]# deb [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] trusty partner[/COLOR]
[COLOR=#000000]# deb-src [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] trusty partner[/COLOR]


[COLOR=#000000]## This software is not part of Ubuntu, but is offered by third-party[/COLOR]
[COLOR=#000000]## developers who want to ship their latest software.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)[COLOR=#000000] trusty main[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)[COLOR=#000000] trusty main[/COLOR]


[COLOR=#000000]I ran this command:[/COLOR]
[COLOR=#000000]sudo apt-get install libyaml-cpp-dev[/COLOR]

[COLOR=#000000]Got the following error ( in the end )[/COLOR]

[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree [/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]The following packages were automatically installed and are no longer required:[/COLOR]
[COLOR=#000000]collada-dom-dev collada-dom2.4-dp-base collada-dom2.4-dp-dev fltk1.3-doc[/COLOR]
[COLOR=#000000]fluid freeglut3 gazebo2 gir1.2-gtk-2.0 hddtemp liballegro4.4[/COLOR]
[COLOR=#000000]liballegro4.4-plugin-alsa libapr1 libapr1-dev libaprutil1 libaprutil1-dev[/COLOR]
[COLOR=#000000]libassimp-dev libassimp3 libatk1.0-dev libavcodec-dev libavformat-dev[/COLOR]
[COLOR=#000000]libavutil-dev libbz2-dev libcairo-script-interpreter2 libcairo2-dev[/COLOR]
[COLOR=#000000]libcegui-mk2-0.7.6 libcegui-mk2-dev libcf0 libconsole-bridge-dev[/COLOR]
[COLOR=#000000]libconsole-bridge0.2 libcurl4-openssl-dev libcv-dev libcvaux-dev[/COLOR]
[COLOR=#000000]libdc1394-22-dev libdevil-dev libdevil1c2 libflann-dev libflann1.8[/COLOR]
[COLOR=#000000]libfltk-cairo1.3 libfltk-forms1.3 libfltk-gl1.3 libfltk-images1.3 libfltk1.1[/COLOR]
[COLOR=#000000]libfltk1.3 libfltk1.3-dev libfontconfig1-dev libfreeimage-dev libfreeimage3[/COLOR]
[COLOR=#000000]libfreetype6-dev libgdk-pixbuf2.0-dev libgeos-3.4.2 libgeos-c1 libgl2ps-dev[/COLOR]
[COLOR=#000000]libgl2ps0 libglib2.0-dev libgnomecanvas2-0 libgnomecanvas2-common[/COLOR]
[COLOR=#000000]libgtk2.0-dev libharfbuzz-dev libharfbuzz-gobject0 libhdf5-7 libhighgui-dev[/COLOR]
[COLOR=#000000]libice-dev libidn11-dev libilmbase-dev libjasper-dev liblcms1-dev[/COLOR]
[COLOR=#000000]liblcms2-dev libldap2-dev liblodo3.0 liblog4cxx10 liblog4cxx10-dev[/COLOR]
[COLOR=#000000]liblua5.1-0 liblua5.1-0-dev liblz4-1 liblz4-dev libmng-dev libnetcdf-dev[/COLOR]
[COLOR=#000000]libnetcdfc++4 libnetcdfc7 libnetcdff5 libodbc1 libogg-dev libogre-1.8-dev[/COLOR]
[COLOR=#000000]libogre-1.8.0 libois-1.3.0 libopencv-calib3d-dev libopencv-contrib-dev[/COLOR]
[COLOR=#000000]libopencv-core-dev libopencv-dev libopencv-features2d-dev[/COLOR]
[COLOR=#000000]libopencv-flann-dev libopencv-gpu-dev libopencv-gpu2.4 libopencv-highgui-dev[/COLOR]
[COLOR=#000000]libopencv-imgproc-dev libopencv-legacy-dev libopencv-ml-dev[/COLOR]
[COLOR=#000000]libopencv-objdetect-dev libopencv-ocl-dev libopencv-ocl2.4[/COLOR]
[COLOR=#000000]libopencv-photo-dev libopencv-photo2.4 libopencv-stitching-dev[/COLOR]
[COLOR=#000000]libopencv-stitching2.4 libopencv-superres-dev libopencv-superres2.4[/COLOR]
[COLOR=#000000]libopencv-ts-dev libopencv-ts2.4 libopencv-video-dev libopencv-videostab-dev[/COLOR]
[COLOR=#000000]libopencv-videostab2.4 libopencv2.4-java libopencv2.4-jni libopenexr-dev[/COLOR]
[COLOR=#000000]libopenni-dev libopenni-sensor-pointclouds0 libopenni0 libpango1.0-dev[/COLOR]
[COLOR=#000000]libpcl-1.7-all libpcl-1.7-all-dev libpcl-1.7-bin libpcl-1.7-doc[/COLOR]
[COLOR=#000000]libpcl-apps-1.7 libpcl-apps-1.7-dev libpcl-common-1.7 libpcl-common-1.7-dev[/COLOR]
[COLOR=#000000]libpcl-features-1.7 libpcl-features-1.7-dev libpcl-filters-1.7[/COLOR]
[COLOR=#000000]libpcl-filters-1.7-dev libpcl-geometry-1.7-dev libpcl-io-1.7[/COLOR]
[COLOR=#000000]libpcl-io-1.7-dev libpcl-kdtree-1.7 libpcl-kdtree-1.7-dev[/COLOR]
[COLOR=#000000]libpcl-keypoints-1.7 libpcl-keypoints-1.7-dev libpcl-octree-1.7[/COLOR]
[COLOR=#000000]libpcl-octree-1.7-dev libpcl-outofcore-1.7 libpcl-outofcore-1.7-dev[/COLOR]
[COLOR=#000000]libpcl-people-1.7 libpcl-people-1.7-dev libpcl-recognition-1.7[/COLOR]
[COLOR=#000000]libpcl-recognition-1.7-dev libpcl-registration-1.7[/COLOR]
[COLOR=#000000]libpcl-registration-1.7-dev libpcl-sample-consensus-1.7[/COLOR]
[COLOR=#000000]libpcl-sample-consensus-1.7-dev libpcl-search-1.7 libpcl-search-1.7-dev[/COLOR]
[COLOR=#000000]libpcl-segmentation-1.7 libpcl-segmentation-1.7-dev libpcl-surface-1.7[/COLOR]
[COLOR=#000000]libpcl-surface-1.7-dev libpcl-tracking-1.7 libpcl-tracking-1.7-dev[/COLOR]
[COLOR=#000000]libpcl-visualization-1.7 libpcl-visualization-1.7-dev libpcre3-dev[/COLOR]
[COLOR=#000000]libpcrecpp0 libpixman-1-dev libplayerc++3.0 libplayerc3.0 libplayercommon3.0[/COLOR]
[COLOR=#000000]libplayercore3.0 libplayerdrivers3.0 libplayerinterface3.0 libplayerjpeg3.0[/COLOR]
[COLOR=#000000]libplayertcp3.0 libplayerwkb3.0 libpmap3.0 libpoco-dev libpococrypto9[/COLOR]
[COLOR=#000000]libpocodata9 libpocofoundation9 libpocomysql9 libpoconet9 libpoconetssl9[/COLOR]
[COLOR=#000000]libpocoodbc9 libpocosqlite9 libpocoutil9 libpocoxml9 libpocozip9 libprotoc8[/COLOR]
[COLOR=#000000]libpyside-dev libpyside-py3-1.2 libpyside1.2 libqhull-dev libqhull6[/COLOR]
[COLOR=#000000]libqwt-dev libqwt5-qt4 libqwt6 libraw1394-dev libraw1394-tools[/COLOR]
[COLOR=#000000]libreadline-dev libreadline6-dev librtmp-dev libsctp-dev libsctp1[/COLOR]
[COLOR=#000000]libsdformat-dev libsdformat1 libshiboken-dev libshiboken-py3-1.2[/COLOR]
[COLOR=#000000]libshiboken1.2 libsilly libsm-dev libstatgrab9 libswscale-dev libtbb-dev[/COLOR]
[COLOR=#000000]libtheora-dev libtinfo-dev libtinyxml-dev liburdfdom-dev[/COLOR]
[COLOR=#000000]liburdfdom-headers-dev liburdfdom-model-state0.2 liburdfdom-model0.2[/COLOR]
[COLOR=#000000]liburdfdom-sensor0.2 liburdfdom-world0.2 libvtk-java libvtk5-dev[/COLOR]
[COLOR=#000000]libvtk5-qt4-dev libvtk5.8 libvtk5.8-qt4 libxaw7-dev libxcb-shm0-dev[/COLOR]
[COLOR=#000000]libxcomposite-dev libxcursor-dev libxft-dev libxi-dev libxinerama-dev[/COLOR]
[COLOR=#000000]libxmu-dev libxmu-headers libxpm-dev libxrandr-dev libxrender-dev libxss-dev[/COLOR]
[COLOR=#000000]libxt-dev libzzip-0-13 libzzip-dev lksctp-tools opencv-data openni-utils[/COLOR]
[COLOR=#000000]python-matplotlib python-matplotlib-data python-netifaces python-opencv[/COLOR]
[COLOR=#000000]python-opengl python-psutil python-pydot python-pyparsing python-pyside[/COLOR]
[COLOR=#000000]python-pyside.phonon python-pyside.qtcore python-pyside.qtdeclarative[/COLOR]
[COLOR=#000000]python-pyside.qtgui python-pyside.qthelp python-pyside.qtnetwork[/COLOR]
[COLOR=#000000]python-pyside.qtopengl python-pyside.qtscript python-pyside.qtsql[/COLOR]
[COLOR=#000000]python-pyside.qtsvg python-pyside.qttest python-pyside.qtuitools[/COLOR]
[COLOR=#000000]python-pyside.qtwebkit python-pyside.qtxml python-qt4-dev python-qt4-gl[/COLOR]
[COLOR=#000000]python-qwt5-qt4 python-sip-dev python-support python-tz python-vtk[/COLOR]
[COLOR=#000000]robot-player ros-indigo-actionlib ros-indigo-actionlib-msgs[/COLOR]
[COLOR=#000000]ros-indigo-actionlib-tutorials ros-indigo-angles ros-indigo-bond[/COLOR]
[COLOR=#000000]ros-indigo-bond-core ros-indigo-bondcpp ros-indigo-bondpy[/COLOR]
[COLOR=#000000]ros-indigo-camera-calibration ros-indigo-camera-calibration-parsers[/COLOR]
[COLOR=#000000]ros-indigo-camera-info-manager ros-indigo-catkin ros-indigo-class-loader[/COLOR]
[COLOR=#000000]ros-indigo-cmake-modules ros-indigo-collada-parser ros-indigo-collada-urdf[/COLOR]
[COLOR=#000000]ros-indigo-common-msgs ros-indigo-common-tutorials[/COLOR]
[COLOR=#000000]ros-indigo-compressed-depth-image-transport[/COLOR]
[COLOR=#000000]ros-indigo-compressed-image-transport ros-indigo-control-msgs[/COLOR]
[COLOR=#000000]ros-indigo-cpp-common ros-indigo-cv-bridge ros-indigo-depth-image-proc[/COLOR]
[COLOR=#000000]ros-indigo-diagnostic-aggregator ros-indigo-diagnostic-analysis[/COLOR]
[COLOR=#000000]ros-indigo-diagnostic-common-diagnostics ros-indigo-diagnostic-msgs[/COLOR]
[COLOR=#000000]ros-indigo-diagnostic-updater ros-indigo-diagnostics[/COLOR]
[COLOR=#000000]ros-indigo-dynamic-reconfigure ros-indigo-eigen-conversions[/COLOR]
[COLOR=#000000]ros-indigo-eigen-stl-containers ros-indigo-executive-smach[/COLOR]
[COLOR=#000000]ros-indigo-filters ros-indigo-gencpp ros-indigo-genlisp ros-indigo-genmsg[/COLOR]
[COLOR=#000000]ros-indigo-genpy ros-indigo-geometric-shapes ros-indigo-geometry[/COLOR]
[COLOR=#000000]ros-indigo-geometry-msgs ros-indigo-geometry-tutorials[/COLOR]
[COLOR=#000000]ros-indigo-image-geometry ros-indigo-image-transport[/COLOR]
[COLOR=#000000]ros-indigo-joint-state-publisher ros-indigo-kdl-conversions[/COLOR]
[COLOR=#000000]ros-indigo-kdl-parser ros-indigo-message-filters[/COLOR]
[COLOR=#000000]ros-indigo-message-generation ros-indigo-message-runtime ros-indigo-nav-msgs[/COLOR]
[COLOR=#000000]ros-indigo-nodelet ros-indigo-nodelet-tutorial-math ros-indigo-octomap[/COLOR]
[COLOR=#000000]ros-indigo-orocos-kdl ros-indigo-pluginlib ros-indigo-pluginlib-tutorials[/COLOR]
[COLOR=#000000]ros-indigo-python-orocos-kdl ros-indigo-random-numbers[/COLOR]
[COLOR=#000000]ros-indigo-resource-retriever ros-indigo-rosbag[/COLOR]
[COLOR=#000000]ros-indigo-rosbag-migration-rule ros-indigo-rosbag-storage[/COLOR]
[COLOR=#000000]ros-indigo-rosbuild ros-indigo-rosclean ros-indigo-rosconsole[/COLOR]
[COLOR=#000000]ros-indigo-rosconsole-bridge ros-indigo-roscpp[/COLOR]
[COLOR=#000000]ros-indigo-roscpp-serialization ros-indigo-roscpp-traits ros-indigo-rosgraph[/COLOR]
[COLOR=#000000]ros-indigo-rosgraph-msgs ros-indigo-roslaunch ros-indigo-roslib[/COLOR]
[COLOR=#000000]ros-indigo-roslz4 ros-indigo-rosmaster ros-indigo-rosmsg ros-indigo-rosnode[/COLOR]
[COLOR=#000000]ros-indigo-rosout ros-indigo-rospack ros-indigo-rosparam ros-indigo-rospy[/COLOR]
[COLOR=#000000]ros-indigo-rosservice ros-indigo-rostest ros-indigo-rostime[/COLOR]
[COLOR=#000000]ros-indigo-rostopic ros-indigo-rosunit ros-indigo-roswtf[/COLOR]
[COLOR=#000000]ros-indigo-self-test ros-indigo-sensor-msgs ros-indigo-shape-msgs[/COLOR]
[COLOR=#000000]ros-indigo-shape-tools ros-indigo-smach ros-indigo-smach-msgs[/COLOR]
[COLOR=#000000]ros-indigo-smach-ros ros-indigo-smclib ros-indigo-std-msgs[/COLOR]
[COLOR=#000000]ros-indigo-std-srvs ros-indigo-stereo-msgs ros-indigo-tf[/COLOR]
[COLOR=#000000]ros-indigo-tf-conversions ros-indigo-tf2 ros-indigo-tf2-msgs[/COLOR]
[COLOR=#000000]ros-indigo-tf2-py ros-indigo-tf2-ros ros-indigo-topic-tools[/COLOR]
[COLOR=#000000]ros-indigo-trajectory-msgs ros-indigo-turtle-actionlib ros-indigo-turtle-tf[/COLOR]
[COLOR=#000000]ros-indigo-turtle-tf2 ros-indigo-turtlesim ros-indigo-urdf[/COLOR]
[COLOR=#000000]ros-indigo-urdf-parser-plugin ros-indigo-visualization-msgs[/COLOR]
[COLOR=#000000]ros-indigo-xmlrpcpp sbcl shiboken sip-dev tango-icon-theme tcl-vtk[/COLOR]
[COLOR=#000000]tcl8.6-dev tk8.6-dev uuid-dev x11proto-composite-dev x11proto-randr-dev[/COLOR]
[COLOR=#000000]x11proto-render-dev x11proto-scrnsaver-dev x11proto-xinerama-dev[/COLOR]
[COLOR=#000000]Use 'apt-get autoremove' to remove them.[/COLOR]
[COLOR=#000000]The following NEW packages will be installed:[/COLOR]
[COLOR=#000000]libyaml-cpp-dev[/COLOR]
[COLOR=#000000]0 upgraded, 1 newly installed, 0 to remove and 424 not upgraded.[/COLOR]
[COLOR=#000000]456 not fully installed or removed.[/COLOR]
[COLOR=#000000]Need to get 0 B/339 kB of archives.[/COLOR]
[COLOR=#000000]After this operation, 1,460 kB of additional disk space will be used.[/COLOR]
[COLOR=#000000](Reading database ... 305597 files and directories currently installed.)[/COLOR]
[COLOR=#000000]Preparing to unpack .../libyaml-cpp-dev_0.5.1-1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking libyaml-cpp-dev (0.5.1-1) ...[/COLOR]
[COLOR=#000000]dpkg: error processing archive /var/cache/apt/archives/libyaml-cpp-dev_0.5.1-1_amd64.deb (--unpack):[/COLOR]
[COLOR=#000000]trying to overwrite '/usr/lib/pkgconfig/yaml-cpp.pc', which is also in package yaml-cpp 0.2.7-5precise-20120502-0513-+0000[/COLOR]
[COLOR=#000000]dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/COLOR]
[COLOR=#000000]Errors were encountered while processing:[/COLOR]
[COLOR=#000000]/var/cache/apt/archives/libyaml-cpp-dev_0.5.1-1_amd64.deb[/COLOR]
[COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]


[COLOR=#000000]Note: I was trying to install ros-indigo which lead to this dependency problem. Any help is appreciated. Thanks.[/COLOR]

---

### Post by Vladlenin5000 on 2015-05-18
Hi and welcome.

I see one problem and another potential one to start with.

**First issue: System not updated.**
```
[COLOR=#000000]0 upgraded, 1 newly installed, 0 to remove and [/COLOR][COLOR=#ff0000]424 not upgraded[/COLOR][COLOR=#000000].[/COLOR]
[COLOR=#000000]456 not fully installed or removed.[/COLOR]
```

Please do
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
and post back any errors. However, if successful, then I would also do the recommend house cleaning:
```
sudo apt-get autoremove
```

The **potential problem** is this:
```
[COLOR=#000000]trying to overwrite '/usr/lib/pkgconfig/yaml-cpp.pc', which is also in package yaml-cpp 0.2.7-5[/COLOR][COLOR=#ff0000]precise[/COLOR][COLOR=#000000]-20120502-0513-+0000[/COLOR]
[COLOR=#000000]dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/COLOR]
```
Why would you have a Ubuntu 12.04 (precise) package in an otherwise Ubuntu 14.04 (trusty)? Have you upgrade from 12.04 to 14.04? If so you might want to read this: [http://answers.ros.org/question/196206/libyaml-cpp-dev-cannot-be-installed-dependencies/](http://answers.ros.org/question/196206/libyaml-cpp-dev-cannot-be-installed-dependencies/)

---

