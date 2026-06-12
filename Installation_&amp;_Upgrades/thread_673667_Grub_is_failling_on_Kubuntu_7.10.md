---
title: "Grub is failling on Kubuntu 7.10"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by abrazafi on 2008-01-20
Hi All,

I finished installing kubuntu 7.10 over the 6.06 LTS ... 
Everything seems work smoothly and after rebooting,
got the grub menu and choose the rigth option...
got the following error message,
     ERROR 17: cannot mount selected partition

My system have 3 Hard Disks:
    -1st HD, windows XP installed
    -2nd HD, storage disk
    - 3rd HD, the linux partition which works fine with kubuntu 6.06 LTS
       more than 1 year now ...

Any help would be appreciated !

Many thanks,
Abdon.

---

### Post by torgrot on 2008-01-20
Post the output of 
 fdisk -l   that is a "lower case L"
and a copy of menu.lst

torgrot

---

### Post by abrazafi on 2008-01-21
Thanks Torgot,

As per requested ...

root>fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38913   210170362+   5  Extended
/dev/sda5           12749       38913   210170331    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38156   306488038+  83  Linux
/dev/sdc2           38157       38913     6080602+   5  Extended
/dev/sdc5           38157       38913     6080571   82  Linux swap / Solaris


--- and the file /boot/grub/menu.lst


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by torgrot on 2008-01-22
In your menu.lst file change the Ubuntu entries ```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd2,0)
kernel /boot/memtest86+.bin
quiet

```
Sorry about the delay, I got kind of busy.

torgrot

---

### Post by abrazafi on 2008-01-23
Hi,

Still not working .... 
After booting with recover mode, the following line is NOT coorect 

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash

I got the following message:

Alert! /dev/hda1 does not exist. Dropping to a shell

I did change to root=/dev/sdc1, same alert message:

Alert! /dev/sdc1 does not exist. Dropping to a shell

When the system is starting, kubuntu splash and freezing at the begening,
means that the grub is looking for the linux kernel hard disk.

==> means still NOT working.

What alternatives do I have:
 - reformat and re-install again ?
 - go back to kubuntu 6.06 LTS ?
 - use lilo instead grub ?

Thanks for your helps,
Abdon.

---

### Post by abrazafi on 2008-02-06
I just re-install again everything from scratch ...
I put Windows and /boot and swap on the first 
Hard Disk (HD) and seems working fine now.

Only pb is Windows XP tried to put/install some windows files 
on the 2nd and then 3rd HD (non formatted partition's) -
really nasty, I had to re-format them, with special tool, after while.
The Disk Manager, from kubuntu is not able to reformat them ...

Anyway, next time, I'll try to avoid my linux boot partition on the
2nd or  3rd HD.

Many thanks,
Abdon.

---

