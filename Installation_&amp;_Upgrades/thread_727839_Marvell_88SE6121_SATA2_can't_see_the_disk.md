---
title: "Marvell 88SE6121 SATA2 can't see the disk"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by dmitri1973 on 2008-03-18
Hi
I just installed the latest Ubuntu 7.10 AMD64 flawlessly. The problem is that I can not access my SATA2 HDD (works fine under xp).
M/B: ASUS M2V
SATA2 controller: Marvell 88SE6121

I see Marvell 88SE6121 device in Hardware Info though. But there is nothing under it.

Please help! I almost moved from xp to linux, this is the last obstacle (even my ATI 1950PRO works now :) )

TIA
Dmitri

---

### Post by housam on 2008-03-18
mount your partitions using this guide [[COLOR="Red"]_http://www.psychocats.net/ubuntu/mountlinux_[/COLOR]]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by dmitri1973 on 2008-03-20
thanks for reply!

i don't think this is my case. i don't see the drive itself.


dmitri@dmitri-desktop:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb505b505

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           1        8001    7  HPFS/NTFS
/dev/hda2               2        1611    12932325    f  W95 Ext'd (LBA)
/dev/hda3            1612        2434     6610747+  83  Linux
/dev/hda5               2        1567    12578863+   7  HPFS/NTFS
/dev/hda6            1568        1611      353398+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55545ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9733    78180291    7  HPFS/NTFS

but the controller seems to be working fine (see the attachment).

---

### Post by dmitri1973 on 2008-03-20
Just checked the booting from the latest gparted livecd... it does not see the disk either. i have a bad feeling :cry:

---

### Post by dmitri1973 on 2008-03-24
so winxp won again?

---

### Post by dmitri1973 on 2008-03-24
apparently sata_mv does not support E series

---

### Post by dmitri1973 on 2008-03-24
[http://linux-ata.org/driver-status.html#marvell](http://linux-ata.org/driver-status.html#marvell)

---

