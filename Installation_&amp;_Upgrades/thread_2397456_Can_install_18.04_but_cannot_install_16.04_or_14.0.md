---
title: "Can install 18.04 but cannot install 16.04 or 14.04"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by bcr-jim on 2018-07-29
I am new to Ubuntu.  I was able to successfully install 18.04 on our desktop.  However, the software package from NVIDIA for their Jetson, I am trying to use requires the use of either 16.04 or 14.04.  I receive an error message on the installation of 16.04 as below, and 14.04 gives the message Error 15: ([http://grub4dos.chenall.net/e/15](http://grub4dos.chenall.net/e/15)).  Any help on this would be appreciated:

[ATTACH=CONFIG]280577[/ATTACH]

---

### Post by oldfred on 2018-07-29
Grub4dos is not normally used with Ubuntu. That often is used with EasyBCD?

What brand/model system?

That does not seem to be a standard system?
[https://developer.nvidia.com/embedded/linux-tegra](https://developer.nvidia.com/embedded/linux-tegra)

---

### Post by bcr-jim on 2018-07-29
Host System is Alienware Area 51 R4.  The Target system is the Jeston.  We are able to get the 16.04 on it without any problem.  We need to be able to run 16.04 or 14.04 on the Host computer to do vision training for deployment on the Jetson.

---

### Post by oldfred on 2018-07-29
Alienware is similar to Dell.
You may need to update UEFI from Alienware. And if SSD update SSD firmware.
Dell need drives set to AHCI, not RAID nor Intel SRT.

Other Alienware threads.
       Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

### Post by bcr-jim on 2018-07-30
Ran update for BIOS and 16.04 loaded without any problems.  Thanks for help.

---

