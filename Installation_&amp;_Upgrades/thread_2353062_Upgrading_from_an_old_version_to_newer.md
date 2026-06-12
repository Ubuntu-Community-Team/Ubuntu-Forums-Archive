---
title: "Upgrading from an old version to newer"
date: 2017-02-18
forum: Installation &amp; Upgrades
---

### Post by adhfan75 on 2017-02-18
I was just wondering if it possible to upgrade from an old version of Ubuntu to a newer version.  I have an old desktop PC which still has version 7.04 Feisty Fawn, yet has a ton of files saved on it (the usual docs, pics, music files, etc.).  I now have Live CDs for both LTS 14.04 and 16.04, and was wondering it is is possible to upgrade to either version without erasing all of my saved files?  

Upgrading the OS as well as some of the hardware on the PC was a project I was just pondering about, so thus I was just wondering if a system upgrade would even be possible.   (My only previous experience upgrading and installing Ubuntu was originally installing Feisty Fawn 7.04 on that old PC back in the day, and then later installing 14.04 on a laptop and upgrading it to 16.04 via an online download...which I've had occasional issues with as well.)

---

### Post by Autodave on 2017-02-18
Upgrading from what you have up to anything now supported is impossible: you will have to install the new system. Just make sure that you have everything backed up first for re installation afterwards. 

I would not use 14.04 since its end of support is coming: go with the 16.04: that is an LTS (long term support).  You didn't give specs on your machine, but given it has a 10 year old version on it, I would not be trying to install Ubuntu because of the memory needed. I would go either with Xubuntu or Lubuntu: Lubuntu is the least memory hungry one of the bunch.

There are also other lighter versions yet, so it would be helpful if you could post the specs of the machine.

---

### Post by howefield on 2017-02-18
Installing into the existing Ubuntu partitions but not marking them for formatting should leave your /home folder intact. But you have to back up important data before going such a potentially risky procedure, one copy of a file is just an accident waiting to happen. 

However coming from as far back as 7.04 I'd recommend a clean install rather than attempting an upgrade which will mean going through several releases some of which are no longer supported.

I'd boot and run a Live media to ensure everything works as you expect and the performance is where it should be, there is a huge difference between what you have and what you want to run in terms of requirements.

---

### Post by yancek on 2017-02-18
If you don't have a separate /home partition, you should be able to create a partition (might need to shrink the filesystem partition first) and copy your pictures, documents and music filess to the new partition.

It might be a good idea to check the minimum hardware requirements and compare that to your actual hardware.  If your PC is older, Ubuntu may not be a good option and you might be able to use Xubuntu or Lubuntu.  

Support for Ubuntu 14.04 is five years or until April, 2019 while Lubuntu and Xubuntu are only 3 which would mean April, 2017.

---

### Post by RobGoss on 2017-02-18
Post the specs for your machine it will help others to give the best advice possible. If your machine is really old them Ubuntu 16.04 may not be the right choice for you as mentioned. Try something lighter like Lubuntu

Running the live desktop with give you some indication how things will run on that machine

---

