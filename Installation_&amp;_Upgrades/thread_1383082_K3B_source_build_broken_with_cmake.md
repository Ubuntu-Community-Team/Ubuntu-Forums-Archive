---
title: "K3B source build broken with cmake"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by brianpatrick on 2010-01-16
Hi,
Suse 11.2 has K3B installed with ripping working. When you load a dvd, it asks you to play/rip/??? Ubu 9.10 does not. There is a rip dvd button, but it only shows the contents of the dvd and offers a burn button, but no rip button. 

I got the latest stable release, k3b-1.68.0, from Launchpad and even followed the instructions. Cmake could not find "FindKDE4Internal.cmake". I scanned the entire file system and this file does not exist anywhere. 

What am I doing wrong this time? Ubu 9.10/64b workstation. 

Thank you,

    BrianP

brianp@trex:~/download/k3b/k3b-1.68.0/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/brianp/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:45 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!

---

### Post by brianpatrick on 2010-01-16
Hi,
The command line is also doing strange things. I found the device for the dvd on /dev/sr1:
grep BRIAN /etc/mtab
/dev/sr1 /media/BRIAN_HOME_MOVIE udf ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,umask=0077 0 0 << wink--wink >>

Then I used the recommended syntax:
brianp@trex:~$ k3b --videodvdrip  --device /dev/sr1
K3bQProcess::QProcess(0x0)

It pops up a "burn image" dialog with a 'X File not found' error in it. Ripping and burning are completely opposite operations. It has /dev/sr1 in the "image to burn" box. 

Is K3B confused or is it me?

Thank you,

    BrianP

---

