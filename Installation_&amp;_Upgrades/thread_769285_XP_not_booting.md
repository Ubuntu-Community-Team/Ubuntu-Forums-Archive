---
title: "XP not booting"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by pwolschen on 2008-04-26
I installed ubuntu 8.04 on my computer running XP. i wanted to make it dual boot. When i start the computer it gives me an option between linux and XP. linux works fine but when i attempt to start windows nothing happens. This is what sudo fdisk -l brings up. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14193   114005241    7  HPFS/NTFS
/dev/sda2           29253       30401     9223200    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           14194       29252   120961417+   5  Extended
/dev/sda5           14194       28899   118125913+  83  Linux
/dev/sda6           28900       29252     2835441   82  Linux swap / Solaris

What can i do to fix this?

---

### Post by Pumalite on 2008-04-26
Post:
cat /boot/grub/menu.lst

---

### Post by pwolschen on 2008-04-26
> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4e1c94aa-609f-4536-adae-5b232c9651c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4e1c94aa-609f-4536-adae-5b232c9651c5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Thats what it says at the end

---

### Post by Pumalite on 2008-04-26
You seem to have a Partition Table problem. Test with TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

