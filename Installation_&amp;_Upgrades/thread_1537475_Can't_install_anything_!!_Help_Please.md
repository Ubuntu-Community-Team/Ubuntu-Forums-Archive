---
title: "Can't install anything !! Help Please"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by rupelke on 2010-07-23
Hi,
i can't install anything on ubuntu :(
i have ubuntu 10.04 and this is the error. i hope you can help me 

Archives  install () failed: (Reading database ... (Reading database ... 5%  (Reading database ... 10% (Reading database ... 15% (Reading database  ... 20% (Reading database ... 25 %  (Reading database ... 30% (Reading database ... 35% (Reading database  ... 40% (Reading database ... 45% (Reading database ... 50% (Reading  database ... 55% ( Reading  database ... 60% (Reading database ... 65% (Reading database ... 70%  (Reading database ... 75% (Reading database ... 80% (Reading database  ... 85% (Reading database ...  90% (Reading database ... 95% (Reading database ... 100% (Reading  database ... 167081 files and directories currently installed.) 
Arista is removed ... 
gstreamer0.10-plugins-bad is removed ... 
Processing triggers for man-db ... 
Processing triggers for your desktop-file-utils ... 
Processing triggers for python-GMENU ... 
Rebuilding / usr/share/applications/desktop.nl_BE.UTF8.cache ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Triggers for processing python-support ... 
Selecting previously deselected package gstreamer0.10-fluendo-mpegdemux. 
(Reading  database ... (Reading database ... 5% (Reading database ... 10%  (Reading database ... 15% (Reading database ... 20% (Reading database  ... 25% (Reading database. 30%  .. (Reading database ... 35% (Reading database ... 40% (Reading  database ... 45% (Reading database ... 50% (Reading database ... 55%  (Reading database ... 60%  (Reading database ... 65% (Reading database ... 70% (Reading database  ... 75% (Reading database ... 80% (Reading database ... 85% (Reading  database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 166863 files and directories currently installed.) 
Unpacking gstreamer0.10-fluendo-mpegdemux (from .../gstreamer0.10-fluendo-mpegdemux_0.10.15-1_i386.deb) ... 
Setting libavformat52 (4:0.5.1-1ubuntu1) ... 
dpkg (subprocess): installed post-installation script can not execute: Wrong executable 
dpkg: error processing libavformat52 (- configure): 
 subprocess installed post-installation script returned error exit status 2 back 
dpkg: dependency problems prevent configuration of gstreamer0.10-ffmpeg: 
 gstreamer0.10-ffmpeg depends on libavformat52 (> = 4:0.5.1-1) | libavformat-extra-52 (> = 4:0.5.1-1) but: 
  Libavformat52 package is not configured yet. 
  Package "libavformat-extra-52" is not installed. 
dpkg: error processing gstreamer0.10-ffmpeg (- configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gstreamer0.10-ffmpeg-dbg: 
 gstreamer0.10-ffmpeg-dbg depends on gstreamer0.10-ffmpeg (= 0.10.10-1) but: 
  Package gstreamer0.10-ffmpeg is not configured yet. 
dpkg: error processing gstreamer0.10-ffmpeg-dbg (- configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libavdevice52: 
 libavdevice52 depends libavformat52 (> = 4:0.5.1-1ubuntu1) | libavformat-extra-52 (> = 4:0.5.1-1ubuntu1) but: 
  Libavformat52 package is not configured yet. 
  Because MaxReports PakketNo apport report has reached Already Written 
 "Libavformat-extra-52" is not installed. 
 libavdevice52 libavformat52 depends on (<<4:0.5.1-99) | libavformat-extra-52 (<<4:0.5.1-99), but: 
  Libavformat52 package is not configured yet. 
  Package "libavformat-extra-52" is not installed. 
dpkg: error processing libavdevice52 (- configure): 
 dependency problems - leaving unconfigured 
Setting libftgl2 (2.1.3 ~ RC5-3) ... 
dpkg (subprocess): installed post-installation script can not execute: Wrong executable 
dpkg: error processing libftgl2 (- configure): 
 installed subprocess post-installation script returned error exit status 2 back 
No apport report has reached Already Written Because MaxReports 
Setting up gstreamer0.10-fluendo-mpegdemux (0.10.15-1) ... 
Errors were encountered while processing: 
 libavformat52 
 gstreamer0.10-ffmpeg 
 gstreamer0.10-ffmpeg-dbg 
 libavdevice52 
 libftgl2 
Setting libftgl2 (2.1.3 ~ RC5 3) ... 
dpkg (subprocess): installed post-installation script can not execute: Wrong executable 
dpkg: error processing libftgl2 (- configure): 
 installed subprocess post-installation script returned error exit status 2 back 
Setting libavformat52 (4:0.5.1-1ubuntu1) ... 
dpkg (subprocess): installed post-installation script can not execute: Wrong executable 
dpkg: error processing libavformat52 (- configure): 
 installed subprocess post-installation script returned error exit status 2 back 
dpkg: dependency problems prevent configuration of gstreamer0.10-ffmpeg: 
 gstreamer0.10-ffmpeg depends on libavformat52 (> = 4:0.5.1-1) | libavformat-extra-52 (> = 4:0.5.1-1) but: 
  Package libavformat52 is not configured yet. 
  Package "libavformat-extra-52" is not installed. 
dpkg: error processing gstreamer0.10-ffmpeg (- configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libavdevice52: 
 libavdevice52 depends libavformat52 (> = 4:0.5.1-1ubuntu1) | libavformat-extra-52 (> = 4:0.5.1-1ubuntu1) but: 
  Libavformat52 package is not configured yet. 
  Package "libavformat-extra-52" is not installed. 
 libavdevice52 depends libavformat52 (<<4:0.5.1-99) | libavformat-extra-52 (<<4:0.5.1-99), but: 
  Libavformat52 package is not configured yet. 
  Package "libavformat-extra-52" is not installed. 
dpkg: error processing of libavdevice52 (- configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gstreamer0.10-ffmpeg-dbg: 
 gstreamer0.10-ffmpeg-dbg gstreamer0.10-ffmpeg depends on (= 0.10.10-1) but: 
  Package gstreamer0.10-ffmpeg is not configured yet. 
dpkg: error processing gstreamer0.10-ffmpeg-dbg (- configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing:

---

