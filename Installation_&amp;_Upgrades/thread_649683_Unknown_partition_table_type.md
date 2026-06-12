---
title: "Unknown partition table type"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by jorgepeixoto on 2007-12-25
Hi. I have two HDs: hda, which is very slow, and hdb, which is even slower. 
hda has a Windows install.
hdb had
hdb1: reiserfs partition for data storage
hdb2: swap
hdb3: ubuntu install

I wanted to move the windows install to hdb so I could install Ubuntu in hda.

So I
backed up the important data in hdb3 to hda
reformated hdb3
moved the important data of hdb1 to the now-empty hdb3
deleted hdb1 and hdb2
created a 512 MB hdb1 for swap, and a 15 Gigs fat32 hdb2 for Windows

Then I tried copying the files from hda1 (Windows) to hdb2.

I don't remember If I did reboot between messing with the partitions and copying the data. 

The copy completed without errors.

However, after I rebooted the computer, not only I cannot mount hdb1 or hdb3, but 

cfdisk /dev/hdb

Unknown partition table type
Do you wish to start with a zero table [y/N] ?



Is there any way I can recover the data that was in hdb3?
If I remember well, the data was in two directories:

/home/jorge
and
/distfiles

---

### Post by bharadwaj on 2007-12-25
did you trying with only one HDD check between master and slave settings in you BIOS

---

### Post by jorgepeixoto on 2007-12-25
> **bharadwaj said:**
> did you trying with only one HDD check between master and slave settings in you BIOS

I doubt that is the problem, but I'll try it

Update: did not work

---

### Post by jorgepeixoto on 2007-12-26
A very important question: is it safe to mess with the partition table, as long as I have made a backup with dd?

---

### Post by jorgepeixoto on 2007-12-29
gpart has saved my day.

---

