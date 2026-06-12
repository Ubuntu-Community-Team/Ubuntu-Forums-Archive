---
title: "Need help with grub getting windows to boot"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Mordrukk on 2007-11-28
I'm having a tough time booting to windows from grub, can't seem to get things right.  I just recently managed to get ubuntu to boot from grub, as it was pointed at the wrong partition.  I believe this is the same problem with the windows partition, as I can see the windows piece fine through ubuntu -- all files are still intact.

here's my fdisk -l

```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x238da564

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdb2           16709       24462    62284005   83  Linux
/dev/sdb3           24463       24792     2650725    f  W95 Ext'd (LBA)
/dev/sdb5           24463       24792     2650693+  82  Linux swap / Solaris

```

what's interesting here is that you can see my linux partition is on sdb2, which you would assume to be (hd1,1) since sdb looks like the 2nd drive located.  however, when I boot the order of the drives is reversed, and the 2nd drive (sdb above) must become sda because I can only boot to ubuntu by doing:

root (hd0,1)

here is my menu.lst info:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c9902129-4cdd-46f3-b017-a51d9993bac1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c9902129-4cdd-46f3-b017-a51d9993bac1 ro single
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
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

again, the ubuntu part seems fine now, but can anyone help me out with the windows one?

---

### Post by confused57 on 2007-11-28
If /dev/sda1 is your Windows drive, then this should work:
```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

If Windows is sdb1, then:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Mordrukk on 2007-11-28
Dude, you rule the earth!

The second one you listed did the trick! THANK YOU!!

---

