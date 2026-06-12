---
title: "Unlinked boot drive"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by shickidyshade on 2008-10-31
On my laptop I have Windows XP installed and fc9. I was attempting to install ubuntu on a flash drive to use as a portable distro for computers around school etc. However the boot grub in sda is no longer linked to the grub in fedora. Attached is my fdisk -l

Code:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc232459c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5101        5125      200812+  83  Linux
/dev/sda3            5126        7296    17438557+  8e  Linux LVM

Any help would be appreciated

---

### Post by caljohnsmith on 2008-10-31
Probably what happened is that you unintentionally installed Grub to the MBR (Master Boot Record) of sda when you installed Ubuntu to your flash drive. You should be able to use these steps to restore Fedora's control over Grub in the MBR of sda:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Fedora partition (or /boot partition if you have one) in the form of (hd0,X) where X is a number, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hd0,X)
grub> setup (hd0)
grub> quit
```
Give that a shot and let me know how it goes.

---

### Post by shickidyshade on 2008-10-31
That worked great

Thank you for your help, I just got ubuntu added into my Fedora grub.conf and am really excited to have it on my computer again.


Shade

---

### Post by caljohnsmith on 2008-11-01
Glad it worked OK; cheers and have fun in LinuxLand. :)

---

