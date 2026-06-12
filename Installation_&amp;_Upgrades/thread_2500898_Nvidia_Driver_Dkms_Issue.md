---
title: "Nvidia Driver Dkms Issue"
date: 2024-09-15
forum: Installation &amp; Upgrades
---

### Post by the-phantom on 2024-09-15
The Following Issue While Installing Driver : 
```
Errors were encountered while processing:
 nvidia-dkms-390
 nvidia-driver-390
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ubfan1 on 2024-09-15
Which Ubuntu release and kernel are you using?  See launchpad bugs [Bug #2051457 &#8220;Jammy 22.04.3 gcc compiler no longer builds module...&#8221; : Bugs : gcc-defaults package : Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457")   and [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165)  for some ideas. Might have to drop back to an earlier kernel. Are you using the graphics-drivers PPA? Their version may work better.

---

