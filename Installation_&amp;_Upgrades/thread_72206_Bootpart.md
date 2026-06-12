---
title: "Bootpart"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by ~J~ on 2005-10-05
Hi,

I've installed WinXP on my SATA RAID0, and Breezy on a secondary disk which is the primary master.

My motherboard is set to boot via the SATA.

I've run the bootpart utility so I now have a menu when I boot, but selected Ubuntu simply flashes a message before returning to the OS menu.

By typing Bootpart at my dos prompt, I get the following...

Physical number of disk 0 : 89799
 0 : C:* type=83  (Linux native), size= 19535008 KB, Lba Pos=63
 1 : C:  type=b  (Win95 Fat32), size= 19792080 KB, Lba Pos=39070080
 2 : C:  type=5  (Extended), size= 875542 KB, Lba Pos=78654240
 3 : C:  type=82   (Linux swap), size= 875511 KB, Lba Pos=78654303
Physical number of disk 1 : d1e0d1e0
 4 : D:* type=7  (HPFS/NTFS), size= 120053713 KB, Lba Pos=63
Physical number of disk 2 : ffffffff
 5 : E:* type=7  (HPFS/NTFS), size= 312568641 KB, Lba Pos=63

My Linux is partitioned accross a 40Gb drive, 20Gb Linux, 20Gb FAT32 and the swap and extended to the rest.

I've typed the following...
Bootpart 0 c:\bootsect.lnk "Linux"

Which has changed my boot.ini to the following...

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\bootsect.lnk="Linux"

Any ideas as to how I can perform the dual boot?  If it helps (or not), I used GRUB instead of LILO.

TIA

---

### Post by darkmatter on 2005-10-06
~J~

Take the Windows entrys out of the settings, and boot from the Live CD.

Try to mount the Breezy partition, and let me know what the results are.

---

