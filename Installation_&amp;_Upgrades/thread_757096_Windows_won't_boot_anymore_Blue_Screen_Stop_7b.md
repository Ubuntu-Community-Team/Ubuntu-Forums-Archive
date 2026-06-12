---
title: "Windows won't boot anymore Blue Screen Stop 7b"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by gjlubbertsen on 2008-04-16
Hi,

i'v installed Ubunto 8.04 next to my windows installation. using grub as my bootloader.
Ubunto runs fine but windows won't boot anymore. 

Just after the logo page (windows XP) and tree stripes in the progress bar it stops with an blue screen. Error is STOP 0x0007B (these errors have somthing to do with the drive or the drive controller)

First thing i tried is to uninstall unbunto. And reinstall the windows loader in the MBR. This fixed te problem. So i reinstalled Ubunto again. Which resulted in the same blue screen.

what is wrong with my drive? of partitioning?

current configuration:
[IMG]http://lubbertsen.com/tweakerspost/diskpart.jpg[/IMG]\

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       14593    91618695    f  W95 Ext'd (LBA)
/dev/sda5            3188        5737    20482843+   7  HPFS/NTFS
/dev/sda6            5738       12498    54307701    7  HPFS/NTFS
/dev/sda7           12499       14499    16073001   83  Linux
/dev/sda8           14500       14593      755023+  82  Linux swap / Solaris


```

menu.lst
```

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
makeactive
chainloader	+1

```

what is wrong with this configuration?

Tnx a lot!

---

### Post by Pumalite on 2008-04-16
Maybe add 'savedefault' after 'rootnoverify'

---

### Post by gjlubbertsen on 2008-04-17
i gues not:
[http://www.gnu.org/software/grub/manual/html_node/savedefault.html](http://www.gnu.org/software/grub/manual/html_node/savedefault.html)

please help me anyone.

---

