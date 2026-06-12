---
title: "GRUB isn't listing Windows"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Armor on 2007-10-19
I had Vista installed on my 40gb SATA hard drive, then installed Gutsy the other night onto the same hard drive by manually creating a swap and / to install to. So all dandy, running Gutsty, however upon reboot, Vista is no where to be found. Only options are to boot to Gutsy. 

Some info:
I designated 10gb from the 40 to use for Gutsy: 1gb swap, rest for Filesystem. In Gutsy right now, Filesystem total size is listed as 10gb...it's like the other 30gigs and Vista have just vanished into thin air. 
Help!

---

### Post by confused57 on 2007-10-19
Open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Here's an excellent guide on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Armor on 2007-10-19
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1459     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ac99433

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
leigh@leigh-desktop:~$ 


There it is

---

### Post by Armor on 2007-10-19
UPDATE:
I popped Gutsy's live CD in and ran the partition manager to see what it had to show, and the remaining space that Vista is on is listed as something like "68gb unsed space" under sda...
Does this mean Vista is gone forever and the bet I can now hope for is a complete format of the 80gb drive and then install Vista and then Gutsy again and hope it doesn't get screwed up this time?

---

### Post by confused57 on 2007-10-20
You could try testdisk, if your Vista partition is recoverable:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
the easiest way to use testdisk  is probably to download the Gparted-Live CD, which has testdisk.

---

### Post by Armor on 2007-10-20
Thanks confused, I'll give it a shot. It looks promising.

---

