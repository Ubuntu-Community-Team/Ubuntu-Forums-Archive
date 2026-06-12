---
title: "ALERT! /dev/sdc1 does not exist. Dropping to a shell"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by techclerk on 2007-06-01
Ubuntu 6.06.1 i3 - installation CD that I burned the image myself

Dell Ispiron 640m laptop configured to boot to CD -> USB -> Internal Hard Drive

Maxtor One Touch III Mini 120GB USB drive

The CD installation disk boots in graphic safe mode because X crashes. From here I make the following deselections

System>Preferences>Removeable Drives and Media

Mount rem drives when hot plug
Mount rem media when insterted
Browse rem media when inserted

I plug in the USB drive.

I run the installation to select the Maxtor and erase entire disk during partitioning.

When the Maxtor boots I see grub. Both normal and recovery mode come to a halt with this message.

**ALERT! /dev/sdc1 does not exist. Dropping to a shell**

sda is the Dell hard drive
sdb is the Maxtor USB drive when I look at it from fdisk in terminal. However, the partition gui lists the drive as sdc! I think I'm sniffing out the problem.

Can anyone explain this and what I should do to get past this?

MY RESEARCH PROGRESS:
[http://ubuntuforums.org/showthread.php?t=382304&highlight=%2Fdev%2Fsdc+does](http://ubuntuforums.org/showthread.php?t=382304&highlight=%2Fdev%2Fsdc+does)

---

### Post by techclerk on 2007-06-03
I got it to work. This may just be luck, but this is how I did it.

sudo bash
fdisk /dev/sdb

Then I deleted all partitions, verified the table, wrote the changes and exited. 

When I ran install this time, no /dev/sdc conflict was created and my drive boots.

---

