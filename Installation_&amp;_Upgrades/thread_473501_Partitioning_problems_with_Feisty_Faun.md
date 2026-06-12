---
title: "Partitioning problems with Feisty Faun"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by carytid9 on 2007-06-14
For some reason, hard disk partitions are treated by Feisty as if they were SCSI devices (identified as sda(x) etc), in spite of the fact that they are actually on IDE hard disks. This appears to mean that there is a lower limitation on the number of partitions which can be accessed on a given drive. The limit for SCSI devices is 15; I'm not sure of the maximum number of IDE devices which is allowed, but I believe it to be 63.

You may wonder what I'm doing with all these partitions, but I have regularly allotted separate partitions to root, boot, usr, home and var. Installing 3 distros and a swap file exceeds the limit of 15, so Feisty can't be installed as a new set of partitions.

There is a program called MAKEDEV which I believe sets up the /dev directory at some stage, but I don't see why it should identify SCSI devices, and not IDE. I have not come across this limitation on other distros.

Why did the developers set it up this way? It is a serious limitation for those who want to evaluate a number of different distros - or perhaps there's another solution?

---

### Post by derby007 on 2007-06-14
I noticed that as well..........all my current partitions are SDxxx, but it seems to work OK !

---

### Post by carytid9 on 2007-06-14
> **derby007 said:**
> I noticed that as well..........all my current partitions are SDxxx, but it seems to work OK !
Do you have more than 15 partitions? I found that so long as I installed on partions below the 16th, a Feisty install was fine. There were no sdxx files in /dev above sdx15, and trying to use mknod to create one didn't work.

---

