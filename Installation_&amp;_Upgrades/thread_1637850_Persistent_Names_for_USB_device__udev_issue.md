---
title: "Persistent Names for USB device / udev issue"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2010-12-05
Hi, I have an eReader with internal flash memory and a memory card. When I plug the eReader into a USB port the system automatically recognizes it as two USB disks. Commonly /dev/sdd1 (internal) and /dev/sde (memory card) I decided I wanted them to be mounted with friendly names. eg. eReader_Internal and eReader_Card. I'm currently running a fresh install of Ubuntu 10.10. I read two different hacks explaining the process, several man pages udevadm and udev among others and created a rules file (see below). I have even confirmed that the rules are running in the correct case(s), and only the correct case(s). I set the NAME="eReader_Internal" as described. And in an alternate case tried NAME{all_partitions}="eReader_Internal". Use of udevadm confirms the device as /dev/eReader_Internal. However, it still gets mounted by what appears to be the ID_FS_UUID. e.g. /media/79B2-C739.

How do I convince the system to use the name I chose?

/etc/udev/rules.d/10-local.rules
```
ACTION=="add", SUBSYSTEM=="block", KERNEL=="sd?*", IMPORT{program}="/sbin/blkid -p -o udev /dev/%k"
ACTION=="add", SUBSYSTEM=="block", ENV{ID_FS_UUID}=="79B2-C739" NAME{all_partitions}:="eReader_Internal"
```

---

