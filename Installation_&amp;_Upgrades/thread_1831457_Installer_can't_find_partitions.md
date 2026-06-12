---
title: "Installer can't find partitions"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by epowerj on 2011-08-23
I am trying to install ubuntu v11 as dual boot. When I am installing it, after I choose my keyboard and press next, the window shows the screen where you select the partitions.  The drop down menu shows my hd (sda1) but the selection screen above shows nothing. There are also buttons like new partition table, delete, and new partition, but They are all whited out, I can't click them. I've tried it with the v10 disc and with same problem.
Ubuntu v8 works, I installed it no problem. But I need v11 and I can't Upgrade from v8 without the disc. I need a way to upgrade to v11, or a way to fix the problem with the disc.

---

### Post by oldfred on 2011-08-23
Welcome to the forums.

With win7 most systems use all four primary partitions, so there is no place to install. You can have four primary partitions or 3 primary and one extended (which is a primary). And then the extended partition can hold any number of logical partitions. Linux installs and runs from logical partitions just fine, Windows first install/bootable partition has to be a primary partition.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other brands:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by epowerj on 2011-08-23
I have a pretty old computer (hp compaq d530) that runs on Windows XP. I installed XP on a single partition that took up almost the whole hd. Ubuntu v11 and v10 had the problem that I described, but in v8 I could recize the partition and install. I tried to upgrade from v8, but it can only upgrade to v9, which is no longer supported. I was able to try out v10 without installing it  and the system could could see the hd.

---

