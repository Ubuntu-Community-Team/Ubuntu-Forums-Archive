---
title: "SMP + RAID1 Problems"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by benshort on 2006-08-19
Hi,

I have been trying to install dapper on a dual p3 machine with 2 80G hdds. I go through the install process and setup raid1 on 78G of each drive and / and raid0 on 1G per drive as swap.

Tihs all works ok and the machie boots. But since its a dual cpu machine I want to install the smp kernel. This is where the problem starts.

Once I have installed the 686 smp kernal and reboot i get aload of Segmentation Faults, complains that it cant find /dev/md0 and then it drops out to busybox. 

Now Im guessing that the 686 smp kernel dosent have raid complied into it, like the i386 one does. Why would this be the case, seems a bit odd.

I am atempting to compile my own kernal but i would be much happier if i could just do apt-get upgrade to get a workign kernel.

If my assumptions are right, where can i ask the ubuntu developers to compile the raid stuff into the kernal?

Ben

---

