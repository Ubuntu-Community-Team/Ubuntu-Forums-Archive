---
title: "A Clean Slate - clear everything and reinstall again"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by Victor_Lai on 2013-10-13
Hello All,

I did searches on google and the forum, there were a lot of topics that have "clean slate" as title but didnt quite contain what I was looking for.

I recently installed Ubunutu 12.04 LTS server from a USB key on a HP ProLiant server.
It was working very well, until I accidentally flushed the IP tables.... 

I panic, and figured since I havent done much yet, the best way to recover is to just reinstall uBuntu from the USB again.

During the reinstall process, I followed all the steps I did before.
However this time around, the installer fails to install grub-pc into /target of the internal Hard drive.

Is this because the hard drive isn't in a "clean slate" state?  Would appreciate if I could get some advice on the process to follow to "clean slate" a HD (including parition table?  I feel this is the reason I am screwing up) to reinstall again.

Thanks!
V

---

### Post by varunendra on 2013-10-14
"Clean Slate" simply means a fresh installation on blank partitions. Or even better, with no partitions at all (creating fresh ones). So if you really mean to start on a "clean slate", boot into live session, delete all partitions with Gparted and create a fresh partition table (Device > Create Partition Table..) and create fresh partitions on it. Then retry the installation.

If you had configured RAID, make sure to reset or disable it (I don't have much idea about it, you should know better if you used it). Make sure to erase its metadata from the HDD as well, which usually means -
```
sudo dmraid -E -r /dev/sda
```
..replace "sda" with the target drive (sdb, sdc..)

---

