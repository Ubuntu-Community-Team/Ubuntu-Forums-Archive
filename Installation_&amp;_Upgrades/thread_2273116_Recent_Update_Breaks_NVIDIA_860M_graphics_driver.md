---
title: "Recent Update Breaks NVIDIA 860M graphics driver"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by mstutzzzz on 2015-04-10
I Recently had to re-install ubuntu 14.0.4 on my Computer (SSD went bad) it installs without an issue and I can install and run the NVIDIA graphics without an issue. As soon as I begin updating from 14.04.1 14.04.2 with the NVIDIA drivers selected and not Intel or open drivers my screen blacks out. I have to purge the driver re-select NVIDIA and switch to intel. Does anyone else have this problem?

---

### Post by dino99 on 2015-04-11
the nvidia issues are now fixed for 'vivid' (aka 15.04); you should dist-upgrade your installation to get a better experience : open /etc/apt/sources.list and change the distro name to 'vivid', then upade/upgrade but disable first third party source if exist

---

### Post by mstutzzzz on 2015-04-12
Thanks ill have to give it a go, recently had to re-install windows.

---

