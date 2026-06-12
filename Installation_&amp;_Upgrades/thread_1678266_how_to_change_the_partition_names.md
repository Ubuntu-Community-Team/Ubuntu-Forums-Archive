---
title: "how to change the partition names"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by ppm123 on 2011-01-30
i have dual boot installation-win7+ ubuntu 10.10 
working fine.
but the linux partitions are shown as 67gb, 30gb etc , filesystem.
what should be done to change the names, and should be changed to what?,for correct identification.-ppm

---

### Post by dino99 on 2011-01-30
into synaptic, install gnome-disk-utility, then set your prefs into: system admin disk utility

---

### Post by matt_symes on 2011-01-30
Hi

...or from the command line

```
tune2fs
``` 

with the L switch. From the man page...

> -L volume-label
              Set the volume label of the filesystem.  Ext2 filesystem  labels
              can  be  at  most  16 characters long; if volume-label is longer
              than 16 characters, tune2fs will truncate it and print  a  warn&#8208;
              ing.   The  volume  label  can be used by mount(8), fsck(8), and
              /etc/fstab(5) (and possibly  others)  by  specifying  LABEL=vol&#8208;
              ume_label instead of a block special device name like /dev/hda5.

Kind regards

---

### Post by kansasnoob on 2011-01-30
I prefer using Gparted to label my partitions:

[ATTACH]182324[/ATTACH]

Simple and straightforward.

---

