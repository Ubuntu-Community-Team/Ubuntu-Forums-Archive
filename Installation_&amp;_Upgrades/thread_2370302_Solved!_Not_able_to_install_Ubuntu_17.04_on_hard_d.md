---
title: "Solved! Not able to install Ubuntu 17.04 on hard disk"
date: 2017-09-01
forum: Installation &amp; Upgrades
---

### Post by Samlion on 2017-09-01
Hi,
 I’m trying to install on one of my hard disk, Ubuntu 17.04 Desktop, using an iso image « ubuntu-17.04-desktop-amd64.iso » (downloaded from « [https://www.ubuntu.com/download/desktop/contribute?version=17.04&architecture=amd64](https://www.ubuntu.com/download/desktop/contribute?version=17.04&architecture=amd64) »).   
 
 
 I use the same way as usual, loading the iso image on an usb key with « netbootin » and booting my system from the usb key using and instruction in the Bios.  I have used this process in the past for many times without any problem.  With the 17.04 version, the system start with the « Ubuntu ... » signal in the middle of the screen and after, nothing happens! The system seems to be freezed.
 
 
 My global configuration is multi-boot and I use Grub2 to manage wich system I’m using.  I have also tried to boot directly from Grub2 and the iso image as described on the Ubuntu documentation (in french : [https://doc.ubuntu-fr.org/tutoriel/grub2_lancer_des_images_iso](https://doc.ubuntu-fr.org/tutoriel/grub2_lancer_des_images_iso)). The result was similar as what the usb produce.
 
 
 I have tried to use the iso image with Virtualbox and the system load correctly all seems to run properly.  
 
 
 Is there somebody that can give me an idea where I can look to find the source of the problem!!!
 
 
 Thanks in advance!

Problem solved!

Seems to be caused by the dual display configuration. Have disconnected the second display and the installation can tun properly!

---

