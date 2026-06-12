---
title: "Can't install updates ubuntu says package system is broken."
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by angelo8 on 2015-02-02
I've been trying to update ubuntu and I won't let me every time I do the software update it says 

The package system is broken check if you are using third party repositories. Also run the terminal command apt-get install -f. I've run that command and it doesn't help. How do I fix this problem?

---

### Post by Elfy on 2015-02-02
Did you check 3rd party repo's? 

Try opening a terminal and running the following. Paste the whole output here for people to check. 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by angelo8 on 2015-02-02
How do I check for third party repo's?

Well here is my code anyway.

```
angelo@angelo-Satellite-S55t-B:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for angelo: 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://linux.dropbox.com trusty InRelease                                  
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://linux.dropbox.com trusty Release.gpg                                
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security Release                         
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Get:3 http://dl.google.com stable/main amd64 Packages [1,224 B]                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:4 http://packages.osrfoundation.org trusty InRelease [2,801 B]             
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://linux.dropbox.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Get:5 http://dl.google.com stable/main i386 Packages [1,198 B]                 
Get:6 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:7 http://packages.osrfoundation.org trusty/main amd64 Packages [22.7 kB]   
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://linux.dropbox.com trusty/main amd64 Packages                        
Hit http://packages.ros.org trusty InRelease                                   
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://linux.dropbox.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://packages.ros.org trusty/main amd64 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Get:8 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Get:9 http://us.archive.ubuntu.com trusty-updates Release [62.0 kB]            
Get:10 http://packages.osrfoundation.org trusty/main i386 Packages [18.8 kB]   
Hit http://packages.ros.org trusty/main i386 Packages                          
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Get:11 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Ign http://linux.dropbox.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Ign http://packages.ros.org trusty/main Translation-en_US                      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Ign http://linux.dropbox.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Ign http://packages.ros.org trusty/main Translation-en                         
Get:12 http://ppa.launchpad.net trusty/main amd64 Packages [29.1 kB]           
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Get:13 http://ppa.launchpad.net trusty/main i386 Packages [29.1 kB]            
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Ign http://packages.osrfoundation.org trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Ign http://packages.osrfoundation.org trusty/main Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Get:14 http://ppa.launchpad.net trusty/main Translation-en [11.4 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:15 http://us.archive.ubuntu.com trusty-updates/main Sources [160 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/restricted Sources [2,061 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/universe Sources [99.4 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [4,502 B]
Get:19 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [411 kB]
Get:20 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [8,875 B]
Get:21 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [243 kB]
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.1 kB]
Get:23 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [401 kB]
Get:24 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [8,846 B]
Get:25 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [243 kB]
Get:26 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [11.3 kB]
Get:27 http://us.archive.ubuntu.com trusty-updates/main Translation-en [196 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1,997 kB in 12s (165 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.5~rc2) but it is not installed
E: Unmet dependencies. Try using -f.
angelo@angelo-Satellite-S55t-B:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cm-super cm-super-minimal collada-dom-dev collada-dom2.4-dp-base
  collada-dom2.4-dp-dev context context-modules fltk1.3-doc fluid fonts-cabin
  fonts-comfortaa fonts-font-awesome fonts-freefont-otf fonts-gfs-artemisia
  fonts-gfs-baskerville fonts-gfs-bodoni-classic fonts-gfs-complutum
  fonts-gfs-didot fonts-gfs-didot-classic fonts-gfs-gazis
  fonts-gfs-neohellenic fonts-gfs-olga fonts-gfs-porson fonts-gfs-solomos
  fonts-gfs-theokritos fonts-hosny-amiri fonts-inconsolata fonts-junicode
  fonts-lato fonts-lobster fonts-lobstertwo fonts-oflb-asana-math
  fonts-sil-gentium fonts-sil-gentium-basic fonts-texgyre hddtemp
  ko.tex-extra-hlfont latex-cjk-all latex-cjk-chinese
  latex-cjk-chinese-arphic-bkai00mp latex-cjk-chinese-arphic-bsmi00lp
  latex-cjk-chinese-arphic-gbsn00lp latex-cjk-chinese-arphic-gkai00mp
  latex-cjk-common latex-cjk-japanese latex-cjk-japanese-wadalab
  latex-cjk-korean latex-cjk-thai latex-sanskrit lcdf-typetools libassimp-dev
  libassimp3 libcf0 libeigen3-dev libflann-dev libflann1.8 libfltk-forms1.3
  libfltk-images1.3 libfltk1.1 libfltk1.1-dev libgl2ps-dev libgnomecanvas2-0
  libgnomecanvas2-common liblodo3.0 libnetcdf-dev libnetcdfc++4 libnetcdfc7
  libnetcdff5 libodbc1 libopencv-dev libopencv-gpu-dev libopencv-gpu2.4
  libopencv-photo-dev libopencv-photo2.4 libopencv-stitching-dev
  libopencv-stitching2.4 libopencv-superres-dev libopencv-superres2.4
  libopencv-ts-dev libopencv-ts2.4 libopencv-videostab-dev
  libopencv-videostab2.4 libopencv2.4-java libopencv2.4-jni libopenni-dev
  libopenni-sensor-pointclouds0 libopenni0 libpcl-1.7-all libpcl-1.7-all-dev
  libpcl-1.7-bin libpcl-1.7-doc libpcl-apps-1.7 libpcl-apps-1.7-dev
  libpcl-common-1.7 libpcl-common-1.7-dev libpcl-features-1.7
  libpcl-features-1.7-dev libpcl-filters-1.7 libpcl-filters-1.7-dev
  libpcl-geometry-1.7-dev libpcl-io-1.7 libpcl-io-1.7-dev libpcl-kdtree-1.7
  libpcl-kdtree-1.7-dev libpcl-keypoints-1.7 libpcl-keypoints-1.7-dev
  libpcl-octree-1.7 libpcl-octree-1.7-dev libpcl-outofcore-1.7
  libpcl-outofcore-1.7-dev libpcl-people-1.7 libpcl-people-1.7-dev
  libpcl-recognition-1.7 libpcl-recognition-1.7-dev libpcl-registration-1.7
  libpcl-registration-1.7-dev libpcl-sample-consensus-1.7
  libpcl-sample-consensus-1.7-dev libpcl-search-1.7 libpcl-search-1.7-dev
  libpcl-segmentation-1.7 libpcl-segmentation-1.7-dev libpcl-surface-1.7
  libpcl-surface-1.7-dev libpcl-tracking-1.7 libpcl-tracking-1.7-dev
  libpcl-visualization-1.7 libpcl-visualization-1.7-dev libphonon4 libpmap3.0
  libpoco-dev libpococrypto9 libpocodata9 libpocofoundation9 libpocomysql9
  libpoconet9 libpoconetssl9 libpocoodbc9 libpocosqlite9 libpocoutil9
  libpocoxml9 libpocozip9 libpyside-dev libpyside-py3-1.2 libpyside1.2
  libqhull-dev libqwt-dev libqwt5-qt4 libqwt6 libshiboken-dev
  libshiboken-py3-1.2 libshiboken1.2 libsimbody3.4 liburdfdom-dev
  liburdfdom-headers-dev liburdfdom-model-state0.2 liburdfdom-model0.2
  liburdfdom-sensor0.2 liburdfdom-world0.2 libvtk-java libvtk5-dev
  libvtk5-qt4-dev libvtk5.8 libvtk5.8-qt4 libxss-dev libyaml-cpp-dev
  libyaml-cpp0.5 linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-image-3.13.0-37-generic linux-image-extra-3.13.0-37-generic
  linux-signed-image-3.13.0-37-generic m-tx musixtex opencv-data openni-utils
  pfb2t1c2pfb phonon phonon-backend-gstreamer phonon-backend-gstreamer-common
  phonon-backend-gstreamer1.0 pmx python-matplotlib python-matplotlib-data
  python-opencv python-opengl python-psutil python-pydot python-pyparsing
  python-pyside python-pyside.phonon python-pyside.qtcore
  python-pyside.qtdeclarative python-pyside.qtgui python-pyside.qthelp
  python-pyside.qtnetwork python-pyside.qtopengl python-pyside.qtscript
  python-pyside.qtsql python-pyside.qtsvg python-pyside.qttest
  python-pyside.qtuitools python-pyside.qtwebkit python-pyside.qtxml
  python-qt4-dev python-qt4-gl python-qwt5-qt4 python-sip-dev python-support
  python-tz python-vtk robot-player ros-indigo-actionlib-tutorials
  ros-indigo-angles ros-indigo-bond ros-indigo-bond-core ros-indigo-bondcpp
  ros-indigo-bondpy ros-indigo-camera-calibration
  ros-indigo-camera-calibration-parsers ros-indigo-camera-info-manager
  ros-indigo-class-loader ros-indigo-cmake-modules ros-indigo-collada-parser
  ros-indigo-collada-urdf ros-indigo-common-msgs ros-indigo-common-tutorials
  ros-indigo-compressed-depth-image-transport
  ros-indigo-compressed-image-transport ros-indigo-control-msgs
  ros-indigo-cv-bridge ros-indigo-depth-image-proc ros-indigo-desktop
  ros-indigo-diagnostic-aggregator ros-indigo-diagnostic-analysis
  ros-indigo-diagnostic-common-diagnostics ros-indigo-diagnostic-updater
  ros-indigo-diagnostics ros-indigo-driver-base ros-indigo-dynamic-reconfigure
  ros-indigo-eigen-conversions ros-indigo-eigen-stl-containers
  ros-indigo-executive-smach ros-indigo-filters ros-indigo-gazebo-msgs
  ros-indigo-geometric-shapes ros-indigo-geometry
  ros-indigo-geometry-tutorials ros-indigo-image-common
  ros-indigo-image-geometry ros-indigo-image-pipeline ros-indigo-image-proc
  ros-indigo-image-rotate ros-indigo-image-transport
  ros-indigo-image-transport-plugins ros-indigo-image-view
  ros-indigo-interactive-marker-tutorials ros-indigo-interactive-markers
  ros-indigo-joint-state-publisher ros-indigo-kdl-conversions
  ros-indigo-kdl-parser ros-indigo-laser-assembler ros-indigo-laser-filters
  ros-indigo-laser-geometry ros-indigo-laser-pipeline
  ros-indigo-librviz-tutorial ros-indigo-map-msgs ros-indigo-media-export
  ros-indigo-mk ros-indigo-nav-msgs ros-indigo-nodelet ros-indigo-nodelet-core
  ros-indigo-nodelet-topic-tools ros-indigo-nodelet-tutorial-math
  ros-indigo-octomap ros-indigo-orocos-kdl ros-indigo-pcl-conversions
  ros-indigo-pcl-msgs ros-indigo-pcl-ros ros-indigo-perception
  ros-indigo-perception-pcl ros-indigo-pluginlib
  ros-indigo-pluginlib-tutorials ros-indigo-polled-camera
  ros-indigo-python-orocos-kdl ros-indigo-python-qt-binding
  ros-indigo-qt-dotgraph ros-indigo-qt-gui ros-indigo-qt-gui-cpp
  ros-indigo-qt-gui-py-common ros-indigo-random-numbers
  ros-indigo-resource-retriever ros-indigo-robot ros-indigo-robot-model
  ros-indigo-robot-state-publisher ros-indigo-ros ros-indigo-ros-base
  ros-indigo-ros-comm ros-indigo-ros-core ros-indigo-rosbag-migration-rule
  ros-indigo-rosbash ros-indigo-rosboost-cfg ros-indigo-rosconsole-bridge
  ros-indigo-roscpp-core ros-indigo-roscreate ros-indigo-roslang
  ros-indigo-roslint ros-indigo-roslisp ros-indigo-rosmake
  ros-indigo-rqt-action ros-indigo-rqt-bag ros-indigo-rqt-bag-plugins
  ros-indigo-rqt-common-plugins ros-indigo-rqt-console ros-indigo-rqt-dep
  ros-indigo-rqt-graph ros-indigo-rqt-gui ros-indigo-rqt-gui-cpp
  ros-indigo-rqt-gui-py ros-indigo-rqt-image-view ros-indigo-rqt-launch
  ros-indigo-rqt-logger-level ros-indigo-rqt-moveit ros-indigo-rqt-msg
  ros-indigo-rqt-nav-view ros-indigo-rqt-plot ros-indigo-rqt-pose-view
  ros-indigo-rqt-publisher ros-indigo-rqt-py-common ros-indigo-rqt-py-console
  ros-indigo-rqt-reconfigure ros-indigo-rqt-robot-dashboard
  ros-indigo-rqt-robot-monitor ros-indigo-rqt-robot-plugins
  ros-indigo-rqt-robot-steering ros-indigo-rqt-runtime-monitor
  ros-indigo-rqt-rviz ros-indigo-rqt-service-caller ros-indigo-rqt-shell
  ros-indigo-rqt-srv ros-indigo-rqt-tf-tree ros-indigo-rqt-top
  ros-indigo-rqt-topic ros-indigo-rqt-web ros-indigo-rviz
  ros-indigo-rviz-plugin-tutorials ros-indigo-rviz-python-tutorial
  ros-indigo-self-test ros-indigo-shape-msgs ros-indigo-shape-tools
  ros-indigo-smach ros-indigo-smach-msgs ros-indigo-smach-ros
  ros-indigo-smclib ros-indigo-stage ros-indigo-stage-ros
  ros-indigo-stereo-image-proc ros-indigo-stereo-msgs
  ros-indigo-tf-conversions ros-indigo-tf2-geometry-msgs
  ros-indigo-theora-image-transport ros-indigo-trajectory-msgs
  ros-indigo-turtle-actionlib ros-indigo-turtle-tf ros-indigo-urdf
  ros-indigo-urdf-parser-plugin ros-indigo-urdf-tutorial
  ros-indigo-vision-opencv ros-indigo-visualization-marker-tutorials
  ros-indigo-visualization-msgs ros-indigo-visualization-tutorials
  ros-indigo-viz ros-indigo-xacro sbcl shiboken sip-dev swath tango-icon-theme
  tcl-vtk tcl8.6-dev tex-gyre tex4ht tex4ht-common texlive-bibtex-extra
  texlive-fonts-extra texlive-fonts-extra-doc texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-formats-extra texlive-games
  texlive-generic-extra texlive-humanities texlive-humanities-doc
  texlive-lang-african texlive-lang-arabic texlive-lang-cjk
  texlive-lang-cyrillic texlive-lang-czechslovak texlive-lang-european
  texlive-lang-german texlive-lang-greek texlive-lang-indic
  texlive-lang-italian texlive-lang-other texlive-lang-polish
  texlive-lang-portuguese texlive-lang-spanish texlive-math-extra
  texlive-music texlive-omega texlive-plain-extra texlive-science
  texlive-science-doc texlive-xetex tipa tk8.6-dev ttf-adf-accanthis
  ttf-adf-gillius x11proto-scrnsaver-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common libreoffice-core libreoffice-gnome libreoffice-gtk
  libreoffice-style-galaxy libreoffice-style-human python3-uno uno-libs3 ure
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
  libreoffice-evolution crystalcursors kde-icons-crystal
The following NEW packages will be installed:
  libreoffice-common
The following packages will be upgraded:
  libreoffice-core libreoffice-gnome libreoffice-gtk libreoffice-style-galaxy
  libreoffice-style-human python3-uno uno-libs3 ure
8 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
10 not fully installed or removed.
Need to get 59.8 MB of archives.
After this operation, 78.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main uno-libs3 amd64 4.4.0~rc3-0ubuntu1~trusty1 [784 kB]
Get:2 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main ure amd64 4.4.0~rc3-0ubuntu1~trusty1 [1,825 kB]
Get:3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-gnome amd64 1:4.4.0~rc3-0ubuntu1~trusty1 [148 kB]
Get:4 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main python3-uno amd64 1:4.4.0~rc3-0ubuntu1~trusty1 [178 kB]
Get:5 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-gtk amd64 1:4.4.0~rc3-0ubuntu1~trusty1 [279 kB]
Get:6 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-core amd64 1:4.4.0~rc3-0ubuntu1~trusty1 [33.2 MB]
Get:7 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-style-galaxy all 1:4.4.0~rc3-0ubuntu1~trusty1 [1,466 kB]
Get:8 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-style-human all 1:4.4.0~rc3-0ubuntu1~trusty1 [1,534 kB]
Get:9 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-common all 1:4.4.0~rc3-0ubuntu1~trusty1 [20.4 MB]
Fetched 59.8 MB in 4min 12s (237 kB/s)                                         
(Reading database ... 434029 files and directories currently installed.)
Preparing to unpack .../uno-libs3_4.4.0~rc3-0ubuntu1~trusty1_amd64.deb ...
Unpacking uno-libs3 (4.4.0~rc3-0ubuntu1~trusty1) over (4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../ure_4.4.0~rc3-0ubuntu1~trusty1_amd64.deb ...
Unpacking ure (4.4.0~rc3-0ubuntu1~trusty1) over (4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../libreoffice-gnome_1%3a4.4.0~rc3-0ubuntu1~trusty1_amd64.deb ...
Unpacking libreoffice-gnome (1:4.4.0~rc3-0ubuntu1~trusty1) over (1:4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../python3-uno_1%3a4.4.0~rc3-0ubuntu1~trusty1_amd64.deb ...
Unpacking python3-uno (1:4.4.0~rc3-0ubuntu1~trusty1) over (1:4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../libreoffice-gtk_1%3a4.4.0~rc3-0ubuntu1~trusty1_amd64.deb ...
Unpacking libreoffice-gtk (1:4.4.0~rc3-0ubuntu1~trusty1) over (1:4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../libreoffice-core_1%3a4.4.0~rc3-0ubuntu1~trusty1_amd64.deb ...
Unpacking libreoffice-core (1:4.4.0~rc3-0ubuntu1~trusty1) over (1:4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../libreoffice-style-galaxy_1%3a4.4.0~rc3-0ubuntu1~trusty1_all.deb ...
Unpacking libreoffice-style-galaxy (1:4.4.0~rc3-0ubuntu1~trusty1) over (1:4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../libreoffice-style-human_1%3a4.4.0~rc3-0ubuntu1~trusty1_all.deb ...
Unpacking libreoffice-style-human (1:4.4.0~rc3-0ubuntu1~trusty1) over (1:4.3.5~rc2-0ubuntu1~trusty1) ...
Preparing to unpack .../libreoffice-common_1%3a4.4.0~rc3-0ubuntu1~trusty1_all.deb ...
Unpacking libreoffice-common (1:4.4.0~rc3-0ubuntu1~trusty1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.4.0~rc3-0ubuntu1~trusty1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9702
rmdir: failed to remove ‘/var/lib/libreoffice/share/prereg/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/share/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/program/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.4.0~rc3-0ubuntu1~trusty1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
angelo@angelo-Satellite-S55t-B:~$ 
```

