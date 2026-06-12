---
title: "missing kernel module for ibm thinkpad t43?"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by crs on 2005-05-18
i tried to install ubuntu 4.10 on my thinkpad t43, but i'm stuck: 

installation is not possible as the installer doesn't find any physical partitions. (the partition menu is empty). the partition layout is correct however, there are 4 primary partitions on the disk (1xntfs, 1xswap, 2xext3) and i can access them when booting with the live cd.

i disabled "ibm predesktop area" and deleted the service partition.

expert installation complains about the missing "ide_scsi" module, but i could not find it on the install cd or on the net.

where could i download the missing module matching the installer's kernel version?

---

### Post by alastair on 2005-05-18
The ide_scsi module is so basic a part of the package that something else is wrong with your install.

But .... why do 4.10? This is the 5.04 forum after all. So download and install 5.04 (Hoary) and try again. This runs/installed on a T40p with no problems.

---

