---
title: "Install fails - due to FAT16 partition?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by ZorMonkey on 2007-06-03
Hello! I've been trying to install 7.04 using the LiveCD, and at the same point every time it reboots my PC. 

I think I've tracked down the problem to a FAT16 partition. If I try to view the partition, Ubuntu reboots my PC. I think that partition is a crusty old copy of Windows NT that I dont care about, so if that's the problem I can get rid of it. 

Is there any way to determine if that's exactly why my installation is failing? I'd just rather not starting playing with partitions more than I already need to

---

### Post by louieb on 2007-06-03
what is the message you are getting? did you run the media test? MS quit using fat16 when win95 came out. That should have nothing to do with the install failing. where in the install is it stopping?

---

### Post by ZorMonkey on 2007-06-07
Sorry I havent replied sooner. I'm now up and running Ubuntu, but I dont really know how. It has been a few days so the details are a little hazy...

I was not getting any message when the computer rebooted, which made it frustrating. If I double-clicked one of the mounted partitions on that drive, my PC would instantly reboot. When installing it would fail after step 5 of 7, which if I remember correctly is when you set up a user.

I'm pretty sure I fixed it by messing with my partitions on the drive in question. I was fooling around in gparted, and noticed that one of the partitions on the drive had a warning symbol, saying a driver or something wasnt loaded (sorry for the vagueness, but I dont think that bit matters. I found out later that that's a bug in gparted with large partitions).

Anyways, my drive partions were something like this:
- Extended Partiton
    - ~2GB FAT16 Logical Partition (Crusty old NT install)
- ~54GB FAT32 Logical Partition (with warning in gparted)

So, I decided that I didnt want that old NT partition anyways, and it might be messing with how Ubuntu sees the FAT32 partition for some reason. So I changed it to the following:

- ~2GB ext3 partition (/home)
- ~54GB FAT32 partition

And then Ubuntu stopped restarting on me! I was able to install, although with more unrelated problems.

---

