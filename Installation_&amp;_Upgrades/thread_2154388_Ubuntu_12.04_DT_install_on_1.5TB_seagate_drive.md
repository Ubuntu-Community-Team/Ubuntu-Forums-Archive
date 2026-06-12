---
title: "Ubuntu 12.04 DT install on 1.5TB seagate drive"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by tookey on 2013-06-14
I am having problems with a 1.5TB seagate drive showing up when I try to install Ubuntu 12.04.  The machine is an HP H8-1534 Desktop.  I suspect that the issue is occurring because of the size of the hard drive.

Does anyone have advice on installing ubuntu on a 1.5TB drive?

---

### Post by dino99 on 2013-06-14
can you set the partitions manually first ?
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by oldfred on 2013-06-14
Is this a new UEFI system?

If so you really need to use gpt partitioning on external drive and install Ubuntu in UEFI mode also. If Ubuntu is in BIOS mode you would have to go into UEFI/BIOS and turn it on or off to boot other system.

See my signature for more info on UEFI with two drives.

---

