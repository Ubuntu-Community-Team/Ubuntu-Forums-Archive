---
title: "Computer only boots off usb when installed. Help please?"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by dstashak on 2012-08-16
Hello all, I hope your still active on these forums because I am lost. After windows 7 was giving me major issues, I fully installed ubuntu 12.04 just now. I enjoy it but I tried  resetting the grub because my computer only boots from the usb stick. If I  take it out it won't boot, so the mdr is written on the usb I assume. I  seen this thread tried it but, it didn't work and I got this. Did I type it wrong???

[http://ubuntuforums.org/showthread.php?p=11919563](http://ubuntuforums.org/showthread.php?p=11919563)

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   617297919   308647936   83  Linux
/dev/sda2       617299966   625141759     3920897    5  Extended
/dev/sda5       617299968   625141759     3920896   82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002780160 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3911679     1955808+   b  W95 FAT32
dstashak@dstashak-Satellite-L655D:~$ **sudo grub-install /dev/sdX** (** typed what thread said maybe wrong)??**
/usr/sbin/grub-probe: error: cannot stat `/dev/sdX'.

---

### Post by dstashak on 2012-08-16
Never mind fixed LOL

had to type 

sudo grub-install /dev/**sda** instead sdx

---

