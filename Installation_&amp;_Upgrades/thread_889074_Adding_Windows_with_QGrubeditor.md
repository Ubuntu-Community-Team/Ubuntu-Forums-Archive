---
title: "Adding Windows with QGrubeditor"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by conradcliff on 2008-08-13
Hey all,

I've recently decided to try another go add Ubuntu and decided to install it on a 20gig partition right next to my windows install. My problem is that when the grub boot loader came up after the install it had no option for booting into windows.

I went ahead and installed QGrubeditor from the repository and attempted to add windows to the grub with my limited knowledge, but whenever I try to boot windows it gives me the error: "error 13: Invalid or unsupported executable format"

Here is what the menu input tab has listed after my attempts:

timeout 10
hiddenmenu

title Windows XP
root (hd0,6)
chainloader +1
makeactive

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet


As always, any help is greatly appreciated..you guys rock!

---

### Post by mvdberg112 on 2008-08-13
Note: you are using QGrubeditor, which I have not used myself. From your question I guess that it used the same syntax and format at Grub. That is what I answer from. To be save, you might just use Grub.

It says:> title Windows XP
root (hd0,6)
chainloader +1
makeactive

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quietSo in both entries it says "root(hd0,6)".
This would refer both to partition 6 on harddisk 0 (the first harddisk).
This does not seem right.
If you have no idea what the right one should be, then try to create mutliple entries, e.g. > title Windows XP hd0,1
root (hd0,1)
chainloader +1
makeactive

title Windows XP hd0,2
root (hd0,2)
chainloader +1
makeactive
.
.
.
.
title Windows XP hd1,1
root (hd1,1)
chainloader +1
makeactiveIf you have only one HDD, and you do not boot from CD or USB at all, then hd0,x should suffice. The one that works is the good one. 

The right way of find out would be to look in the partition manager of course.
I was very much helped by the following manual when I had grub problems:
[http://www.gnu.org/software/grub/manual/grub.html#Device-map](http://www.gnu.org/software/grub/manual/grub.html#Device-map)
Let us know your findings and final solution; if it works, it helps others. If it didn't work, we try to help you again.

---

### Post by conradcliff on 2008-08-14
Thanks for the reply, I took your advice and edited the grub. I had to use the command: *sudo nano /boot/grub/menu.lst* because Qgrubeditor would not allow me to apply my changes to the partitions. Here is what the current menu.lst file looks like (I'll drop the whole thing in just for good measure):

timeout 10
hiddenmenu

title Windows XP hd0,0
root (hd0,0)
chainloader +1
makeactive

title Windows XP hd0,1
root (hd0,1)
chainloader +1
makeactive

title Windows XP hd0,2
root (hd0,2)
chainloader +1
makeactive

title Windows XP hd0,3
root (hd0,3)
chainloader +1
makeactive

title Windows XP hd0,4
root (hd0,4)
chainloader +1
makeactive

title Windows XP hd0,5
root (hd0,5)
chainloader +1
makeactive

title Windows XP
root (hd0,6)
chainloader +1
makeactive

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4747ecc2-e925-4b74-ab4f-251e747ad64e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false




And here are the errors I get in order of trying to boot from each windows line:

Error 12: Invalid device requested
Error 22: No such partition
Error 22: No such partition
Error 22: No such partition
Error 12: Invalid device requested
Error 13: Invalid or unsupported executable format
Error 13: Invalid or unsupported executable format


Not sure if there is some other file I need to edit or what aside from the grub menu.lst being that I'm a newby and all but I'm sure someone here can help me out! :)

Also, the system keeps crashing due to kernel panic, but that's an issue for another thread...

Thanks again for any help!

---

### Post by cariboo on 2008-08-14
It might be alittle easier for us to diagnose your problem if you were to run in a terminal:

```
sudo fdisk -l
```

This will create a list of your hard drives and partitions. post the output in your next post.

Jim

---

### Post by conradcliff on 2008-08-14
Thanks for the reply cariboo, 

Here is the output for the fdisk:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9c586c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       20023   160826715    f  W95 Ext'd (LBA)
/dev/sda5               2        2557    20531038+   7  HPFS/NTFS
/dev/sda6           19778       20023     1975963+  82  Linux swap / Solaris
/dev/sda7            2558        5113    20531038+  83  Linux
/dev/sda8            5114       19777   117788548+  83  Linux

Partition table entries are not in disk order


Hopefully this will help..thanks again!

---

### Post by conradcliff on 2008-08-19
bump

---

