---
title: "blender installation"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by cbalasubramanian on 2011-12-13
Friends,
I am using ubuntu 11.04, While i try to install Blender 3D animation software through ubuntu software center, it throws me the following error.

Failed to fetch [http://it.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.12.854-2_i386.deb](http://it.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.12.854-2_i386.deb) 

Failed to fetch [http://it.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_i386.deb](http://it.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_i386.deb) 403  Forbidden [IP: 193.206.139.45 80]


Some one pls help me to resolve the problem,

Cheers,
Bala

---

### Post by thatguruguy on 2011-12-13
Interesting.

You can try the following, although I no longer use 11.04, and I've had no problems installing Blender.

Open a terminal and type the following:
```
sudo apt-get libopenal1
```
After that's done, try to install Blender again.  You may also want to get the latest build of Blender straight from the [Blender site]("http://www.blender.org/download/get-blender/"), because the one in the Ubuntu repository is somewhat out of date.

---

