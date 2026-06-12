---
title: "i am trying to install darling software but this is what i am getting.."
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by ubilli on 2013-10-18
ubilli@ubilli-pc:~/Documents/darling-master$ CC=clang CXX=clang++ cmake .
-- No build type selected, default to Debug
-- This is a 64-bit build


-- checking for module 'libudev'


--   package 'libudev' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:266 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:320 (_pkg_check_modules_internal)
  CMakeLists.txt:37 (pkg_check_modules)




-- Building ObjC ABI 2
You have called ADD_LIBRARY for library Carbon without any source files. This typically indicates a problem with your CMakeLists.txt file
You have called ADD_LIBRARY for library AppKit without any source files. This typically indicates a problem with your CMakeLists.txt file
You have called ADD_LIBRARY for library auto without any source files. This typically indicates a problem with your CMakeLists.txt file
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
LIBOBJC2_INCLUDE_DIR
   used as include directory in directory /home/ubilli/Documents/darling-master
   used as include directory in directory /home/ubilli/Documents/darling-master/src/motool
   used as include directory in directory /home/ubilli/Documents/darling-master/src/util
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libmach-o
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libdyld
   used as include directory in directory /home/ubilli/Documents/darling-master/src/dyld
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libSystem
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libltdl
   used as include directory in directory /home/ubilli/Documents/darling-master/src/Cocoa
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libobjcdarwin
   used as include directory in directory /home/ubilli/Documents/darling-master/src/CoreFoundation
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libncurses
   used as include directory in directory /home/ubilli/Documents/darling-master/src/CoreSecurity
   used as include directory in directory /home/ubilli/Documents/darling-master/src/CoreServices
   used as include directory in directory /home/ubilli/Documents/darling-master/src/ExceptionHandling
   used as include directory in directory /home/ubilli/Documents/darling-master/src/IOKit
   used as include directory in directory /home/ubilli/Documents/darling-master/src/Foundation
   used as include directory in directory /home/ubilli/Documents/darling-master/src/Carbon
   used as include directory in directory /home/ubilli/Documents/darling-master/src/CoreVideo
   used as include directory in directory /home/ubilli/Documents/darling-master/src/OpenGL
   used as include directory in directory /home/ubilli/Documents/darling-master/src/thin
   used as include directory in directory /home/ubilli/Documents/darling-master/src/libstdc++darwin


-- Configuring incomplete, errors occurred!
ubilli@ubilli-pc:~/Documents/darling-master$ apt-get install libudev
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubilli@ubilli-pc:~/Documents/darling-master$ sudo apt-get install libudev
[sudo] password for ubilli: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libudev

please whare can i get libudev from..

---

### Post by steeldriver on 2013-10-18
Did you follow [the instructions here]("http://darling.dolezel.info/en/Build/Ubuntu")?

> 
# Libraries
sudo apt-get install libxml2-dev libgnutls-dev libicu-dev libcairo-dev \
                     libjpeg-dev libpng-dev libtiff-dev libbsd-dev [COLOR=#0000ff]**libudev-dev**[/COLOR] \
                     liblcms-dev libkqueue-dev libssl-dev libbz2-dev uuid-dev \
                     libncurses-dev libxrandr-dev libavcodec-dev libavformat-dev


---

### Post by ubilli on 2013-10-21
this is what i get when i did what you said
this is the output....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcairo2-dev' instead of 'libcairo-dev'
Note, selecting 'libpng12-dev' instead of 'libpng-dev'
Note, selecting 'libtiff4-dev' instead of 'libtiff-dev'
Note, selecting 'liblcms1-dev' instead of 'liblcms-dev'
Note, selecting 'libncurses5-dev' instead of 'libncurses-dev'
libbsd-dev is already the newest version.
libncurses5-dev is already the newest version.
libncurses5-dev set to manually installed.
libpng12-dev is already the newest version.
libpng12-dev set to manually installed.
libkqueue-dev is already the newest version.
libssl-dev is already the newest version.
libssl-dev set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libcairo2-dev : Depends: libcairo2 (= 1.10.2-6.1ubuntu2) but 1.10.2-6.1ubuntu3 is to be installed
                 Depends: libcairo-gobject2 (= 1.10.2-6.1ubuntu2) but 1.10.2-6.1ubuntu3 is to be installed
                 Depends: libcairo-script-interpreter2 (= 1.10.2-6.1ubuntu2) but 1.10.2-6.1ubuntu3 is to be installed
                 Depends: libxcb-render0-dev (>= 0.9.92) but it is not going to be installed
                 Depends: libxcb-shm0-dev but it is not going to be installed
 libgnutls-dev : Depends: libgnutls26 (= 2.12.14-5ubuntu3) but 2.12.14-5ubuntu3.2 is to be installed
                 Depends: libgnutlsxx27 (= 2.12.14-5ubuntu3) but it is not going to be installed
                 Depends: libgnutls-openssl27 (= 2.12.14-5ubuntu3) but it is not going to be installed
                 Depends: libgcrypt11-dev (>= 1.4.0) but it is not going to be installed
 libjpeg-dev : Depends: libjpeg8-dev but it is not going to be installed
 libtiff4-dev : Depends: libtiff4 (= 3.9.5-2ubuntu1) but 3.9.5-2ubuntu1.4 is to be installed
 libudev-dev : Depends: libudev0 (= 175-0ubuntu9) but 175-0ubuntu9.4 is to be installed
 libxml2-dev : Depends: libxml2 (= 2.7.8.dfsg-5.1ubuntu4) but 2.7.8.dfsg-5.1ubuntu4.4 is to be installed
 libxrandr-dev : Depends: libxrandr2 (= 2:1.3.2-2) but 2:1.3.2-2ubuntu0.1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by steeldriver on 2013-10-21
what Ubuntu version and architecture are you trying to build this on? it looks like it requires some pretty specific versions of libraries

---

### Post by ubilli on 2013-10-22
ubuntu 12.04 LTS

---

### Post by SeijiSensei on 2013-10-22
> libcairo2-dev : Depends: libcairo2 (= 1.10.2-6.1ubuntu2) but 1.10.2-6.1ubuntu3 is to be installed


Notice the equal signs in that error message?  That means the package requires those specific versions of the libraries.  A well-packaged program should work with future releases as well which are designated with ">=" rather than "=".

Either you are going to have to install those specific libraries, or revert to an earlier version of Ubuntu with those specific library versions.  I'd post a bug report on the developer's site suggesting that the packaging be made less specific.

---

