---
title: "libgl1-mesa-glx-lts-quantal conflicts with libgl1"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by Aung_Thiha on 2014-02-11
I'm trying to install deb downloaded from [http://packages.ubuntu.com/precise/amd64/libgl1-mesa-glx-lts-quantal/download](http://packages.ubuntu.com/precise/amd64/libgl1-mesa-glx-lts-quantal/download) to Initialize a build environment for android.
Can't Install it. Please help!



```
aungthiha@aungthiha:~/Desktop$ sudo dpkg -i libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise3_amd64.deb 
Selecting previously unselected package libgl1-mesa-glx-lts-quantal.
dpkg: regarding libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise3_amd64.deb containing libgl1-mesa-glx-lts-quantal:
 libgl1-mesa-glx-lts-quantal conflicts with libgl1
  libgl1-mesa-glx-lts-saucy provides libgl1 and is present and installed.
dpkg: error processing libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise3_amd64.deb (--install):
 conflicting packages - not installing libgl1-mesa-glx-lts-quantal
Errors were encountered while processing:
 libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise3_amd64.deb
aungthiha@aungthiha:~/Desktop$ 

```

---

