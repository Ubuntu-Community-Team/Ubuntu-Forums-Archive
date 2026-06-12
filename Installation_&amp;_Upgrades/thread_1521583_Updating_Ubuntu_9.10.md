---
title: "Updating Ubuntu 9.10"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Garrett85 on 2010-07-01
I have a computer split between Windows Vista and Ubuntu 9.10. A friend of mine who has the same configuration update his Ubuntu several months back and found that his Windows partition was unable to boot up. In order to restore his sytem he had to run Windows recover through his Windows CD. After doing some research I found that a lot of people were having this problem and apparently it had something to do with "Karmic to Lucid" update.

I have not update my Ubuntu in months because of this very problem. What I want to know is, has his problem been fixed? Is it save for me to finally update?

---

### Post by bcbc on 2010-07-01
The problem you are referring to is the part where it asks you where to install the grub2 bootloader. A screen pops up showing:
```
/dev/sda
  /dev/sda1
  /dev/sda2

```
etc. You are supposed to check where to install it.

Scenario 1. You have a proper dual boot i.e. you installed Ubuntu direct to partition, not using WUBI. In this case, only select the drive you boot from, usually /dev/sda (make sure you don't select any of the partitions /dev/sda1 etc)

Scenario 2. You installed using wubi (e.g. on your c: drive you have c:\wubildr, c:\ubuntu). 
In this case, do not install grub anywhere. The next screen will warn you about it, just check to ignore and proceed.

Also, in the General Help forum, there is a sticky with known 10.04 issues with their workarounds ([http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475))

For all cases, it's a good idea to backup your data first.

EDIT: I've attached screenshots of what you might see. The comment about "it is often a good idea to install GRUB to all of them" refers to drives /dev/sda, /dev/sdb - not partitions /dev/sda1. That is the part that has tripped up people.

---

