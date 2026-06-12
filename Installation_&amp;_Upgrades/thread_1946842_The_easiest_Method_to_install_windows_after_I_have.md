---
title: "The easiest Method to install windows after I have Installed kubuntu 11.10"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by forsubhi on 2012-03-25
I have now kubuntu 11.10  installed on my pc and I want to install windows7 without affecting the existing ubuntu 

I need the easiest way to do that 

please give me easy way , not complicated ways .   :popcorn:

---

### Post by critin on 2012-03-25
The easiest way is to install Windows first.  Really.

---

### Post by perspectoff on 2012-03-25
+1

Ubuntu accommodates Windows, but Windows does not accommodate Linux. 

The easiest way is to make sure you have 4 partitions on your hard drive (using GParted from your existing Ubuntu installation).

Then install Windows into one or two partitions (Windows 7 and 8 require 2 partitions).

Some versions of Windows installers re-format the entire disk with one or two partitions. If you have one of those versions, you're going to have to shrink the partitions before installing Ubuntu (which requires one or two partitions itself).

The best way to do that is either from within windows itself or using a program such as Perfect Disk (Trial version).

All of my methods are complex, but those two steps are somewhat easy.

See:
[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu)

and

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Mark Phelps on 2012-03-26
> **forsubhi said:**
> I have now kubuntu 11.10  installed on my pc and I want to install windows7 without affecting the existing ubuntu. ... I need the easiest way to do that 

Don't you just love the way you ask a simple question here and folks give you a roundabout answer??

Anyway ... the easiest way is to do the following:
1) Since you can't shrink a partition while it is in use, then boot using an Ubuntu LiveCD, select the Try Ubuntu option, run GParted (GNome partition editor) -- and use it to shrink the Ubuntu partition to leave some unallocated space.  Would recommend 30GB for Win7.
2) Reboot, this time, from a Win7 DVD, and install to the unallocated space -- and NO, it will NOT wipe out your hard disk!
3) After that is done, when you reboot, it will boot right into Win7 -- NOT because MS hates other OS's (!), but because Windows overwrote the MBR code.
4) Using the instructions below, reinstall GRUB so that you can boot into Ubuntu: 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by forsubhi on 2012-03-26
thank you very much Mark Phelps and thank for all subscribers 
this is what I want

---

