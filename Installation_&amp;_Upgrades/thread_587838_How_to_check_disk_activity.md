---
title: "How to check disk activity?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by tomcatf14 on 2007-10-23
Any tool to monitor disk write/read activity? I want to know if the disk is being write or read more.

---

### Post by ihcnet on 2007-10-23
Iostat should be able to do what you want. Install iostat with ```
sudo apt-get install sysstat
```. Then run ```
iostat -d 2
``` this will update the output every two seconds, there are more options than this, just check ```
man iostat
``` for more information. Good luck.

---

