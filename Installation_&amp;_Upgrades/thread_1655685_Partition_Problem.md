---
title: "Partition Problem"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by imrairai on 2010-12-30
Hi everyone! Sorry to bother you but im new in ubuntu and i installed ubuntu 10.04 in my laptop. I didn't have any partition..is there a way to make a partition though i already installed ubuntu? And also what will happen if i update my os without a partition, will my files be erase?

---

### Post by Bucky Ball on 2010-12-30
System->Administration->Gparted Partition Editor

Make sure you have some free space to create the partition in. Update will not kill anything. They only update packages in your operating system. ;)

You're not bothering us, that's why we're here! Welcome and hope you enjoy your OS and the learning curve.

---

### Post by Idefix82 on 2010-12-30
You certainly have at least one partition, namely the one on which Ubuntu is installed. If you want to have a separate partition for your personal files, you will need to create one:
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

Once you have done that, you will be able to upgrade to a new version of Ubuntu while preserving all your documents, music, etc. Note that there is a difference between regular updates and an upgrade to a new version of the OS. You can safely install the regular updates anyway, even without having a separate /home partition.

---

### Post by imrairai on 2010-12-30
> **Bucky Ball said:**
> System->Administration->Gparted Partition Editor

Make sure you have some free space to create the partition in. Update will not kill anything. They only update packages in your operating system. ;)

You're not bothering us, that's why we're here! Welcome and hope you enjoy your OS and the learning curve.
Thank you so much! I will try that..im kinda nervous because I dont want my files to be erased. Haha. Anyway, thank you again..:)

---

### Post by imrairai on 2010-12-30
> **Idefix82 said:**
> You certainly have at least one partition, namely the one on which Ubuntu is installed. If you want to have a separate partition for your personal files, you will need to create one:
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

Once you have done that, you will be able to upgrade to a new version of Ubuntu while preserving all your documents, music, etc. Note that there is a difference between regular updates and an upgrade to a new version of the OS. You can safely install the regular updates anyway, even without having a separate /home partition.
I see.. :) thank you thank you! Coz i really dont want to reinstall ubuntu because i already installed many applications including my programming needs. Anyway, thank you again. :D

---

### Post by Bucky Ball on 2010-12-30
Just make sure you BACK UP anything irreplaceable before diddling with partitions. If you already have free space, you're good to go. Just leave your existing partition alone and create a new one. ;)

---

