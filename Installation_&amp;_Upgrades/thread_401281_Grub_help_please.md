---
title: "Grub help please"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by scotty026 on 2007-04-04
I have just did a fresh install of Ubuntu :) but get error code 17 when booting up grub , can any one help with this problem.

Grub file 

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot


fstab output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
#
/dev/sda5       none            swap    sw              0       0
#
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
#
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by geirha on 2007-04-04
I had a similar issue. I have three harddrives; hda, sda and sdb. I installed ubuntu on hda1 and ubuntu configured grub with root (hd0,0) however, (hd0,0) turned out to be sda1 while hda1 was (hd2,0).

If you have more than one harddrive, this could be your case as well. So try this:
1. Turn on you machine
2. When it gets to the boot menu, select **Ubuntu, kernel 2.6.17-10-generic** and hit 'e' to edit it.
3. Select the root-line **root (hd0,0)** and hit 'e' to edit it
4. Change it to **root (hd1,0)** or **root (hd2,0)** and then hit 'b' to boot

if this works, make sure to edit /boot/grub/menu.lst, and change the line ```
# groot (hd0,0)
``` to ```
# groot (hd1,0)
``` (or whichever was the correct one. DON'T remove the '#' at the beginning of the line.)
 Then running ```
sudo update-grub
``` should fix it permanentely.

---

