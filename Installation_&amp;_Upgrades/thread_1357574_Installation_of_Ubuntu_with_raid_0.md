---
title: "Installation of Ubuntu with raid 0"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by mebeatyou on 2009-12-17
Hello,

I am having some trouble dual booting Ubuntu 9.10 with my Windows 7. I first installed Windows 7 and everything went smoothly and now I have that operating system on my computer. I have three hard drives, an 80GB that I use for storage, and two 640GB hard drives which are set up in a raid 0 configuration (striped). Now, when I run the Ubuntu installer for a full install on my computer, it shows devices: 
/dev/sda
/dev/sdb
/dev/sdc

sda and sdb are my two 640GB hard drives, however Ubuntu does not recognize the raid configuration. It only sees them as two seperate hard disks and does not recognize the fact that I already have Windows installed either. When in Windows 7, I partitioned my 1.2TB of space leaving about 900GB for Windows and 300-ish GB for Ubuntu, creating a separate drive essentially. So now, when in Windows, I can see C: (900GB) and D: (80GB storage), and now F: (300GB, partitioned for Ubuntu). I thought all went well with this, but now when I run the Ubuntu installer, it's as if it has no idea that I have done any of that. 

How do I get Ubuntu to install on the 300GB partition I set up in Windows 7?

Thanks for your help.

---

### Post by Grenage on 2009-12-17
This will help explain why it's happening:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by llawwehttam on 2009-12-17
Unless of course its a software raid in windows?

---

### Post by mebeatyou on 2009-12-17
I was just reading about the FakeRaid thing, however while reading, it appears to me that Ubuntu would have to be my first install, meaning I'd have to crash my Windows 7 and start everything from scratch. Is that true or is there still a way to install to my partition? I don't mean to sound ignorant, but I already went through all the trouble of putting pretty much everything I own onto my Windows 7 partition and would like to avoid doing it again if at all possible.

> **llawwehttam said:**
> Unless of course its a software raid in windows?

The entire thing is on a raid 0 set up in my bios, however the partition was created via Windows 7 disk manager.

---

### Post by darkod on 2009-12-17
First, you need to use the Alternate Install CD for raid. The standard Desktop CD will only see separate drives.
Second, you can't "prepare" partition(s) for linux in windows, they don't use same filesystem. Any ntfs partition you create you will have to delete later. Plus ubuntu needs minimum of two partitions, not one. So just set up your windows and leave the rest of the space unallocated for ubuntu.
Third, I'm not sure if you can dual boot windows and ubuntu on fakeraid like that. I'm waiting to buy second drive to test that myself, so can't help you much there.

---

### Post by Grenage on 2009-12-17
I don't know how you would go about it installing Windows first; sorry.

---

### Post by mebeatyou on 2009-12-17
> **darkod said:**
> First, you need to use the Alternate Install CD for raid. The standard Desktop CD will only see separate drives.
Second, you can't "prepare" partition(s) for linux in windows, they don't use same filesystem. Any ntfs partition you create you will have to delete later. Plus ubuntu needs minimum of two partitions, not one. So just set up your windows and leave the rest of the space unallocated for ubuntu.
Third, I'm not sure if you can dual boot windows and ubuntu on fakeraid like that. I'm waiting to buy second drive to test that myself, so can't help you much there.

What is this Alternate Install CD?

---

### Post by Grenage on 2009-12-17
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by darkod on 2009-12-17
Scroll down little bit:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Basically it's the same as desktop but the installer is text based, not GUI. So during installation process it will be text based, like the older XP looked like.

---

### Post by gilson585 on 2009-12-20
you will need to follow the instructions in my post after you install 9.10 if you want to be able to boot off of fakeraid [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

### Post by mebeatyou on 2009-12-21
> **gilson585 said:**
> you will need to follow the instructions in my post after you install 9.10 if you want to be able to boot off of fakeraid [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)
 
Ok I have the alternate install CD as well as the live CD at my disposal to use. What I have is a C:\ drive with 900GB of space for Win7 then 300GB unallocated space (approximations of course). I ran the alternate install CD and nothing is recognizing the fact that my hdd is partitioned at all. It only recognizes seperate hard drives.

---

### Post by mebeatyou on 2009-12-21
I am currently in the alternate install disc installation process attempting to follow the fakeRaid howto guide. Whe it comes to partition however, the guide shows that I should have partitioning options, but the installation acts as if I have already gone through that and merely asks if I would like to Undo changes or continue partitioning and write changes to disk, which I am afraid to do in fear of it erasing what is already on my hdd in the windows partition.

---

### Post by gilson585 on 2009-12-21
In 9.10 you no longer need to use the alternate cd to install onto fakeraid. I used the livecd and it detected the raid just fine with no intervention. If the livecd doesnt work I would assume either the array is not setup properly or dmraid does not support your raid controller yet. If it's the latter you might be able to use mdadm to use raid in linux. I'm not sure on the specifics but I've seen it around somewhere. Don't quote me on this but using mdadm may restrict your options with dual booting.

---

