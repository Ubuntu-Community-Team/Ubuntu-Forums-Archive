---
title: "bug, GUI installation doesnt see partitions"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by OwiecPL1986 on 2013-01-06
I have exalty this computer:
[http://www.sony.pl/product/vaio-seria-t/svt1311m1e](http://www.sony.pl/product/vaio-seria-t/svt1311m1e)

I download from ubuntu.com the newest 64-bit ubuntu.

The problem is when i try to install ubuntu gui instalator doesn`t see the partitions. In gparted i created ext4 partition and still gui installator doesn`t see this partition. Gpatred see all partitions and all is correct.

I dont have any idea what i can do with that, i lost all day to try find a solution.

My purpose is to install new system ubuntu but i want have still preinstalled windows 7.

---

### Post by OwiecPL1986 on 2013-01-07
To be more precise:

GUI instalator detect /dev/sda but doesn't see any partitions.

When i click anything i have error:
Sorry, Ubuntu 12.10 has experienced an internal error.

In details i see:
ExecutablePath:
/usr/lib/ubiquity/bin/ubiquity

Package:
ubiquity 2.12.16

ProblemType:
Crash

Title:
ubiquity crashed with TypeError in partman_dialog(): 'NoneType' object is not subscriptable

---

### Post by egravier on 2013-01-31
Hello,

I have exactly the same problem as above.
My laptop is an Alienware M17xR4.

No partition is shown in the installation screen. Then when I press any button I get the same error as above...

Thanks a lot for any answer you could provide.

I tried the installation with doing F6 + nomraid option.
It doesn't change anything.

When I try ubuntu from the DVD without installing, everything is working fine. The hard drive partitions are correctly mounted.

---

### Post by 35a6nxh7wcnuwzv5gtzu on 2013-02-18
Hello,

I got today the same ultrabook and wasted all the day with that problem. I finally found a solution on this website: [http://www.webstimme.de/2013/01/11/ubuntu-linux-auf-ultrabook-von-sony-installieren-anleitung-howto/](http://www.webstimme.de/2013/01/11/ubuntu-linux-auf-ultrabook-von-sony-installieren-anleitung-howto/)

You just need to uninstall dmraid. I have no idea why, but at least it worked for me.

---

### Post by oldfred on 2013-02-19
The UltraBooks use RAID to implement the Intel SRT.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

