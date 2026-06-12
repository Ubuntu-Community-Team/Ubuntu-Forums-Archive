---
title: "Ubuntu 10.10 boot from LIVEcd  didn't work: UBUNTU text and four red dots on display"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by jjaakkol on 2010-11-06
Live CD and USB install failed as mentioned in title.

Solution in my case was to install correct graphic card drive from USB (NVIDIA GeForce 8200M G):

UBUNTU installed  with "Alternative downloads" from CD
[http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download](http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download)

After that desktop was still not working, only prompt.
From prompt I installed desktop with "sudo apt-get install ubuntu-desktop" but desktop was still not 
working.

From boot menu I choose Recovery mode for Ubuntu

1. picked up graphic card driver matching to laptop hardware from site
2. Started ubuntu with recovery mode

In recovery mode you need to give command to be able to install driver:
3. telinit 3 (it will ask your username and psw what you gave in installation)
4. mkdir /media/usb
5. mount -t /dev/sdb1 /media/usb (you can check your usb stick "dev name" with sudo fdisk -l)
6. cd /media/usb/linux (I had driver in linux directory)
7. sudo ./NVIDIA-Linux-x86-260.19.12.run
Installation should start. I just followed instructions.
8. sudo reboot- f
9. Start Ubuntu in normal mode.

Desktop is OK now! So my problem was in the end that graphic driver in Ubuntu installation "package" was not compatible with my hardware.

---

