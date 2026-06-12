---
title: "installer doesn't recognize HD"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by rihard_marius on 2011-11-10
**i cannot install ubuntu**

tried to open a live session (try ubuntu):
it stops with the violet background and the cursor, i can move the cursor, right click doesn't do anything, no icons or panel

tried to install ubuntu:
-click on install
-everything goes perfect until the allocation of the system:
 it doesn't recognize sda, i mean, when i have the options "install alongside..." it gives only two options:
  -erase disk and install ubuntu
  -manual settings
this means that the installer doesn't recognize windows

i choose "manual settings"

the partition table is as follows

sda    unknown
sdb
sdb1    ... GB
sdb2    ... GB

alredy tried live session and install with the following distros:
ubuntu 11.10
ubuntu 11.10 alt
ubuntu 11.04
xubuntu 10.10

same result

i have two HDs (sda and sdb)

sda: it has five partitions
 sda1: my partition (with docs, pics, etc)
 sda2: my brother's partition
 sda3: windows partition
 sda4: ubuntu partition
 sda5: swap partition

sdb: (deposit) it has two partitions with no system, i don't use it because it is old and when i try to install windows or ubuntu it gaves several errors, no details

---

### Post by critin on 2011-11-10
Do you have an extended partition?  I believe 4 is the maximum number of primary partitions allowed per disk.   With an extended you can use any number of logical partitions inside the extended.

---

### Post by efflandt on 2011-11-11
With a standard DOS partition table you can only have 4 primary or extended partitions.  So is sda4 a primary partition, and which partition is the extended partition that contains (logical?) partition sda5 (was any Linux running with those before)? Are any of the partitions Windows Volumes?

It may help to post the output of **sudo fdisk -l** (small L), and wrap that output in code tags by highlighting it and clicking the **#** symbol in message window so formatting is preserved.

---

### Post by rihard_marius on 2011-11-11
attached screenshot of the windows partition manager, since i cannot install ubuntu or use a live session

it is wrong, the disk is 1 TB disk with the following partitions:

C: local disk 206 GB
E: Evelyn     250 GB
F: Richard    446 GB

wichs sums like 900 GB

I did a 98 GB for ubuntu and a 2 GB for swap once, now i cannot access the disk from the ubuntu installer

---

