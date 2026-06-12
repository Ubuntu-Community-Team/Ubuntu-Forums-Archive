---
title: "Multiple Ubuntu - how to delete and move grub"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by honkenhg on 2008-05-06
Hi there,

I have a laptop (Thinkpad T61) with Windows Vista and two Ubuntu installations - initially both 7.10 but 32 and 64 Bit. Now I updated the 64Bit to 8.04 and besides some issues with the nvidia driver and screen resolution everything worked like a thread. Since there is no need for me to use the 32Bit Ubuntu anymore, I want to gain back that space and merge the partition with a ntfs partition that I use for shared access to data from Vista and Ubuntu.

sda1 - Vista
sda4 - Ubuntu 7.10 32Bit (active grub)
sda6 - Ubuntu 8.04 64Bit

Not on that particular notebook, so if required I'll post detail fstab, fdisk or menu.lst later. Just let me know.

My issue is, that grub is installed from that 32Bit Ubuntu. And from reading through forums and web sites it seems I will have to re-install it from my 64Bit Ubuntu. So far so good, but what will happen when I am merging the partitions? The 64Bit is on sda6 and the 32Bit which I want to merge is on sda4, therefore all the references afterwards won't work anymore. 

That at least is my assumption and worry, so does anybody know a way to get around possible issues with not being able to boot the two remaining OS?

Thanks in advance
Daniel
---
Lenovo T61, 3GB RAM, 120GB Harddisk, Dual Core 2.2Ghz --> happy Ubuntu Runner

---

### Post by honkenhg on 2008-05-07
I investigated a bit further and following process appears quite logical to me:

1. grub-install from the running 64Bit Ubuntu (the one that will stay).
2. backup the old menu.lst
3. do a fdisk -l and note the current setup
4. use gparted to merge partitions of to be deleted 32Bit Ubuntu with NTFS
5. do a fdisk -l again and adopt the menu.lst to reflect changes (do not use unique identifiers but drive descriptors sda1,sda2, sdaX)

btw, here is the current fdisk -l output:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         815     6545408   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         816        6424    45050040    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10248       14594    34905088    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            6424       10248    30716280    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            6424        8248    14651248+  83  Linux
/dev/sda6            8248        8613     2933248+  82  Linux swap / Solaris
/dev/sda7            8613       10248    13131688+  83  Linux

Partition table entries are not in disk order

```
As you can see, the entries from my first post are not correct. From now on please refer to the information from fdisk -l

And here the current menu.lst from 32Bit ubuntu:
```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1c27b435-49fa-4923-ad98-f9cc85ba0481 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1c27b435-49fa-4923-ad98-f9cc85ba0481 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (Rescue&Recovery)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04 64Bit (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dddb5b8e-1531-4a10-8479-b146c59830c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04 64Bit (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dddb5b8e-1531-4a10-8479-b146c59830c6 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Anyone with experience in this area? Or just a comment on the proposed process? Any input is appreciated since I'm actually going to start the procedure during the next couple of days.

---

### Post by honkenhg on 2008-05-08
Ok, I found out it wasn't exactly as i described here, because it wasn't the 32Bit I wanted to delete, but the 64Bit. So at the end it has been fairly easy, though I thought it might be interesting for someone else, so posted the description as it would have helped myself:

[http://atentia.wordpress.com/2008/05/08/how-to-update-grub-while-merge-partitions/](http://atentia.wordpress.com/2008/05/08/how-to-update-grub-while-merge-partitions/)

Daniel

---

