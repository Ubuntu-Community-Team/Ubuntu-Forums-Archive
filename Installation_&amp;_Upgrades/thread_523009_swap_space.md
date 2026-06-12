---
title: "swap space"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by tgpqaz on 2007-08-11
right now i an installing the alternative install cd(in text mode) for ubuntu 7.04 but i can not find how to make my extra space into swap space or can i do after the installation

---

### Post by tgalati4 on 2007-08-11
In cfdisk or gparted, you need to partition a portion of the disk as swap.  You need to tell the installer to use that partition as /swap.  Sometimes this is automatic, some distros need to be told where swap is.  Some types of file systems build swap into the file system so a dedicated swap partition is not needed.  However, most live CD's will use swap to run faster so that the installation is much quicker.  Also, if you only have 128 MB, you will need swap to use the graphical installer (which needs 256 MB).  It's slow but it works.  Alternate only needs 128 MB I believe.

You can make swap afterwards, but you need to have already created the swap partition ahead of time.

sudo mkswap /dev/hda4    

(This assumes that the 4th partition of the first disk was partitioned as as swap drive)

sudo swapon /dev/hda4

(turn swap on for this session--it's normally automatic. )

Check swap usage:

>free

The swap size should roughly match the size of the partition that you created.

Good luck.

---

