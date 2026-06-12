---
title: "Gutsy upgrade problems and Nvidia confusion"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by elrod on 2007-11-12
Hi, fairly new to Ubuntu having come from Gentoo, which should explain a lot. ;-( 

Anyway, Upgraded Feisty to Gusty but that will not boot on my laptop using the default kernel (2.6.22). Was able to boot using 2.6.20-16 but the nvidia driver does not load. 

[ 2679.964000] NVRM: API mismatch: the client has the version 1.0-9639, but
[ 2679.964000] NVRM: this kernel module has the version 1.0-9755.  Please

That driver version does not show up in the package manager.

This would probably all be simple if I understood apt better but alas....

Thanks for any pointers:

1) how to get the nvidia version that works with the kernel my laptop likes.
2) How to (or should i?)  fiddle with the kernel build options to try and get .22 working with my laptop. It's an Acer 9300 which ran just fine under Feisty.

Thanks

---

### Post by Pumalite on 2007-11-12
Lets find out where your Gutsy kernel is first (?): post

sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by elrod on 2007-11-12
fdisk -lu:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa025a025

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16386299     8193118+  12  Compaq diagnostics
/dev/sda2   *    16386300    79198142    31405921+   7  HPFS/NTFS
/dev/sda3        79200255   129965849    25382797+   f  W95 Ext'd (LBA)
/dev/sda4       129965850   234436544    52235347+  83  Linux
/dev/sda5        79200256   125417471    23108608    7  HPFS/NTFS
/dev/sda6       125419518   129965849     2273166   82  Linux swap / Solaris

cat:

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=f7d4b10f-a10a-411f-948a-a643c72908b6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-386
quiet

title           Ubuntu 7.10, kernel Eric Debug
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-386 root=/dev/sda4
initrd          /boot/initrd.img-2.6.22-14-386
quiet
acpi=off

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=f7d4b10f-a10a-411f-948a-a643c72908b6 ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f7d4b10f-a10a-411f-948a-a643c72908b6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f7d4b10f-a10a-411f-948a-a643c72908b6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

[B]title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f7d4b10f-a10a-411f-948a-a643c72908b6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet[/B]

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f7d4b10f-a10a-411f-948a-a643c72908b6 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

---

### Post by elrod on 2007-11-14
Can anyone help?

---

### Post by Pumalite on 2007-11-14
I'd comment out all the instances of Feisty in menu.lst, save, exit and reboot. Backup your menu.lst first.

---

### Post by elrod on 2007-11-14
But the only kernel that will boot is the .20 one. 
I think that's what you mean to comment out? Doesnt sound good. ;-)

Is there some way I can just get the correct version of the nvidia drive (9755) for the kernel which boots?
Then wait till whatever bug in .22 is biting me to be resolved.

---

### Post by hosk on 2007-11-14
You could try switching out your nvidia for the nvidia-glx-new or the nvidia-glx-legacy drivers, depending on what your card is?

---

