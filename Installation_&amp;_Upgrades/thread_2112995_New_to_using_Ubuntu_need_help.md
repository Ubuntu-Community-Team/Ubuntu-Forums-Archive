---
title: "New to using Ubuntu need help"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by NVale on 2013-02-06
I just recently decided to start using Ubuntu opposed to windows for various reasons, but after installing(12.10 32 bit) and trying to boot I am brought to a black screen which says the following:
BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

I am not sure what to once this message pops up onto my screen and before I had already installed this onto my desktop with no problems, but now I am having this problem with my laptop. I apologize in advance if this is a easy problem to fix but I am fairly new to Ubuntu and not quite sure with how to fix this problem.

---

### Post by dino99 on 2013-02-06
how did you do installation ?

here is how to set the partitions:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by choosing "Something Else" into the installer.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

then when installing  the  iso, choose the "manual" installation

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

