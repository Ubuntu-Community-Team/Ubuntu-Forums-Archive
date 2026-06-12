---
title: "boot up problems after install"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by Sungbob on 2005-04-13
Hi everybody,
I had just installed hoary into my computer. However on the first reboot after install i get this msg "extended partition not bootable". I have no idea what this problem is nor where to begin in solving this problem. I'll put up a copy of my fdisk/menu.lst to see if this holds any problems.

Menu.lst:
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot

fdisk:
Disk /dev/hde: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3644    29270398+  83  Linux
/dev/hde2            3645        3737      747022+   5  Extended
/dev/hde5            3645        3737      746991   82  Linux swap

Any pointers would be much appreciated.
Sungbob Linux Newbie.

P.S. I was able to install/run warty/hoary once before untill something happened not sure. Could it be something with my bios ?

---

