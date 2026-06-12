---
title: "trouble installing K3B from the source"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by vasyl4 on 2011-01-16
Hey, I'm having trouble installing K3B(version  k3b-2.0.2, because in synaptic there is older 1.91.version) on Ubuntu 10.04 from the source. 
After downloading the k3b-2.0.2.tar.bz2 and extracting that file i did :

mkdir build
cd build

when i`m trying to do cmake i get this:

vasyl@vasyl-desktop:~/k3b-2.0.2/build$ cmake ..
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/vasyl/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:52 (find_package)


-- Configuring incomplete, errors occurred!
vasyl@vasyl-desktop:~/k3b-2.0.2/build$ 

So what should i do? Please help.

---

