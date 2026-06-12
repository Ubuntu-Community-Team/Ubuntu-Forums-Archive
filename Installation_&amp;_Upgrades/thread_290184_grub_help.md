---
title: "grub help"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by dhawk312 on 2006-10-31
I upgraded to edgy and I havent tried booting into Windows since I rarely use it.  Today I tried to boot in to my windows Xp partition but i got this "Error 12:  Invalid device requested" How can I fix this?

here is my grub menu list:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title		Microsoft Windows XP Home Edition
root		(hd0,4)
savedefault
makeactive
chainloader	+1

---

### Post by Herman on 2006-11-01
sudo fdisk -lu              dhawk312

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

__Device____________Boot______Start_________End______Blocks______Id______System
/dev/hda1________________________63___116680094____58340016_______5____Extended
/dev/hda4_________________116680095___117210239______265072+_____82____Linux swap / Solaris
/dev/hda5_____________*_________126____31680179____15840027_______7____HPFS/NTFS
/dev/hda6__________________31680243____73690154____21004956______83____Linux
/dev/hda7__________________73690218____95345774____10827778+_____83____Linux
/dev/hda8__________________95345838___116680094____10667128+_____83____Linux
```dhawk, I think your partitioning is rather unusual, but if you know what you are doing there is nothing wrong with it really.
Your partition number 1 is an extended partition, it has inside it your Windows NTFS partition and three linux partitions.
Then you have a swap area which is another primary partition.

A standard dual boot installation would have Windows as number1, then a Linux primary partition and an extended with a swap area (logical) inside it.

In order to give you the right kind of help, I'll need a little background information about why you chose that type of partitioning arrangement. I'll be back in a while and then I'll be able to help you more. 
Your partitioning is okay though, but it's just not standard, so I need to know more about why, that's all.

Regards, Herman :D

---

