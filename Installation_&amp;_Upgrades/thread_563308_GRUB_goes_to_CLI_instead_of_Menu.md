---
title: "GRUB goes to CLI instead of Menu"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by Guardian-Mage on 2007-09-29
I just installed Ubuntu 7.10 Beta for the third time. After I installed it once, it didn't work, I reformatted, tried again, reformatted, tried 7.04 Final, reformatted and did 7.10 again. I have two hard drives.

Internal 80GB Drive, 1 NTFS Partition, Windows XP Home
External 250GB Drive, 1 EXT3 Partition(20gb), 1 SWAP(1.5GB)  Partition, 2 NTFS(The rest)  Partitions

The same problem happens every time. This time I manually installed to order the partitions right. Now I don't get an error 18 with GRUB Stage 1.5. Now GRUB works but instead of showing the GRUB Bootloader menu, it goes to the GRUB CLI. I used a Live CD to get help, and I figured out how to get into Windows.

grub > root (hd0,0)
grub > rootnoverify(hd0,0)
grub > chainloader +1
grub > boot

And Windows Starts Fine. I cannot get Ubuntu to boot up. It may have something to do with the fact that my external hard drive de-activates shortly after the GRUB CLI appears. It also won't turn back on when I start windows, it only ever turns back on and mounts when I use my Live CD.

Model of the External Hard Drive is a Seagate Desktop Agent 250GB.

Any help is greatly appreciated.

---

