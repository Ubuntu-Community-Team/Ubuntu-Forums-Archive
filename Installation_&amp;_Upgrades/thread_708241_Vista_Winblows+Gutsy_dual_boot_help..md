---
title: "Vista Winblows+Gutsy dual boot help."
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Mauler5858 on 2008-02-26
Ok here is the problem.

I have one sata hard drive which is where vista is installed with the vista mbr still intact.

I have an ata hard drive, hda1, which is where gutsy is located at.

For grub ive been trying to do:

rootnoverify (sd0)
savedefault
makeactive
chainloader +1

It will not boot.  Can anybody please help.

---

### Post by Pumalite on 2008-02-26
Windows is installed first, Ubuntu last. You also have the SATA+IDE problem

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)
From another thread:

I had something similar happening with a sata drive - try adding irqpoll as a boot option.

In grub, edit the boot option (there's a key to press in the grub menu - e? - it says which one at the bottom of the menu), go down to the kernel line and add "irqpoll" to the end of it. Hit B and you should boot.

---

### Post by Mauler5858 on 2008-02-26
Ive heard negative things about the irqpoll when it comes to system performance, but since its booting windows that fact should be negated anyway correct?

So:


rootnoverify (sd0)
irqpoll
savedefault
makeactive
chainloader +1

---

### Post by confused57 on 2008-02-26
> **Mauler5858 said:**
> Ive heard negative things about the irqpoll when it comes to system performance, but since its booting windows that fact should be negated anyway correct?

So:


rootnoverify (sd0)
irqpoll
savedefault
makeactive
chainloader +1

Have you tried something like?:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by Mauler5858 on 2008-02-26
Yes and its actually vista that im doing.  When i do that one it says ntldr not found.

---

### Post by confused57 on 2008-02-26
> **Mauler5858 said:**
> Yes and its actually vista that im doing.  When i do that one it says ntldr not found.
Post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
and the boot entries in your menu.lst:
```
gedit /boot/grub/menu.lst
```

---

### Post by Mauler5858 on 2008-02-26
Currently at work.  Will post back around 6:30est.

---

### Post by Mauler5858 on 2008-02-26
FDISK:


Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27e627e6

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825       14488    85658580   83  Linux
/dev/hda3           14489       14946     3678885    5  Extended
/dev/hda5           14489       14946     3678853+  82  Linux swap / Solaris

Disk /dev/hdb: 17.2 GB, 17247928320 bytes
255 heads, 63 sectors/track, 2096 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00005dda

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2096    16836088+   7  HPFS/NTFS

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d282

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       12549    70078464    7  HPFS/NTFS
/dev/sda3           12549       30516   144320512    7  HPFS/NTFS


GRUB:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b066430-165d-445f-813a-1accf0e26d1e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b066430-165d-445f-813a-1accf0e26d1e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
makeactive
chainloader	+1

title	Microsoft Windows Vista
rootnoverify (sd1,0)
savedefault
makeactive
chainloader +1

---

### Post by confused57 on 2008-02-26
You could try this entry for Vista:
```
title              Windows XP
root               (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

Device map may show your Vista drive as (hd2):
```
gedit /boot/grub/device.map
```

---

### Post by Mauler5858 on 2008-02-26
Just a couple of slight differences and it works:

title              Windows Vista
rootnoverify    (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1

Thanks for the help.

---

### Post by confused57 on 2008-02-26
Glad to help, good job on your part...sometimes rootnoverify works when just root doesn't...thanks for the update.

---

