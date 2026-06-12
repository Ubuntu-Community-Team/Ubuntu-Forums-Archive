---
title: "qt-sdk libqt4-opengl-dev dependency issue on lucid"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by ccdwiu on 2012-08-29
```
chris@jarvis:~$ sudo apt-get install qt-sdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qt-sdk: Depends: libqt4-opengl-dev but it is not going to be installed
E: Broken packages
chris@jarvis:~$ sudo apt-get install libqt4-opengl-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-opengl-dev: Depends: libgl1-mesa-dev but it is not going to be installed or
                              libgl-dev
                     Depends: libglu1-mesa-dev but it is not going to be installed or
                              libglu-dev
E: Broken packages

```Trying to install the dependencies leads to an extremely large (uncountable) number of similar errors. Has anybody any advice or an idea of what is going on?

Ubuntu 10.04

---

