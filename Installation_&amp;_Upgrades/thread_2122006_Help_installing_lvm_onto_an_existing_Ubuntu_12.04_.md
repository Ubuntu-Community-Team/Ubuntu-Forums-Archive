---
title: "Help installing lvm onto an existing Ubuntu 12.04 system"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by pappo on 2013-03-03
I currently have two 500Gb hard drives.  

sda is 500Gb internal drive and I have installed Ubuntu 12.04 desktop on it.  sda1 - 20Gb root partition  sda7 80Gb - home partition  sda5 - 365Gb unused.
sdb is external (USB) 500Gb hard drive   sdb1 - I use as a home file server storage and share using samba.

What I would like to do is add the sdb1 and sda5 partitions into a LVM Volume Group and that would become my Logical Volume for file server storage.  That would increase my file server storage

So my question is, can I change my existing file system into a LVM system without doing a new installation ?

---

### Post by fantab on 2013-03-03
I don't think that it is possible to change the file-system without re-installing Ubuntu or for that matter any OS.

---

