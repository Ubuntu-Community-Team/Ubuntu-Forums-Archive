---
title: "Gparted doesn't open and installation trouble"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by daviede on 2012-10-17
I was trying to install ubuntu 12.04 from a bootable USB, but the installation hanged at "Preparing to Install."  I searched the forum for this problem and came across a thread that suggested it could be due to a problem with the partitions.
However, when I try to open gparted, it  hangs, with the bar by "scanning for devices" endlessly going back and forth.  I couldn't understand what my problem might be for this or the "preparing to install" freezing.  Here is what I get when I try to open gparted from terminal: ```
ubuntu@ubuntu:~$ sudo /usr/sbin/gparted
======================
libparted : 2.3
======================

** (gpartedbin:21600): WARNING **: Could not connect: Connection refused

```Thanks for any help.

---

### Post by jerrrys on 2012-10-17
try

gksudo gparted

---

### Post by daviede on 2012-10-17
> **jerrrys said:**
> try

gksudo gparted
It doesn't say anything about connection being refused this time but I still get the same response from gparted: "scanning all devices" and no progress beyond that.

---

### Post by Starcruiser322 on 2012-10-18
Can you mount the drive at least?
sudo fdisk -l          (that's an "L" by the way)
(mentally select the right partition, example sda1)
sudo mkdir /media/host
sudo mount -t **ntfs-3g** /dev/**sda1** /media/host 
(replace sda1 with your drive, also assuming windows ntfs partition, else use vfat or ext2/4)

when done, to unmount:
sudo umount /dev/**sda1**

---

