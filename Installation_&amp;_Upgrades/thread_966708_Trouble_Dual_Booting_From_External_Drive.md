---
title: "Trouble Dual Booting From External Drive"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by artilluer on 2008-11-01
Angry  Trouble Dual Booting From External Drive
K so i believe to be pretty good with computers and I've tried to fix my problem by googling and checking the forum posts but no one has exactly the same problem as me. I can install Linux fine on my external Acomdata 250 GB hard drive which I partitioned 50/50 so I can still use it on windows. Whenever I try to start up the computer and go into the bios setting and go to boot priorities I can't see my external drive. So I keep the boot from main drive and I had grub installed in the main MBR in my (hd0) for windows but Linux is in (hd2,4)and I always get error 21 whenever I install grub and try to start the computer.

I tried to install grub through live cd typing sudo grub, find /boot/grub/stage1, root(hd2,4), setup(hd0), quit but didn't work. I tried super grub disk and it could fix it.

Pleas help.

Here's some information on my setup

Disk /dev/sda: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07eca173

Device Boot Start End Blocks Id System
/dev/sda1 63 10236239 5118088+ b W95 FAT32
/dev/sda2 * 10236240 117210239 53487000 7 HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20b9746a

Device Boot Start End Blocks Id System
/dev/sdb1 63 312575759 156287848+ c W95 FAT32 (LBA)

Disk /dev/sdc: 249.9 GB, 249925971968 bytes
255 heads, 63 sectors/track, 30385 cylinders, total 488136664 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x355f0e8e

Device Boot Start End Blocks Id System
/dev/sdc1 * 63 241762184 120881061 b W95 FAT32
/dev/sdc2 241762185 488135024 123186420 5 Extended
/dev/sdc5 241762248 483604694 120921223+ 83 Linux
/dev/sdc6 483604758 488135024 2265133+ 82 Linux swap / Solaris

---

