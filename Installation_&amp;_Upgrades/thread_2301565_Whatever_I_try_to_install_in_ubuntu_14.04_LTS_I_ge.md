---
title: "Whatever I try to install in ubuntu 14.04 LTS I get this error."
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by ali55 on 2015-11-03
```
ali@ali-SVS1511BFXB:~$ sudo apt-get install git
[sudo] password for ali: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 0 B/64,3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package libopenjpeg2:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of libavcodec-extra-54:amd64:
 libavcodec-extra-54:amd64 depends on libopenjpeg2; however:
  Package libopenjpeg2:amd64 is not configured yet.

dpkg: error processing package libavcodec-extra-54:amd64 (--configure):
 dependency problems - leaving unconfiguredNo apport report written because the error message indicates its a followup error from a previous failure.

dpkg: dependency problems prevent configuration of libavformat54:amd64:
 libavformat54:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libavformat54:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-highgui2.4:amd64:
 libopencv-highgui2.4:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.10); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 libopencv-highgui2.4:amd64 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package libopencv-highgui2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-objdetect2.4:amd64:
 libNo apport report written because the error message indicates its a followup error from a previous failure.
                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        opencv-objdetect2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-objdetect2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-contrib2.4:amd64:
 libopencv-contrib2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.
 libopencv-contrib2.4:amd64 depends on libopencv-objdetect2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-objdetect2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-contrib2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-legacy2.4:amd64:
 libopencv-legacy2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configureNo apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               d yet.

dpkg: error processing package libopencv-legacy2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libchromaprint0:amd64:
 libchromaprint0:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.10); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libchromaprint0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 vlc-nox depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.
 vlc-nox depends on libchromaprint0 (>= 0.2); however:
  Package libchromaprint0:amd64 is not configured yet.

dpkg: error processing package vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-plugins-bad:amd64:
 gstreamer1.0-plugins-bad:amd64 depends on libchromaprint0 (>= 0.2); however:
  Package libchromaprint0:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-contrib2.4; however:
  Package libopencv-contrib2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-highgui2.4; however:
  Package libopencv-highgui2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-legacy2.4; however:
  Package libopencv-legacy2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-objdetect2.4; however:
  Package libopencv-objdetect2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopenjpeg2; however:
  Package libopenjpeg2:amd64 is not configured yet.

dpkg: error processing package gstreamer1.0-plugins-bad:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-libav:amd64:
 gstreamer1.0-libav:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.13); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 gstreamer1.0-libav:amd64 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package gstreamer1.0-libav:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdlna0:
 libdlna0 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package libdlna0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ushare:
 ushare depends on libdlna0; however:
  Package libdlna0 is not configured yet.

dpkg: error processing package ushare (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavcodec-extra:
 libavcodec-extra depends on libavcodec-extra-54; however:
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libavcodec-extra (--configure):
 dependency problems - leaving unconfigured
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mörgæs on 2015-11-03
Please boot the computer, run 
```
sudo apt-get update
```
and post the output in CODE tags.

---

### Post by Bucky Ball on 2015-11-03
Welcome. Better still, go all the way:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

One after the other with return in between. Report any and all errors. These commands will not upgrade your installed release to a newer one. And yes, please use code tags (see the last link in my signature, I have added them to your first post), default color and point size. Thanks. :)

---

### Post by ali55 on 2015-11-04
Hi Thanks for responding, i will try to do the following and report the scene and i'll use code tags. Thanks a lot!

---

### Post by ali55 on 2015-11-04
[COLOR=#ff0000][B]1-sudo apt-get update
[/B][/COLOR]
```
Ign http://extras.ubuntu.com trusty InRelease
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:1 http://security.ubuntu.com trusty-security InRelease [64,4 kB]           
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:2 http://security.ubuntu.com trusty-security/main Sources [98,0 kB]        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                    
Ign http://extras.ubuntu.com trusty/main Translation-en                       
Get:3 http://security.ubuntu.com trusty-security/restricted Sources [3.357 B]
Get:4 http://security.ubuntu.com trusty-security/universe Sources [31,0 kB]
Get:5 http://security.ubuntu.com trusty-security/multiverse Sources [2.346 B]
Get:6 http://security.ubuntu.com trusty-security/main amd64 Packages [362 kB]
Get:7 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12,4 kB]
Get:8 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:9 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3.688 B]
Get:10 http://security.ubuntu.com trusty-security/main i386 Packages [342 kB]
Get:11 http://security.ubuntu.com trusty-security/restricted i386 Packages [12,2 kB]
Get:12 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:13 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3.846 B]
Get:14 http://security.ubuntu.com trusty-security/main Translation-en [196 kB]
Get:15 http://security.ubuntu.com trusty-security/multiverse Translation-en [1.679 B]
Get:16 http://security.ubuntu.com trusty-security/restricted Translation-en [3.076 B]
Get:17 http://security.ubuntu.com trusty-security/universe Translation-en [68,4 kB]
Ign http://de.archive.ubuntu.com trusty InRelease                              
Hit http://de.archive.ubuntu.com trusty-updates InRelease
Get:18 http://de.archive.ubuntu.com trusty-backports InRelease [64,5 kB]
Hit http://de.archive.ubuntu.com trusty Release.gpg                            
Hit http://de.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://de.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://de.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://de.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://de.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://de.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://de.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://de.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://de.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://de.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://de.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:19 http://de.archive.ubuntu.com trusty-backports/main Sources [7.547 B]    
Get:20 http://de.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:21 http://de.archive.ubuntu.com trusty-backports/universe Sources [32,1 kB]
Get:22 http://de.archive.ubuntu.com trusty-backports/multiverse Sources [1.898 B]
Get:23 http://de.archive.ubuntu.com trusty-backports/main amd64 Packages [8.999 B]
Get:24 http://de.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:25 http://de.archive.ubuntu.com trusty-backports/universe amd64 Packages [38,3 kB]
Get:26 http://de.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1.571 B]
Get:27 http://de.archive.ubuntu.com trusty-backports/main i386 Packages [9.017 B]
Get:28 http://de.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:29 http://de.archive.ubuntu.com trusty-backports/universe i386 Packages [38,3 kB]
Get:30 http://de.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1.552 B]
Get:31 http://de.archive.ubuntu.com trusty-backports/main Translation-en [5.013 B]
Get:32 http://de.archive.ubuntu.com trusty-backports/multiverse Translation-en [1.215 B]
Get:33 http://de.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:34 http://de.archive.ubuntu.com trusty-backports/universe Translation-en [33,7 kB]
Hit http://de.archive.ubuntu.com trusty Release                                
Hit http://de.archive.ubuntu.com trusty/main Sources                           
Hit http://de.archive.ubuntu.com trusty/restricted Sources                     
Hit http://de.archive.ubuntu.com trusty/universe Sources                       
Hit http://de.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://de.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://de.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://de.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://de.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://de.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://de.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://de.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://de.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://de.archive.ubuntu.com trusty/main Translation-en                    
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://de.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://de.archive.ubuntu.com trusty/universe Translation-en                
Ign http://de.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://de.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://de.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://de.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1.682 kB in 34s (48,5 kB/s)                                            
Reading package lists... Done

