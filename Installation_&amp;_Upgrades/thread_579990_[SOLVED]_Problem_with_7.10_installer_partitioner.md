---
title: "[SOLVED] Problem with 7.10 installer partitioner"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by zman0900 on 2007-10-18
I am trying to do a clean install of 7.10 onto my laptop.  When I get to the partitioner part of the installer, I chose the manual option, and set the mount points for my boot partition and the root partition, which I formated prior to starting the installer.  I also set mount points for my windows partition and my data partition.  When I try to click next, it always tells me that my boot and root partitions have not been marked for formating, so it will not let me continue.  But there is no where to mark those partitions to be formated.  How can I force it to install anyways, since I know there is nothing on those partitions, and they have already been formated to ext3 with GParted?  :confused:

My setup is:
HP dv8000 laptop
2GHz Core Duo
2GB Ram
GeForce Go 7600 256MB
2 internal SATA hdds
1 external USB hdd

Partitions are as follows:
sda2: 111.23GB ntfs (Vista)
sda3: 62.75MB ext3 (Grub)
sda4: 509.88MB extended
sda5: 502.03MB linux-swap

sdb2: 14.50GB ext3 (ubuntu)
sdb3: 509.88MB linux-swap
sdb1: 96.79GB ntfs (data)

sdc1: 298.09GB ntfs (external storage)

---

