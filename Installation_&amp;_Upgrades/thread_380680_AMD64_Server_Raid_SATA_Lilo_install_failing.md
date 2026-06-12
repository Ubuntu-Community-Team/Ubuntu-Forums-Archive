---
title: "AMD64 Server Raid SATA Lilo install failing"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2007-03-09
I am attempting to install Ubuntu on a new AMD 64 server (Nvidia chip set). I am using Server install CD I downloaded yesterday.

The server has 2 - 320 MB SATA hard drives I want to install as a RAID 0 software array. I was able to figure out how to partition the drive using the Logical Drive Manage in the install scripts but I can't get the install to complete. Every time it fails with a error that lilo can't be installed and the computer won't reboot. I've set lilo to install in /dev/md0, which is the RAID array device.

Typically I would allocate seperate partitions to root, var, tmp boot and my user data. Home directories are shared across the network and are on another machine.

I've tried to locate a fix online and have found several references to people with similar problems but  no clear solutions.

---

### Post by rsteinmetz70112 on 2007-03-11
I solved the problem. The fake raid on the motherboard was conflicting with the software raid when I tried to boot. The fake raid need to be disabled, it wasn not enough to not define raid sets.

After discovering that the install went smoothly.

---

