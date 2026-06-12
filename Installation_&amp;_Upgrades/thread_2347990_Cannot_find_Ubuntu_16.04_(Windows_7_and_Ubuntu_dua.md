---
title: "Cannot find Ubuntu 16.04 (Windows 7 and Ubuntu dual boot)"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by baali-ilyes on 2016-12-30
I have followed the regular instructions to install ubuntu 16.04 alongside windows 7 on a Dell T7600, the installations goes fine, when I restart the computer there is no Grub menu, I just enter to windows 7 directly. The boot is Legacy mode. I run boot-repair and here is the link to the report: [http://paste2.org/CZF0EB69](http://paste2.org/CZF0EB69). Thank you for the help in advance

---

### Post by ajgreeny on 2016-12-30
Which hard drive does your machine use as first boot priority as grub appears to be on sdb form some reason, and the windows bootloader on sda, so I assume sda is the first boot device.

Try changing the boot priority of your machine in the BIOS to sdb and with luck you should find that this second drive, with one NTFS partition shown in your output as
```
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 558.9 GiB, 600127266816 bytes, 1172123568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192 1,172,119,551 1,172,111,360   7 NTFS / exFAT / HPFS
```
may get you to the grub menu.

However the boot-repair output also says it will install grub on sdc, which makes more sense as it is your Ubuntu OS disk, so if booting from sdb is unsuccessful you may need to allow boot-repair to do its job.
However, I would avoid the default repair as it will put grub on all hard disks including the Windows disk, sda and in my opinion it is better to keep the Windows bootloader on sda, and put grub elsewhere, ie, sdc, for which you will need to make use of the Advanced option of boot-repair.

---

