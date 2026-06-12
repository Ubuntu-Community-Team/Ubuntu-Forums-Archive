---
title: "Folder sizes limited - Ubuntu 14.04"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by Davis_Goertzen on 2014-07-31
Hello all,

I recently installed Ubuntu 14.04 and during installation tried to set up a partition for boot and another for files. Afterward, I found that my Documents, Downloads, Music, Pictures, and Videos folders were all severely limited. So, I used GParted to merge the 2 said partitions. However, the folders are still so limited that I can only put a few GB of data in them before they will not accept more. If anyone has any ideas why this is and how I can correct it, I would greatly appreciate it.

---

### Post by Davis_Goertzen on 2014-07-31
It may be helpful to add that I had initially installed the OS on a 12 GB partition, and even after having used GParted, the Details section is only showing 12 GB for my disk. Does anyone know how to correct this?

---

### Post by oldfred on 2014-08-01
Post these, if you have any other partitions mount them or click on them in Nautilus so they are mounted:

sudo parted -l
df -h
mount
cat /etc/fstab

---

### Post by Davis_Goertzen on 2014-08-03
FWIW, I just gave up and used another hard drive I had lying around.

---

