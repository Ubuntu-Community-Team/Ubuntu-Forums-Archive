---
title: "Change partitioning setup"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by MaximusTG on 2007-09-10
My current situation:

3 partitions,

1st: Windows XP
2nd: Windows data partition
3rd: Ubuntu Feisty

I've been using Ubuntu since a couple of months now, and I would like to completely remove Windows now. However, I would like to keep my Ubuntu installation. How would I go about this? I suppose I should make a disk image of the Ubuntu partition(what program?), then start a live cd, remove all partitions, and restore the Ubuntu image to one new partition (and enlarge it to fill the entire disk) and then reinstall Grub. Am I forgetting anything? Would this work?

---

### Post by Pumalite on 2007-09-10
Nothing so complicated. You could Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), erase windows, format that partion to ext3 and then re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
But better post: sudo fdisk -lu to make sure I'm giving you the right advise.

---

### Post by MaximusTG on 2007-09-10
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8177084     4088511   12  Compaq diagnostics
/dev/sda2   *     8177085    62187614    27005265    c  W95 FAT32 (LBA)
/dev/sda3        62187615    93000284    15406335    7  HPFS/NTFS
/dev/sda4        93000285   117210239    12104977+   f  W95 Ext'd (LBA)
/dev/sda5   *    93000348   116085689    11542671   83  Linux
/dev/sda6       116085753   117210239      562243+  82  Linux swap / Solaris

I forgot to mention that the first partition is a rescue partition (it's an Acer laptop) and I would like to keep it. Rearranging or removing wouldn't damage Grub would it? Isn't it located between 1-63?

But when I would erase those windows partitions, and format them as ext3, how would I use them? Programs get installed to /usr/bin don't they? I don't understand how I would use the extra space.. Isn't it easier as one large partition?

---

### Post by Pumalite on 2007-09-10
Device Boot Start End Blocks Id System
/dev/sda1 63 8177084 4088511 12 Compaq diagnostics
/dev/sda2 * 8177085 62187614 27005265 c W95 FAT32 (LBA)
/dev/sda3 62187615 93000284 15406335 7 HPFS/NTFS
/dev/sda4 93000285 117210239 12104977+ f W95 Ext'd (LBA)
/dev/sda5 * 93000348 116085689 11542671 83 Linux
/dev/sda6 116085753 117210239 562243+ 82 Linux swap / Solaris

You have 6 partitions: your diagnostics is a problem but not unsurmountable
sda2 is a ? to me. It has a bootflag, but is not XP. XP is in sda3
sda4 is another ?
sda5 is your Ubuntu; sda6 is swap. Could you clarify sda2 and sda4?

---

### Post by MaximusTG on 2007-09-10
Well, 

sda2 IS XP, Acer delivers this laptop (acer 3680) with a fat32 xp partition, and a DATA partition (also fat32)I converted the Data partition to NTFS (before I installed ubuntu)

sda4, is, as I see it, an extended partition, that holds sda5 & sda6...

---

### Post by Pumalite on 2007-09-10
sda2 is your target then. You can use to hold your stuff from Ubuntu or change your /home to it if you want.

---

### Post by MaximusTG on 2007-09-16
So, I've been doing some research, and this is what I found. If I were to follow this manual:

[http://www.arsgeek.com/?p=637](http://www.arsgeek.com/?p=637) 

to make a complete copy of my filesystem, then start the LiveCD, and reinstall the machine, using the entire harddisk as 1 partition (but keeping the Acer restore partition). Then restore the backup as explained in the link above, would the only difference be that I would have to change my Grub menu.lst in /boot/grub ? 

It is now:

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Would it have to be:

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=adec27d2-175b-4917-9278-0bf4c5fac19b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (this is the restore partition)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Would this work?

---

### Post by Pumalite on 2007-09-16
I like this idea better:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

