---
title: "[SOLVED] Dual Boot reinstall GRUB problem"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by pepito9 on 2008-06-04
Hi all,
here. my setup:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b5d652c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       91201   732564000    f  W95 Ext'd (LBA)
/dev/sda2               1           1        8001    7  HPFS/NTFS
/dev/sda5               2       91201   732563968+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdabde656

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       36483   293041665    f  W95 Ext'd (LBA)
/dev/sdb5               2       36483   293041633+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24502450

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdc2           12749       24792    96743430    5  Extended
/dev/sdc5           12749       24414    93707113+  83  Linux
/dev/sdc6           24415       24792     3036253+  82  Linux swap / Solaris

Disk /dev/sdd: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004e0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         126     1007584+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

I previously had a working double boot with XP and i486 Ubuntu, both setup on SDC, i uninstalled Ubuntu and deleted the partitions, did a fixmbr from windows and installed i386 Ubuntu in the same location.

The problem is that i can't boot into Ubuntu, only directly to XP Grub does not load i suppose the fixmbr did not  work.

If i change the boot order from SDC to SDA then i get a Grub error 21

any ideas?

---

### Post by melrom on 2008-06-04
Do you have an install CD available?? If so, try to mount the linux partition and edit menu.lst for grub.

-Melissa

---

### Post by melrom on 2008-06-04
as an alternative, [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) is your best friend. =)

Also, check out the advice people gave me on this post: [http://ubuntuforums.org/showthread.php?t=809403](http://ubuntuforums.org/showthread.php?t=809403)

I ended up doing a roundabout fix, because I couldn't download a super grub disk while at work, but their advice was very helpful.

---

### Post by dstew on 2008-06-04
My guess is that when you did fixmbr, the Windows boot loader went into the MBR of /dev/sdc, so when you set your BIOS to boot that disk, it goes right to Windows. But, your previous Ubuntu installation put grub in the MBR of /dev/sda, so when you set your BIOS to boot that disk, grub starts. It seems that you did not install grub with your new installation. So, since you re-partitioned, the grub boot loader can no longer find its stage2, and you get the error. The grub boot loader is "hard-wired" to find its stage2 file when it is installed. It cannot search for it. So, if you repartiton, grub is lost.

If you want to fix your system so that it dual-boots, you will need to re-install grub. First, decide which hard disk you want to have as your boot disk in BIOS, and set your BIOS that way. It really doesn't matter, but it is best to boot the same disk that has your Ubuntu system on it I think. 

Once you have set your BIOS to boot the disk you want, boot an Ubuntu Live CD. Open a terminal window and enter grub. That should get you the grub shell program, with the grub> prompt. At the grub prompt enter```
find /boot/grub/stage2[code]It should return a partition number in grub-form, like (hd2,4). Whatever it returns, use as the argument of the root statement:[code]root (hd2,4)
```Then, install the boot loader into the disk that you designated to boot. Usually, this will be numbered as 0 by the BIOS:```
setup (hd0)
```Then, remove the Live CD and reboot.

---

### Post by meierfra. on 2008-06-04
> If i change the boot order from SDC

Since you are booting   from SDC, which is the Ubuntu drive, you need

```

sudo grub
root (hd2,4)  # Output from "find /boot/grub/stage2
setup (hd2)          #  First number from the output
quit

```

---

### Post by pepito9 on 2008-06-04
Here´s the latest.
I can log into my new Ubuntu install by editing the Grub menu on startup, it points to (hd2,5) i change it to  (hd0,4) and i´m in

once inside the result given by # find /boot/grub/stage2 is (hd1,4)

Then i use 

```

root (hd1,4)
setup (hd1)
quit

```

reboot

on reboot i have to edit the grub menu again because nothing has changed, so i try a different approach, i use the info that works on startup instead of the one given by the find command, here is what i do and get:

```
grub> find /boot/grub/stage2
 (hd1,4)

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

```

by the way here&#347; menu.lst

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d08522a9-0cdf-4b89-9b04-a816ee9bb14b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d08522a9-0cdf-4b89-9b04-a816ee9bb14b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Thanks,

Diego

---

### Post by pepito9 on 2008-06-04
Got it!

Of course the answer was right there, too bad i was not looking.

i edited menu.lst to the values that worked manually on startup.

Again, Thanks to all.

---

