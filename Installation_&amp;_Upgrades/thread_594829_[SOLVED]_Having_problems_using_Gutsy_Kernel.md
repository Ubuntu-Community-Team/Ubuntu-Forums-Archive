---
title: "[SOLVED] Having problems using Gutsy Kernel"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by ossi on 2007-10-28
Hi!

I upgraded from Edgy to Gutsy on my Kubuntu Laptop. My harddisk is on /dev/hdb while my Discdrive has to be on /dev/hda for hardware reasons. Anyway the new kernel does not boot, even if I edit the boot device from the Grub entry to /dev/hdb instead of /dev/hda.

What is very funny is, that if I edit the Boot directory entry of the Edgy Kernel to /dev/hdb Kubuntu boots without pain. The same method does not work with the Gutsy Kernel. So what's wrong here? 

best regards

---

### Post by Pumalite on 2007-10-28
What's probably wrong is Windows and her dev/hda.

---

### Post by ossi on 2007-10-28
Sorry if there is a misunderstanding, but there is only Kubuntu running on this machine. Nothing else is. So there is a Harddiscdrive which is originally /dev/hda and a DVDdrive which is /dev/hdb. But when the DVD Drive got changed during a warranty case from my laptop manufacturer I had to change the jumpering from the Discdrive from slave to master and now the Harddisc is slave.

This is what is unusual with my laptop. The Discdrive is Master and the Harddrive slave. Otherwise the machine won't work. I am sorry for being a bit unprecise with the terms here but I am not a expert ;-) Any clues or more info needed?

---

### Post by Pumalite on 2007-10-28
In that case: boot from Live CD, mount your partitions and post from Terminal:
sudo fdisk -lu
cat /boot/grub/menu.lst
(if you don't know how to mount partitions from Live CD, use Knoppix:(it mounts partitions automatically on boot.)

---

### Post by ossi on 2007-10-29
Used knoppix and did the sudo stuff. Here's the output:

> sudo fdisk -lu
[sudo] password for ossi:

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd5bd826f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   150239879    75119908+  83  Linux
/dev/hdb2       150239880   156296384     3028252+   5  Extended
/dev/hdb5       150239943   156296384     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   488392064   244196001   83  Linux

Disk /dev/sdb: 129 MB, 129892352 bytes
16 heads, 16 sectors/track, 991 cylinders, total 253696 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          33      253439      126703+   6  FAT16


Here is my kernel list:
> ### BEGIN AUTOMAGIC KERNELS LIST
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
# kopt=root=UUID=508e1901-f57f-8f00-0000-000002000000 ro
# kopt_2_6=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash locale=de_DE

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

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hdb1 ro quiet splash locale=de_DE
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

#title          Ubuntu 7.10, kernel 2.6.20-16-generic
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash locale=de_DE
#initrd         /boot/initrd.img-2.6.20-16-generic
#quiet

#title          Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro single
#initrd         /boot/initrd.img-2.6.20-16-generic

#title          Ubuntu 7.10, kernel 2.6.20-15-generic
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro quiet splash locale=de_DE
#initrd         /boot/initrd.img-2.6.20-15-generic
#quiet

#title          Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
#root           (hd0,0)
#kernel         /boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro single
#initrd         /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash locale=de_DE
initrd          /boot/initrd.img-2.6.17-11-generic
quiet

title           Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu 7.10, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash locale=de_DE
initrd          /boot/initrd.img-2.6.17-10-generic
quiet

title           Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST









But still can't mount the originial gutsy kernel, even if i tell it to use /dev/hdb1 for booting. I don't know. Here's what happens  when I boot the Gutsy Kernel in recovery mode:

```
tray
[ 10.316000] sr 2:0:0:0: Attached scsi generic sg3 type 5

```

And here the booting process stops. I still got a running system using the edgy kernel, but I would like to use the gutsy kernel. It also doesn't work when I use the feisty Kernels. Can anyone help me?

---

### Post by ossi on 2007-10-29
Can nobody help me? This is a serious issue. Help please ;-)

---

### Post by Pumalite on 2007-10-29
Set your bios to boot from the ide drive.

open the file /boot/grub/menu.lst via
Code:

gksudo gedit /boot/grub/menu.lst

Look for:

Quote:
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
change "hiddenmenu" to "#hiddenmenu"

This will give you the "grub menu" at boot up.

---

### Post by ossi on 2007-10-30
Thanks, but how can I get running the Gutsy Kernel with my slave hd? /dev/hdb1 does not seem to work :confused:

---

### Post by Pumalite on 2007-10-30
(hd1,0)?

---

### Post by ossi on 2007-10-30
Tried that, doesn't work either. Grub does not even start to boot the kernel - can't find HD. It's all very wicked, because what works with the Edgy Kernel does not work with the Kernels since Feisty. I hoped Gutsy would solve the issue, but no luck ;-)

---

### Post by ossi on 2007-10-31
I got the solution now. I got a hint in a other forum. Some guy pointed out, that since Feisty the Kernels don't use /dev/hda1 etc., they use now /dev/sda1. I had to change that in grub bootmenu. Now it seems to work. What's strange is, that Gutsy Kernel only boots when I type in /dev/sda1 and Edgy Kernel only boots when I type in /dev/hdb1. Got no clue why that happens, but it works now.

Remember also to change fstab if you got the same problem and use other external partitions.

---

