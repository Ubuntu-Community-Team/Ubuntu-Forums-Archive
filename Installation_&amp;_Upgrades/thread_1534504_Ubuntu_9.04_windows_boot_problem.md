---
title: "Ubuntu 9.04 windows boot problem"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Servando Mendoza on 2010-07-19
Hello everybody.

I have installed Ubuntu 9.04 after installed Win XP using the asisted partition tool i guess that it did the partition job for me, everything worked great but when the grub started and I select my Windows XP partition it tells an error reading the HD.

Can somebody help me, how can i fix this problem?

My partitions:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1e04f8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13415   107755956    7  HPFS/NTFS
/dev/sda2           13416       14593     9462285    5  Extended
/dev/sda5           13416       14537     9012433+  83  Linux
/dev/sda6           14538       14593      449788+  82  Linux swap / Solaris

my grub:

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e9897f59-3f31-444e-b7dd-3f6b755ebf6d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e9897f59-3f31-444e-b7dd-3f6b755ebf6d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e9897f59-3f31-444e-b7dd-3f6b755ebf6d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e9897f59-3f31-444e-b7dd-3f6b755ebf6d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e9897f59-3f31-444e-b7dd-3f6b755ebf6d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by Old_Grey_Wolf on 2010-07-19
This may help. Enter```
sudo update-grub
```in a terminal. Then reboot.

---

