---
title: "Grub error 17 and my solution"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by sobranko on 2008-10-31
This is from memory so it is not 100% accurate.

I installed ubuntu v8.04 (from LiveUSB) on computer with 1 IDE disk and 2 SATA disks, one SATA disk was new and not formatted so i installed ubuntu on it. This computer has windows installed on IDE disk and had linux (openSUSE) installed previously but i removed it completely (formatted disks and restored windows MBR).

Problem #1:
No grub on primary boot disk - only windows bootloader there which started up Windows.
Solution #1:
I tried to manually select disk - first i tried SATA disk where ubuntu is installed - no luck, so i tried second SATA disk - grub was there but -

Problem #2:
Grub loading ... bla bla
...
Grub error 17!
Solution:
booted Ubuntu from LiveUSB and i checked /boot/grub/menu.lst and /boot/grub/device.map. Here is listing from device.map:
```

(hd0)	/dev/sda    # windows formatted SATA disk
(hd1)	/dev/sdb    # ubuntu formatted SATA disk
(hd2)	/dev/sdc    # windows IDE disk with C:\WINDOWS

```
Here is listing from menu.lst:
```

# this is for ubuntu - there are more ubuntu entries but not needed for 
# this example
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=blabla ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
...
# and for windows, autmatically generated
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```
And here is fdisk -l dump:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5450842d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       16193    68629680    7  HPFS/NTFS
/dev/sda3           16194       19457    26218080    f  W95 Ext'd (LBA)
/dev/sda5           16194       19457    26218048+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00013a7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2445    19639431   83  Linux
/dev/sdb2            2446       12171    78124095   83  Linux
/dev/sdb3           12172       12657     3903795   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafbf6403

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdc2            5100       10198    40957717+   7  HPFS/NTFS
/dev/sdc3           10199       14593    35302837+   f  W95 Ext'd (LBA)
/dev/sdc5           10199       14593    35302806    7  HPFS/NTFS

```

Grub was installed on hd0, which is windows SATA disk, i didnt like this so i installed it on hd1 where Ubuntu is installed, i switched root to hd1,0. New menu lst is:
```

# for ubuntu
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3614f80e-8e16-4fd7-8ccd-a5d97247dd82 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
....
# for windows, remained same
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

I restarted computer and changed disk boot priorities so disk hd1 (Ubuntu SATA disk) is first and ... 
yay i got ubuntu menu ... but -

Problem #3:
If i tried any ubuntu menu entry i got:
```

Error 17: Cannot mount selected volume.

```
on other hand windows works like a charm
i knew i was getting close...
Solution:
i tried e option from grub menu and edited line
```

root (hd1,0) 

```
to
```

root (hd0,0)

```

and it worked ... !!!!
But why???
Theory: 
grub sees disks in boot priority order, ubuntu sees disks in some other order.
Proof:
i changed windows disk from 3th to 2nd place in boot priorities and broke grub. Grub failed to load windows with message 
```

NTDLR not found

```
but when i edited grub to root (hd1, 0) and replaced hd2 with hd1 in map lines windows loaded successfully.

I hope this helps you.

---

