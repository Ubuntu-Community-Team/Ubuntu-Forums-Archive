---
title: "No detected operating systems when trying to dual boot Ubuntu on Mac"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by Liam_Byren on 2016-03-07
Hi all

I'm trying to dual install Ubuntu onto my Mac, I followed these instructions [http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/) and I'm using a bootable USB

It was all going fine until I tried to install Ubuntu, there was no option to install it alongside Mac OS and I get the Message"This computer as no detected operating systems." which is obviously wrong since I has a working version of OS X.

Please help me, I think I might have to use FixParts but have no idea how, been baffled for the last 4 hours and I'm close to smashing the screen

Regards
Liam

---

### Post by yancek on 2016-03-07
Did you get the correct iso from the site below?  Do you get Try Ubuntu and Install Ubuntu options on boot?  Did you have any problems installing rEFind or shrinking the Mac partiton or any other steps?  If you don't see the Install Alongside Mac, try the manual option which is Something Else.  Select the Try Ubuntu option and boot to the Desktop, open a terminal and run these two commands:  sudo fdisk -l  and sudo parted -l and post the output here.  Both commands have a Lower Case Letter L.

[http://cdimage.ubuntu.com/releases/14.04.4/release/](http://cdimage.ubuntu.com/releases/14.04.4/release/)

---

