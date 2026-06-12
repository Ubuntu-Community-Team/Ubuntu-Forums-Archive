---
title: "Ubuntu 18.04 Installation"
date: 2018-05-18
forum: Installation &amp; Upgrades
---

### Post by Ajufo on 2018-05-18
Hi guys, So i have a Leapbook laptop by innjoo and i planned to flash the windows os to run on ubuntu 18.04. Unfortunately the laptop has a 32gb eMMC and when i try to run ubuntu installation after going through liveboot, i gets stuck and reverts back to running normal windows 10.

How can i succefully convert the laptop to a full ubuntu machine.

---

### Post by dino99 on 2018-05-18
I have an old laptop with only 20 Gb hdd :( but running 18.04 smootly) :P
The easiest way is:
- save your data on an external device
- downloaded the bionic image and 'gparted live' onto a usb stick then format the disk with ext4 format; set / as ~ 8 gb and /home
- reboot and deactivate uefi to use 'legacy' install mode, otherwise see lp:1767703

[https://gparted.org/download.php](https://gparted.org/download.php)
[http://cdimage.ubuntu.com/ubuntu/releases/bionic/release/](http://cdimage.ubuntu.com/ubuntu/releases/bionic/release/)

[https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)

---

