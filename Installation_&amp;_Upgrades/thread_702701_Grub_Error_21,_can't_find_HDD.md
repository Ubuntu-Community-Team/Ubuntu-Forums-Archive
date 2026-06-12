---
title: "Grub Error 21, can't find HDD?"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Intolucidity on 2008-02-20
Hi there, I am currently only able to run off the Ubuntu live cd though the install proceeded without any problems.
When I boot off the hard drive, I receive an error 21 from Grub, which I believe is a problem with finding where the kernel is installed to?

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel	      /boot/vmlinuz-2.6.22-14-generic root=UUID=6cfb8d4d-4de9-415b-a686-7698db0b7cd7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel	       /boot/vmlinuz-2.6.22-14-generic root=UUID=6cfb8d4d-4de9-415b-a686-7698db0b7cd7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel	       /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


and from fdisk -l
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84965911

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         831     6670336   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         832        6909    48821535   83  Linux
/dev/sda3            6910        7517     4883760   82  Linux swap / Solaris


So it appears that the partition is fine and exists, but Grub is having problems with it?
I am kinda new at this, but any help would be appreciated.

---

### Post by jocheem67 on 2008-02-20
[HTML]GRUB Error 21 problem solved 
thanks to David Balazic for pointing me in the right direction!
i changed the CMOS settings to detect the HD's in my system...
this is what i did:
entered Standard CMOS Setup

set the Primary Master to:

    Type = User,  Mode = LBA

by scrolling through the options

 

then set the Primary Slave to:

    Type = Auto, Mode = Auto[/HTML]

It seems that the error 21 is bios-related, you should check out the way your harddisk is registered  in the bios, grub uses that information for it's own hardware recognition....

 



 

tom

---

### Post by dstew on 2008-02-20
When do you get the error? Do you get the error, without any explanation, right at the start of the grub boot, or do you get it after you select a menu item? An error without any explanation is a stage1.5 error, and an error with an explanation like "Error 21 : Selected disk does not exist" after you choose a menu item is a stage2 error. They need to be handled differently.

Usually, a stage1.5 error means you need to reinstall grub. A stage2 error means you have to adjust the menu.lst file.

---

### Post by Pumalite on 2008-02-20
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