---

### Post by Elfy on 2015-02-02
You must have added them if you have any - PPA's.

Seems you've got some issues with libreoffice currently.

Paste the content of your sources list 

```
cat /etc/apt/sources.list
```

and the list of PPA's if they're in the right place 

```
ls /etc/apt/sources.list.d/
```

---

### Post by angelo8 on 2015-02-02
Here is sources.list

```
angelo@angelo-Satellite-S55t-B:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
angelo@angelo-Satellite-S55t-B:~$ 

```
and the list of  PPA's

```
angelo@angelo-Satellite-S55t-B:~$ ls /etc/apt/sources.list.d/
atareao-atareao-trusty.list       google-chrome.list
atareao-atareao-trusty.list.save  google-chrome.list.save
dropbox.list                      libreoffice-ppa-trusty.list
dropbox.list.save                 ros-latest.list
gazebo-latest.list                ros-latest.list.save
gazebo-latest.list.save
angelo@angelo-Satellite-S55t-B:~$ 

```

---

### Post by Impavidus on 2015-02-02
Here is the problem:
```

dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.4.0~rc3-0ubuntu1~trusty1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9702 
```
A conflict between libreoffice and openoffice. You can't have both.

---

### Post by angelo8 on 2015-02-02
Ok, but now the problem is that I can't remove open office. 

Whenever I try to remove open office using

```
sudo apt-get remove openoffice
```  I get this error

```
angelo@angelo-Satellite-S55t-B:~$ sudo apt-get remove openoffice
[sudo] password for angelo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.4.0~rc3) but it is not going to be installed
 openoffice-brand-base : Depends: openoffice but it is not going to be installed
 openoffice-brand-calc : Depends: openoffice but it is not going to be installed
 openoffice-brand-draw : Depends: openoffice but it is not going to be installed
 openoffice-brand-en-us : Depends: openoffice but it is not going to be installed
 openoffice-brand-impress : Depends: openoffice but it is not going to be installed
 openoffice-brand-math : Depends: openoffice but it is not going to be installed
 openoffice-brand-writer : Depends: openoffice but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

