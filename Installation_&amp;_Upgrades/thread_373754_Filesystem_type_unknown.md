---
title: "Filesystem type unknown"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by Napu on 2007-03-01
Hi, first of all sorry ab my english

Im installing Ubuntu amd64 6.06.1 in a raid0 hd using fakeraid guide

Im In the Installing the Bootloader Package point when i get into grub shell
i tell GRUB which device is the boot device with code
```
device (hd0) /dev/mapper/nvidia_jcajaddb
```
then
```
root (hd0,5)
```
It fails throwing this error:
Filesystem type unknown, partition type 0x6

My  nvidia_jcajaddb6 partition is EXT3, but grub tell me this message. any suggestions?

Thanks in advance

---

### Post by Napu on 2007-03-12
Up!

---

