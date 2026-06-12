---
title: "Change boot flag?"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by jordinf on 2011-09-27
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d450f4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580       97524   770668363    7  HPFS/NTFS
/dev/sda4           97524      121602   193405953    f  W95 Ext'd (LBA)
/dev/sda5          112805      121602    70654976    7  HPFS/NTFS
/dev/sda6           97524      112316   118819840   83  Linux
/dev/sda7          112316      112804     3921920   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001de1d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         986     7913440+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(984, 254, 63) logical=(985, 46, 21)

```

How do I change my boot flag from sda2 to say sda6

---

### Post by westie457 on 2011-09-27
Hi, there is no need to change the BOOT flag as Linux does not need it. The BOOT flag is there for Windows. In Linux the boot procedure is controlled by Grub.

Having said that and you still want to change the BOOT flag there is probably an easy way in the terminal and I do not know it.

Start Gparted right-click on the partition you want to change and select 'Manage Flags'.

---

### Post by oldfred on 2011-09-27
+1 on westie457 comments.

IF you have to repair Windows, it also needs the boot flag to know which install to repair. If boot flag is not on your Windows install it will not repair anything.

Some BIOS (Intel motherboard primarily) will only let you boot if you have a boot flag on a primary partition (Seems to assume Windows).

Just for info this is the command line version:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

Speaking of repair of Windows. Have you made a repairCD? You should have a repairCd or liveCD for the current version of every system installed.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

