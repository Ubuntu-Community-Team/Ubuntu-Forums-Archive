---
title: "Boot Error after fixes"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by edvinm on 2012-12-25
I have had Ubuntu working on my system for months.  No hardware changes.  Now it won't boot, I just get a black screen with a blinking cursor.  I cannot get to a proper prompt and especially not into the GUI.  I tried the Boot repair CD and although it says it was successful, my boot process doesn't go any further.  It is possible that there were updates done the last time the system was up.  Any help is greatly appreciated.

[http://paste2.org/p/2645450](http://paste2.org/p/2645450)

---

### Post by oldfred on 2012-12-26
Welcome to the forums.

I moved you from the Boot-Repair mega-thread to your own thread, so we can more easily keep responses to one user. 

Since you only have one system installed, it probably is not a boot issue, but a driver issue.

If you hold shift key down from BIOS screen do you get grub menu. Then can you boot in recovery mode. Or use e on grub menu and remove quiet splash from linux line. Then you will see a lot of lines scroll by quickly but may see what driver is causing issues. May not be last shown on screen.

Also  what video card.

Some also have had issues with larger / (root) partitions. Not sure if BIOS setting, should be large, lba or AHCI but not ide. Or if a grub issue. If grub installs files beyond a certain point on drive then it may have issues. Some have solved with separate /boot partition inside 100GB, so Boot-Repair often recommends that. But Boot-Repair did not see exactly where your files were on drive. Some others have make / smaller so it is fully inside the first 100GB and used the rest of the drive as a separate /home or just as a data partition.

---

### Post by edvinm on 2012-12-26
I have tried holding down the shirt key, but I do not get the grub menu.  It still ends up going to the flashing cursor.

I have an Asus M5A88-M motherboard with onboard video that is Integrated ATI Radeon HD 4250.  It has been working fine until suddenly it didn't boot.

I will look into the BIOS settings for the drive to make sure nothing got reset there.  

Thank you for your help and I will keep you posted.

---

### Post by oldfred on 2012-12-26
Did you upgrade to 12.10?

With 12.10 older ATI/AMD video is not supported by AMD. Older Ubuntu still should have the older drivers?

       This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for Ubuntu 12.10 Quantal Quetzal.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by YannBuntu on 2012-12-26
> **oldfred said:**
> make / smaller so it is fully inside the first 100GB and used the rest of the drive as a separate /home or just as a data partition.

+1
(via Gparted, reduce sda1 from 242GB to 100GB)

---

### Post by edvinm on 2012-12-28
I did, but it was working fine even with 12.10.  How do I use the drivers if I cannot seem to get to a prompt?  Also will changing the partition result in data loss?

> **oldfred said:**
> Did you upgrade to 12.10?


---

### Post by oldfred on 2012-12-28
From liveCD use gparted to shrink partition. You should not loose any data, but always backup any data you consider valuable first, if not already backed up. 

Do you get grub menu or is problem before that?

Did you have proprietary driver installed? Some report that default open source drivers work ok if not Unity. But Unity needs more powerful systems to work well.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by edvinm on 2013-02-11
Sorry for the delay and thanks for all the help.  I downloaded Ubuntu and was able to run it off the CD.  I then got a new drive and installed ubuntu 12.10 to it. I could not boot to that drive either.  I ended up removing one stick of RAM and unplugged the DVD Rom drive.  I was then able to boot properly.  

I put my old hard drive back and that booted too.  I am thinking that perhaps one of the RAM sticks has gone bad and I will test that theory shortly.

Again, thank you for all the help.  I am glad the system is up and running again.

---

### Post by edvinm on 2013-02-19
> **edvinm said:**
>   I ended up removing one stick of RAM and unplugged the DVD Rom drive.  I was then able to boot properly.  

...

Again, thank you for all the help.  I am glad the system is up and running again.

So I tested and it works fine with both memory sticks, but not with the DVD drive plugged in.  That drive used to work fine (it is an IDE drive not SATA).  I can do without it.

---

