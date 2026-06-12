---
title: "Ubuntu in Windows 7"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by totalfunky on 2012-02-22
I need to install Ubuntu 11.10 inside Windows 7(32 bit) on Dell Latitude E6410. I've already downloaded iso image of the same. Could someone please help me out and let me know how I can install the same using USB drive. Till now I've tried following:
1. Created a bootable usb drive and try to install it but couldn't get any option to create a seperate partition for the same. (Though I didn't want to install like this as I want to install inside windows 7 only)
2. Tried with the help of unetbootin-windows-568.exe and used following options 
Distribution : Ubantu Version : 11.10_Live
DiskImage : Path of image ubuntu-11.10-desktop-i386.iso on my local system.
Type : Hard Disk   C:\ (Second time I used USB Drive but it also didn't work)
but after installation when I rebooted the system I got a messge saying "Unable to find a medium containing a live file system". 
 
Please help.
 
-Regards

---

### Post by Mark Phelps on 2012-02-23
To install INSIDE Windows (using Wubi) you need to be RUNNING Windows during the installation.  I don't believe that you can install the way you want booting from USB or CD.

Basically, you do the following:
1) Download the Ubuntu ISO file to a directory
2) Download wubi.exe to the SAME directory
3) Right-click on the wubi.exe file and select "Run as administrator"

That will do a Wubi install.

---