```
[B][COLOR=#ff0000]
2- sudo apt-get upgrade[/COLOR][/B]

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-generic-lts-vivid linux-headers-generic
  linux-headers-generic-lts-vivid linux-image-generic
  linux-image-generic-lts-vivid linux-image-server linux-server
The following packages will be upgraded:
  linux-libc-dev pycharm
2 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
17 not fully installed or removed.
Need to get 184 MB/184 MB of archives.
After this operation, 36,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/mystic-mirage/pycharm/ubuntu/ trusty/main pycharm all 5.0~mm1 [183 MB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-libc-dev amd64 3.13.0-67.110 [769 kB]
Fetched 184 MB in 2min 14s (1.366 kB/s)                                        
(Reading database ... 232037 files and directories currently installed.)
Preparing to unpack .../linux-libc-dev_3.13.0-67.110_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-67.110) over (3.13.0-66.108) ...
Preparing to unpack .../pycharm_5.0~mm1_all.deb ...
Unpacking pycharm (5.0~mm1) over (4.5.4~mm1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
dpkg: error processing package libopenjpeg2:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of libavcodec-extra-54:amd64:
 libavcodec-extra-54:amd64 depends on libopenjpeg2; however:
  Package libopenjpeg2:amd64 is not configured yet.

dpkg: error processing package libavcodec-extra-54:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavformat54:amd64:
 libavformat54:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libavformat54:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-highgui2.4:amd64:
 libopencv-highgui2.4:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.10); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 libopencv-highgui2.4:amd64 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package libNo apport report written because the error message indicates its a followup error from a previous failure.
                                                            No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  opencv-highgui2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-objdetect2.4:amd64:
 libopencv-objdetect2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-objdetect2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-contrib2.4:amd64:
 libopencv-contrib2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.
 libopencv-contrib2.4:amd64 depends on libopencv-objdetect2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-objdetect2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-contrib2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopNo apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                encv-legacy2.4:amd64:
 libopencv-legacy2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-legacy2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libchromaprint0:amd64:
 libchromaprint0:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.10); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libchromaprint0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 vlc-nox depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.
 vlc-nox depends on libchromaprint0 (>= 0.2); however:
  Package libchromaprint0:amd64 is not configured yet.

dpkg: error processing package vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-plugins-bad:amd64:
 gstreamer1.0-plugins-bad:amd64 depends on libchromaprint0 (>= 0.2); however:
  Package libchromaprint0:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-contrib2.4; however:
  Package libopencv-contrib2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-highgui2.4; however:
  Package libopencv-highgui2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-legacy2.4; however:
  Package libopencv-legacy2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-objdetect2.4; however:
  Package libopencv-objdetect2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopenjpeg2; however:
  Package libopenjpeg2:amd64 is not configured yet.

dpkg: error processing package gstreamer1.0-plugins-bad:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-libav:amd64:
 gstreamer1.0-libav:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.13); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 gstreamer1.0-libav:amd64 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package gstreamer1.0-libav:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdlna0:
 libdlna0 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package libdlna0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ushare:
 ushare depends on libdlna0; however:
  Package libdlna0 is not configured yet.

dpkg: error processing package ushare (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavcodec-extra:
 libavcodec-extra depends on libavcodec-extra-54; however:
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libavcodec-extra (--configure):
 dependency problems - leaving unconfigured
Setting up linux-libc-dev:amd64 (3.13.0-67.110) ...
Setting up pycharm (5.0~mm1) ...
Errors were encountered while processing:
 libopenjpeg2:amd64
 libavcodec-extra-54:amd64
 libavformat54:amd64
 libopencv-highgui2.4:amd64
 libopencv-objdetect2.4:amd64
 libopencv-contrib2.4:amd64
 libopencv-legacy2.4:amd64
 libchromaprint0:amd64
 vlc-nox
 vlc-plugin-notify
 vlc
 vlc-plugin-pulse
 gstreamer1.0-plugins-bad:amd64
 gstreamer1.0-libav:amd64
 libdlna0
 ushare
 libavcodec-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**[COLOR=#ff0000]3- sudo apt-get dist-upgrade[/COLOR]**

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-image-3.13.0-66-generic linux-image-extra-3.13.0-66-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.13.0-67 linux-headers-3.13.0-67-generic
  linux-headers-3.19.0-32 linux-headers-3.19.0-32-generic
  linux-image-3.13.0-67-generic linux-image-3.19.0-32-generic
  linux-image-extra-3.13.0-67-generic linux-image-extra-3.19.0-32-generic
The following packages will be upgraded:
  linux-generic linux-generic-lts-vivid linux-headers-generic
  linux-headers-generic-lts-vivid linux-image-generic
  linux-image-generic-lts-vivid linux-image-server linux-server
8 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 127 MB/127 MB of archives.
After this operation, 559 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-3.13.0-67-generic amd64 3.13.0-67.110 [15,2 MB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-3.19.0-32-generic amd64 3.19.0-32.37~14.04.1 [16,7 MB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-server amd64 3.13.0.67.73 [1.750 B]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-server amd64 3.13.0.67.73 [1.750 B]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-extra-3.13.0-67-generic amd64 3.13.0-67.110 [36,7 MB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-generic amd64 3.13.0.67.73 [1.780 B]
Get:7 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-generic amd64 3.13.0.67.73 [2.386 B]
Get:8 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.13.0-67 all 3.13.0-67.110 [8.882 kB]
Get:9 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.13.0-67-generic amd64 3.13.0-67.110 [698 kB]
Get:10 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-generic amd64 3.13.0.67.73 [2.374 B]
Get:11 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-extra-3.19.0-32-generic amd64 3.19.0-32.37~14.04.1 [38,3 MB]
Get:12 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-generic-lts-vivid amd64 3.19.0.32.19 [1.792 B]
Get:13 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-generic-lts-vivid amd64 3.19.0.32.19 [2.268 B]
Get:14 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.19.0-32 all 3.19.0-32.37~14.04.1 [9.296 kB]
Get:15 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.19.0-32-generic amd64 3.19.0-32.37~14.04.1 [746 kB]
Get:16 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-generic-lts-vivid amd64 3.19.0.32.19 [2.246 B]
Fetched 127 MB in 2min 22s (890 kB/s)                                          
Selecting previously unselected package linux-image-3.13.0-67-generic.
(Reading database ... 232151 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-67-generic (3.13.0-67.110) ...
Selecting previously unselected package linux-image-3.19.0-32-generic.
Preparing to unpack .../linux-image-3.19.0-32-generic_3.19.0-32.37~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Preparing to unpack .../linux-server_3.13.0.67.73_amd64.deb ...
Unpacking linux-server (3.13.0.67.73) over (3.13.0.66.72) ...
Preparing to unpack .../linux-image-server_3.13.0.67.73_amd64.deb ...
Unpacking linux-image-server (3.13.0.67.73) over (3.13.0.66.72) ...
Selecting previously unselected package linux-image-extra-3.13.0-67-generic.
Preparing to unpack .../linux-image-extra-3.13.0-67-generic_3.13.0-67.110_amd64.deb ...
Unpacking linux-image-extra-3.13.0-67-generic (3.13.0-67.110) ...
Preparing to unpack .../linux-generic_3.13.0.67.73_amd64.deb ...
Unpacking linux-generic (3.13.0.67.73) over (3.13.0.66.72) ...
Preparing to unpack .../linux-image-generic_3.13.0.67.73_amd64.deb ...
Unpacking linux-image-generic (3.13.0.67.73) over (3.13.0.66.72) ...
Selecting previously unselected package linux-headers-3.13.0-67.
Preparing to unpack .../linux-headers-3.13.0-67_3.13.0-67.110_all.deb ...
Unpacking linux-headers-3.13.0-67 (3.13.0-67.110) ...
Selecting previously unselected package linux-headers-3.13.0-67-generic.
Preparing to unpack .../linux-headers-3.13.0-67-generic_3.13.0-67.110_amd64.deb ...
Unpacking linux-headers-3.13.0-67-generic (3.13.0-67.110) ...
Preparing to unpack .../linux-headers-generic_3.13.0.67.73_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.67.73) over (3.13.0.66.72) ...
Selecting previously unselected package linux-image-extra-3.19.0-32-generic.
Preparing to unpack .../linux-image-extra-3.19.0-32-generic_3.19.0-32.37~14.04.1_amd64.deb ...
Unpacking linux-image-extra-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Preparing to unpack .../linux-generic-lts-vivid_3.19.0.32.19_amd64.deb ...
Unpacking linux-generic-lts-vivid (3.19.0.32.19) over (3.19.0.31.18) ...
Preparing to unpack .../linux-image-generic-lts-vivid_3.19.0.32.19_amd64.deb ...
Unpacking linux-image-generic-lts-vivid (3.19.0.32.19) over (3.19.0.31.18) ...
Selecting previously unselected package linux-headers-3.19.0-32.
Preparing to unpack .../linux-headers-3.19.0-32_3.19.0-32.37~14.04.1_all.deb ...
Unpacking linux-headers-3.19.0-32 (3.19.0-32.37~14.04.1) ...
Selecting previously unselected package linux-headers-3.19.0-32-generic.
Preparing to unpack .../linux-headers-3.19.0-32-generic_3.19.0-32.37~14.04.1_amd64.deb ...
Unpacking linux-headers-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Preparing to unpack .../linux-headers-generic-lts-vivid_3.19.0.32.19_amd64.deb ...
Unpacking linux-headers-generic-lts-vivid (3.19.0.32.19) over (3.19.0.31.18) ...
dpkg: error processing package libopenjpeg2:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of libavcodec-extra-54:amd64:
 libavcodec-extra-54:amd64 depends on libopenjpeg2; however:
  Package libopenjpeg2:amd64 is not configured yet.

dpkg: error processing package libavcodec-extra-54:amd64 (--configure):No apport report written because the error message indicates its a followup error from a previous failure.

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavformat54:amd64:
 libavformat54:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libavformat54:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-highgui2.4:amd64:
 libopencv-highgui2.4:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.10); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 libopencv-highgui2.4:amd64 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package libopencv-highgui2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             ration of libopencv-objdetect2.4:amd64:
 libopencv-objdetect2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-objdetect2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-contrib2.4:amd64:
 libopencv-contrib2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-highgui2.4:amd64 is not configured yet.
 libopencv-contrib2.4:amd64 depends on libopencv-objdetect2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  Package libopencv-objdetect2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-contrib2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-legacy2.4:amd64:
 libopencv-legacy2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however:
  PackagNo apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  e libopencv-highgui2.4:amd64 is not configured yet.

dpkg: error processing package libopencv-legacy2.4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libchromaprint0:amd64:
 libchromaprint0:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.10); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libchromaprint0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.18); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 vlc-nox depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.
 vlc-nox depends on libchromaprint0 (>= 0.2); however:
  Package libchromaprint0:amd64 is not configured yet.

dpkg: error processing package vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.1.6-0ubuntu14.04.1); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-plugins-bad:amd64:
 gstreamer1.0-plugins-bad:amd64 depends on libchromaprint0 (>= 0.2); however:
  Package libchromaprint0:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-contrib2.4; however:
  Package libopencv-contrib2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-highgui2.4; however:
  Package libopencv-highgui2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-legacy2.4; however:
  Package libopencv-legacy2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-objdetect2.4; however:
  Package libopencv-objdetect2.4:amd64 is not configured yet.
 gstreamer1.0-plugins-bad:amd64 depends on libopenjpeg2; however:
  Package libopenjpeg2:amd64 is not configured yet.

dpkg: error processing package gstreamer1.0-plugins-bad:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer1.0-libav:amd64:
 gstreamer1.0-libav:amd64 depends on libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.13); however:
  Package libavcodec54 is not installed.
  Package libavcodec-extra-54:amd64 is not configured yet.
 gstreamer1.0-libav:amd64 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package gstreamer1.0-libav:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdlna0:
 libdlna0 depends on libavformat54 (>= 6:9.1-1); however:
  Package libavformat54:amd64 is not configured yet.

dpkg: error processing package libdlna0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ushare:
 ushare depends on libdlna0; however:
  Package libdlna0 is not configured yet.

dpkg: error processing package ushare (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavcodec-extra:
 libavcodec-extra depends on libavcodec-extra-54; however:
  Package libavcodec-extra-54:amd64 is not configured yet.

dpkg: error processing package libavcodec-extra (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-67-generic (3.13.0-67.110) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-3.19.0-32-generic
Found kernel: /boot/vmlinuz-3.19.0-31-generic
Found kernel: /boot/vmlinuz-3.19.0-30-generic
Found kernel: /boot/vmlinuz-3.13.0-67-generic
Found kernel: /boot/vmlinuz-3.13.0-66-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.19.0-32-generic
Found kernel: /boot/vmlinuz-3.19.0-31-generic
Found kernel: /boot/vmlinuz-3.19.0-30-generic
Found kernel: /boot/vmlinuz-3.13.0-67-generic
Found kernel: /boot/vmlinuz-3.13.0-66-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Setting up linux-image-extra-3.13.0-67-generic (3.13.0-67.110) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.19.0-32-generic
Found kernel: /boot/vmlinuz-3.19.0-31-generic
Found kernel: /boot/vmlinuz-3.19.0-30-generic
Found kernel: /boot/vmlinuz-3.13.0-67-generic
Found kernel: /boot/vmlinuz-3.13.0-66-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-generic (3.13.0.67.73) ...
Setting up linux-headers-3.13.0-67 (3.13.0-67.110) ...
Setting up linux-headers-3.13.0-67-generic (3.13.0-67.110) ...
Setting up linux-headers-generic (3.13.0.67.73) ...
Setting up linux-generic (3.13.0.67.73) ...
Setting up linux-server (3.13.0.67.73) ...
Setting up linux-image-server (3.13.0.67.73) ...
Setting up linux-image-extra-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.19.0-32-generic
Found kernel: /boot/vmlinuz-3.19.0-31-generic
Found kernel: /boot/vmlinuz-3.19.0-30-generic
Found kernel: /boot/vmlinuz-3.13.0-67-generic
Found kernel: /boot/vmlinuz-3.13.0-66-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-generic-lts-vivid (3.19.0.32.19) ...
Setting up linux-headers-3.19.0-32 (3.19.0-32.37~14.04.1) ...
Setting up linux-headers-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Setting up linux-headers-generic-lts-vivid (3.19.0.32.19) ...
Setting up linux-generic-lts-vivid (3.19.0.32.19) ...
Errors were encountered while processing:
 libopenjpeg2:amd64
 libavcodec-extra-54:amd64
 libavformat54:amd64
 libopencv-highgui2.4:amd64
 libopencv-objdetect2.4:amd64
 libopencv-contrib2.4:amd64
 libopencv-legacy2.4:amd64
 libchromaprint0:amd64
 vlc-nox
 vlc-plugin-notify
 vlc
 vlc-plugin-pulse
 gstreamer1.0-plugins-bad:amd64
 gstreamer1.0-libav:amd64
 libdlna0
 ushare
 libavcodec-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QIII on 2015-11-04
What happens if you disable -backports?

---

### Post by ali55 on 2015-11-05
I don't know why it seems this problem is so persistent, I posted it elsewhere as well, but none of the suggested solution helped that i'm even thinking to remove the whole OS and install other distro, I am developing a small web application and this is preventing me from installing lot's of tools under the hood...

---

### Post by tgalati4 on 2015-11-05
You might need a clean install.  You have a mixture of kernel 3.13 and 3.19 packages which is confusing as to why you have this situation.  The base 14.04 runs kernel 3.13, but newer kernels can be installed.  What kernel are you currently running?

```
uname -a
```

---

### Post by Bucky Ball on 2015-11-05
> **tgalati4 said:**
> You might need a clean install.  You have a mixture of kernel 3.13 and 3.19 packages which is confusing as to why you have this situation.  The base 14.04 runs kernel 3.13, but newer kernels can be installed.  What kernel are you currently running?

```
uname -a
```

... or perhaps we could have a look at the sources.list file and kill some offenders, if there.

Please post the output of this command along with that of tgalati4's:

```
nano /etc/apt/sources.list
```

Make sure you get the whole thing and nothing is down the page. :)

---

### Post by ali55 on 2015-11-05
Thanks tgalati4 and Bucky Ball here is the output of 
[COLOR=#ff0000][B]
nano /etc/apt/sources.list[/B][/COLOR]


```
[COLOR=#000000]# deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

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

^G Get Help                       ^O WriteOut                       ^R Read File                      ^Y Prev Page                      ^K Cut Text                       ^C Cur Pos
^X Exit                           ^J Justify                        ^W Where Is                       ^V Next Page                      ^U UnCut Text                     ^T To Spell
[/COLOR]
```

---

### Post by Bucky Ball on 2015-11-05
Thanks, but there is more down the output I think. Could you provide that, too? Thanks.

Try QIII's suggestion of disabling the backports, then update and see how you go. 

To do that, open that file again, this time with:

```
sudo nano /etc/apt/sources.list
```

The fifth section in your output looks like this:

```
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
```

Disable those last two repos by adding a # at the beginning of the line:

```
# deb http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
```

Then:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

