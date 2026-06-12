---
title: "Grub can't boot ubuntu."
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Redundant Username on 2010-04-24
I used LVPM to transfer my Wubi install to my second drive, but I think Grub is set to boot from the first drive instead the second one.(the one that Grub is installed in) It keeps trying and failing to boot my Wubi on my first drive instead of the Ubuntu install it's own drive. Here is the bottom part of the menu.lst file on the second drive.```
## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.04 LTS, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title UnknownOS
root (hd1,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd1,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd1,2)
makeactive
chainloader +1
boot

``` I'll upload up a picture of my partitions in Gparted. Sdb is my first drive, and sda is my second drive

---

### Post by oldfred on 2010-04-24
It was my understanding that LVPM is not supported for the newer versions. It also used grub legacy which should work but we are now trying to use grub2. Some complain since grub2 is new and different.

I see several missing/wrong entries in you menu.lst. I do not know if it would be easier to try to edit or just reinstall grub and create a new menu.lst from scratch? And this assumes LVPM copied everything else ok.

This is a wubi style and need changing
root        ()/ubuntu/disks
to:
root        (hd0,1)

and this needs a UUID where XXX is:
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=[COLOR=DarkRed]XXXX[/COLOR]  ro quiet splash 

To get UUID
sudo blkid

One of my old entries:
title        Ubuntu 9.04, kernel 2.6.24-21-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=f9b2a783-78ba-4437-9bc5-9d8cfa86ff0c ro quiet splash irqpoll 
initrd        /boot/initrd.img-2.6.24-21-generic
savedefault
boot

---

### Post by Redundant Username on 2010-04-24
Thank you, it works now. I'm going to play with the Fstab now.

---

### Post by Redundant Username on 2010-04-24
I have a new problem. How do I point Vista's MBR to the second drive? I don't want to select drives every time I boot up. I still have my Wubi install, could I somehow point the Ubuntu boot up option to the second drive instead of the Wubi partition?

---

### Post by oldfred on 2010-04-25
You want to have Vista's boot in the MBR of the Vista drive and the grub in the MBR of the Ubuntu drive. Then in BIOS you boot the Ubuntu drive and it will also give you the option of booting windows. If the Ubuntu drive ever has problems you can still directly boot the windows drive with (f12 one time boot) or change BIOS to that drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also mount your wubi root.disk in your Ubuntu install if it did not copy everything you wanted over.

---

