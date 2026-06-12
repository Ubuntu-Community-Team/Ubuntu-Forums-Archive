---
title: "error booting windows xp from grub"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by crazy_jutt on 2007-12-12
I have installed ubuntu on my desktop where i have two hard drives ( both SATA ) 
I can boot ubuntu fine from grub but can not boot windows. 

Hard Drives are listed in BIOS as 

IDE Channel 2 : Master Disk ( This is where i installed ubuntu, Size 160 GB )
IDE Channel 3 : Master Disk ( This is where i installed windows xp pro, Size 300 GB )
=====================================================
Output from fdisk is as below : 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00089fe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306937889   153468913+  83  Linux
/dev/sda2       306937890   312576704     2819407+   5  Extended
/dev/sda5       306937953   312576704     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15831583

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   586083329   293041633+   7  HPFS/NTFS
===============================================

my menu.lst file is below
====================================================
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b032b5aa-510e-4d47-9f30-24a36265119a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b032b5aa-510e-4d47-9f30-24a36265119a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
===================================================

additional information :

From inside Ubuntu session i get following information
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)

when i try to run setup (hd0) , i get error
=====================================
From inside Grub menu during boot time, i get following information 

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)

When i edit my grub entry for windows xp and change root ( hd1,0) to root (hd0,0) it goes to console with message  "starting up" and then stay there forever 

When i insert ubuntu live CD and choose the option to boot from first hard disk, my computer boots in windows xp without any issues

What is wrong in my system ?

---

### Post by Pumalite on 2007-12-12
What was the boot order when you installed? Or did you install XP last?

---

### Post by dabl on 2007-12-12
Use GParted to turn off the "boot" flag on the Linux partition.

---

### Post by crazy_jutt on 2007-12-12
thanks for help 

Removing boot flag from Linux partition did not help 
XP is installed already. I installed SUSE enterprise server earlier and then installed XP. that was a year ago

What could be wrong in my system ?

---

### Post by Pumalite on 2007-12-12
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by crazy_jutt on 2007-12-12
Thanks for lot for everyone's help

It finally worked when i changed hard disk boot priority 

[http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority](http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority)

---

