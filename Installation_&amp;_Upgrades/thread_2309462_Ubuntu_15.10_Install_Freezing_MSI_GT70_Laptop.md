---
title: "Ubuntu 15.10 Install Freezing MSI GT70 Laptop"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by Eric_Wenzel on 2016-01-10
I have an MSI GT70 Laptop and have loaded the Ubuntu 15.10 iso onto a 16gb thumbdrive using unetbootin.  I did a file integrity check and there are no files with an error.  I have disabled secureboot and fastboot.  I understand there are potential issues with nvidia graphics cards but I am unsure what to do to potentially resolve this possible issue.  I have the most recent video card driver installed on my windows 8 installation.   Current nvidia driver version is 361.43.

When I boot from the USB, select Install Ubuntu and load the installation gui.  I can get 3 menus deep before it completely freezes.
Ive tried to install without connecting to my wifi.
Ive also tried to connect to my hidden network but it freezes before I have the opportunity to put my network information in.

I would also like to point out that I have very little experience with linux of any flavor so Im not savvy to the lingo.  Please help!

EDIT:  I should point out that I want to install ubuntu alongside my windows OS.  Not use it as my primary or sole OS.

---

### Post by Geoffrey_Arndt on 2016-01-11
Perhaps the installer (if the iso is good) has issue with the disk partition table . . . how is your hdd setup now?   Can you post a screenshot?   To install, Ubuntu would either need at least 20 GiB in "unallocated" space or a defined partition using a Linux file system like ext4  . . . . the installer has to see those to even have a chance to know where to install.   Also, what install option are you using?   You shouldn't use "install alongside . . " but use the "something else" (which is a custom install process).  

Also, what method did you use to shrink the windows partition to make room for Ubuntu?    Note that if you're on a uefi system (versus standard MBR bios), then the installer must also be installed in uefi mode.

Regarding nvidia , you will have to either install those drivers after install, OR, better, be sure you have a stable web connection (ethernet best) and check the box to install updates and restricted/proprietary packages (software).  That way, Ubuntu will try to install those drivers during the install so you don't get a "Black Screen" upon install reboot.


Good luck.

---

