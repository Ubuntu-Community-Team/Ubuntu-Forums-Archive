---
title: "Grub install failed on Gusty install"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by feysal on 2007-10-20
Hi,
I'm trying to install Ubuntu 7.10 onto my computer, but I have this message at the end of installation
> Grub install failed on hd0
This is a fatal error
I have a 4 partitions, two NTFS, one is Ext3 and the last is swap
Please help me

---

### Post by ccprog on 2007-10-20
Is hd0 a ntfs or ext3 partition?

If you have some idea what grub does, you might want to try fixing problems with the [Super GRUB disk]("http://forjamari.linex.org/projects/supergrub/").

---

### Post by ciuci on 2007-10-31
I think this is the 3rd topic with this problem, but I'm going to try my luck everywhere I can! I have got the exact same problem! Can anyone help?

---

### Post by ciuci on 2007-11-01
heloooooo, is there anyone here?

---

### Post by adrian15 on 2007-11-06
> **feysal said:**
> Hi,
I'm trying to install Ubuntu 7.10 onto my computer, but I have this message at the end of installation

I have a 4 partitions, two NTFS, one is Ext3 and the last is swap
Please help me

Why don't you try to do a little /boot  (100 MB) partition at the beginning of the free space (once you remove the ubuntu and swap partitions) ?

With SGD you should be able to boot your system in the meanwhile.

adrian15

---

