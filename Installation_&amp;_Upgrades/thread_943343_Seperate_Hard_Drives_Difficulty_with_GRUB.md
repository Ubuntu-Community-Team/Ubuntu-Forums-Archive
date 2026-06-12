---
title: "Seperate Hard Drives: Difficulty with GRUB"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by shade11 on 2008-10-10
After installing Ubuntu, there appears to be some difficulty with GRUB.

Currently, when I boot into GRUB I receive an error regardless of what operating system I choose to boot into:

```
Error 21: Selected disk does not exist.
```

Grub runs on the same hard drive as my Windows XP partition does. The hard drive with Windows XP uses the Microsoft MBR (nothing else seemed to work). My Ubuntu 8.04 partition is currently installed on a separate hard drive. I had to change back to XP as my boot flag instead of GRUB in order to boot properly.

Is there a way for me to get GRUB functioning properly?

Here are some details:

-The computer is currently running on two hard drives, one master and one slave.
-The slave drive is plugged in through a PCI IDE Bus since there is no more room on the motherboard.
-The master drive is plugged directly into the motherboard.

---

### Post by Elfy on 2008-10-10
You'll have to boot the live cd to get some information, run

```
sudo fdisk -l
```

You could also follow my post here to get the menu list
[http://ubuntuforums.org/showthread.php?t=943245](http://ubuntuforums.org/showthread.php?t=943245)

---

### Post by shade11 on 2008-10-10
Here it is:

```
Disk /dev/hdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ea50ea4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1            4574        4865     2345490   82  Linux swap / Solaris
/dev/hdf2   *           1        4573    36732591   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9712    78011608+   7  HPFS/NTFS
/dev/sda2            9713        9726      112455   83  Linux

```

---

### Post by Elfy on 2008-10-10
Can you do these and then post the outputs you get for the last 2 commands please.

```
sudo mkdir /mnt/recover
sudo mount -t ext3 /dev/hdf1 /mnt/recover
```
Should be no errors if there are - post them pelase

```
cat /mnt/recover/boot/grub/menu.lst
cat /mnt/recover/boot/grub/device.map
```

---

### Post by shade11 on 2008-10-10
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/recover
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdf1 /mnt/recover
**mount: /dev/hdf1 already mounted or /mnt/recover busy**
ubuntu@ubuntu:~$ cat /mnt/recover/boot/grub/menu.lst
**cat: /mnt/recover/boot/grub/menu.lst: No such file or directory**
ubuntu@ubuntu:~$ cat /mnt/recover/boot/grub/device.map
**cat: /mnt/recover/boot/grub/device.map: No such file or directory**

```

---

### Post by Elfy on 2008-10-10
You already have it mounted then - be in nautilus I expect - just naviagte to /boot/grub and open the 2 files and paste from there

---

### Post by shade11 on 2008-10-10
There is no /boot/grub that I can see. There is only /boot which contains:

abi-2.6.24-19-generic
config-2.6.24-19-generic
memtest86+.bin
System.map-2.6.24-19-generic
cmlinuz-2.6.24-19-generic

Does it not show up since GRUB is on my other harddrive?

---

### Post by Elfy on 2008-10-10
mmm.. I thought that grub on the other drive would just point here.

Try to reinstall grub form the livecd - do ```
sudo grub
``` to get grub prompt grub>, if it doens't find grub with the find boot quit.

grub>find /boot/grub/stage1
(response should be in form hdx,y)
grub>root (hdx,y)
grub> setup (hdx)
grub> quit

You might have more luck with supergrub, in the meantime I'll look at the grubpage

---

### Post by hyper_ch on 2008-10-10
there are some issues with IDE / SATA drive combinations... grub sometimes does not setup things correctly. Best would be to (1) detach the drive that does not have /boot (2) install grub on that drive (3) set the bios to boot as first device from that drive (4) re-attach the other drive.

---

### Post by caljohnsmith on 2008-10-10
Can you set your hdf drive in BIOS to boot first on start up? If you can, that would be ideal, because using Forestpixie's method will install Grub to the MBR of that drive and make it bootable. Then the only thing you might need to do is tweak your Grub's menu.lst. So we can see your menu.lst, first do:
```
sudo umount /dev/hdf2
```
Don't worry if it returns a "not mounted" error, it is only to make sure hdf2 is not mounted somewhere. Proceed with:
```
sudo mount /dev/hdf2 /mnt
cat /mnt/boot/grub/menu.lst
```
And post the results of that. Also, what is that Linux partition on sda2?

---

### Post by shade11 on 2008-10-10
> **forestpixie said:**
> mmm.. I thought that grub on the other drive would just point here.

Try to reinstall grub form the livecd - do ```
sudo grub
``` to get grub prompt grub>, if it doens't find grub with the find boot quit.

grub>find /boot/grub/stage1
(response should be in form hdx,y)
grub>root (hdx,y)
grub> setup (hdx)
grub> quit

You might have more luck with supergrub, in the meantime I'll look at the grubpage

No luck.

> **hyper_ch said:**
> there are some issues with IDE / SATA drive combinations... grub sometimes does not setup things correctly. Best would be to (1) detach the drive that does not have /boot (2) install grub on that drive (3) set the bios to boot as first device from that drive (4) re-attach the other drive.

None of my drives are using SATA. I have the capability to use SATA drives, but I'm not.

> **caljohnsmith said:**
> Can you set your hdf drive in BIOS to boot first on start up? If you can, that would be ideal, because using Forestpixie's method will install Grub to the MBR of that drive and make it bootable. Then the only thing you might need to do is tweak your Grub's menu.lst. So we can see your menu.lst, first do:
```
sudo umount /dev/hdf2
```
Don't worry if it returns a "not mounted" error, it is only to make sure hdf2 is not mounted somewhere. Proceed with:
```
sudo mount /dev/hdf2 /mnt
cat /mnt/boot/grub/menu.lst
```
And post the results of that. Also, what is that Linux partition on sda2?

Here it is:

```
**ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst**
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=f74e1c59-3048-430b-91c8-8d01475d9b0d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f74e1c59-3048-430b-91c8-8d01475d9b0d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f74e1c59-3048-430b-91c8-8d01475d9b0d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
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
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by hyper_ch on 2008-10-10
> **shade11 said:**
> None of my drives are using SATA. I have the capability to use SATA drives, but I'm not.

yet you still have a mix-up

```
Disk /dev/hdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ea50ea4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1            4574        4865     2345490   82  Linux swap / Solaris
/dev/hdf2   *           1        4573    36732591   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9712    78011608+   7  HPFS/NTFS
/dev/sda2            9713        9726      112455   83  Linux

```

---

### Post by shade11 on 2008-10-10
> **hyper_ch said:**
> yet you still have a mix-up

```
Disk /dev/hdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ea50ea4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1            4574        4865     2345490   82  Linux swap / Solaris
/dev/hdf2   *           1        4573    36732591   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9712    78011608+   7  HPFS/NTFS
/dev/sda2            9713        9726      112455   83  Linux

```

I don't quite fully understand what you mean.

---

### Post by hyper_ch on 2008-10-10
hdf vs. sda
ide vs. sata

---

### Post by caljohnsmith on 2008-10-10
> **shade11 said:**
> No luck.

If you want help booting from your hdf drive, you'll need to tell us more than "no luck." :) So what exactly happens when you follow Forestpixie's steps in post #8? Can you post the output? If it says it succeeds, what happens when you boot from the hdf drive?

---

### Post by shade11 on 2008-10-10
> **caljohnsmith said:**
> If you want help booting from your hdf drive, you'll need to tell us more than "no luck." :) So what exactly happens when you follow Forestpixie's steps? Can you post the output? If it says it succeeds, what happens when you boot from the hdf drive?

I receive the input that he told me I'd get (hd0,1). I boot into GRUB after and it still didn't work.

---

### Post by Pumalite on 2008-10-10
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by caljohnsmith on 2008-10-10
> **shade11 said:**
> I receive the input that he told me I'd get (hd0,1). I boot into GRUB after and it still didn't work.
I don't think you've mentioned it yet, but what is on sda2? Is that maybe a boot partition?

---

### Post by shade11 on 2008-10-10
> **caljohnsmith said:**
> I don't think you've mentioned it yet, but what is on sda2? Is that maybe a boot partition?


I have no idea. SDA2 is an 109.82 MiB ext2 drive flagged as boot. This is where GRUB resides.

---

### Post by caljohnsmith on 2008-10-10
OK, try:
```
sudo umount /dev/sda2
sudo umount /mnt
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
And post the output. Next post the output of:
```
sudo dd if=/dev/hdf bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/hdf bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
Also, did you post the full output of "sudo fdisk -l" in post #3? I don't think you should have an hdf drive unless you also have drives hda, hdb, hdc, etc.

---

### Post by shade11 on 2008-10-10
> **caljohnsmith said:**
> OK, try:
```
sudo umount /dev/sda2
sudo umount /mnt
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
And post the output.

```
ubuntu@ubuntu:~$ ls -l /mnt
total 11103
-rw-r--r-- 1 root root    422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root     80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x 2 root ubuntu    1024 2008-10-08 05:42 grub
-rw-r--r-- 1 root ubuntu 7871345 2008-10-08 05:42 initrd.img-2.6.24-19-generic
drwxr-xr-x 2 root root     12288 2008-10-08 15:31 lost+found
-rw-r--r-- 1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root    905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root   1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

```

> **caljohnsmith said:**
> Next post the output of:
```
sudo dd if=/dev/hdf bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/hdf bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```

```
ubuntu@ubuntu:~$ **sudo dd if=/dev/hdf bs=512 count=1 2>/dev/null | strings | grep -i grub**
GRUB 
ubuntu@ubuntu:~$ **sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub**
ubuntu@ubuntu:~$ **sudo dd if=/dev/hdf bs=1 skip=1049 count=2 2>/dev/null | hexdump**
0000000 ff01                                   
0000002
ubuntu@ubuntu:~$ **sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump**
0000000 8001                                   
0000002
ubuntu@ubuntu:~$ 
```

> **caljohnsmith said:**
> so, did you post the full output of "sudo fdisk -l" in post #3? I don't think you should have an hdf drive unless you also have drives hda, hdb, hdc, etc.

That was the whole thing.

```
Disk /dev/hdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ea50ea4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1            4574        4865     2345490   82  Linux swap / Solaris
/dev/hdf2   *           1        4573    36732591   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9712    78011608+   7  HPFS/NTFS
/dev/sda2   *        9713        9726      112455   83  Linux

```

---

### Post by caljohnsmith on 2008-10-10
OK, that clears things up a bit; you've got a boot partition on your Windows drive, i.e. sda2. Also, your hdf drive has Grub installed to the MBR, while sda does not. I'll need a little more info though before I can straighten out your setup, so please post:
```
sudo umount /dev/hdf2
sudo umount /dev/sda2
sudo mkdir /media/hdf2 /media/sda2
sudo mount /dev/hdf2 /media/hdf2
sudo mount /dev/sda2 /media/sda2
cat /media/hdf2/etc/fstab
ls -lR /media/hdf2/boot
ls -l /media/sda2/grub

```

---

### Post by shade11 on 2008-10-10
```
**ubuntu@ubuntu:~$ sudo umount /dev/hdf2**
umount: /dev/hdf2: not mounted
[B]ubuntu@ubuntu:~$ sudo umount /dev/sda2
ubuntu@ubuntu:~$ sudo mkdir /media/hdf2 /media/sda2
ubuntu@ubuntu:~$ sudo mount /dev/hdf2 /media/hdf2
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/sda2
ubuntu@ubuntu:~$ cat /media/hdf2/etc/fstab[/B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdf2
UUID=f74e1c59-3048-430b-91c8-8d01475d9b0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdf1
UUID=4a713088-590f-4862-a8e6-832086360433 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
**ubuntu@ubuntu:~$ ls -lR /media/hdf2/boot**
/media/hdf2/boot:
total 11096
-rw-r--r-- 1 root root    422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root     80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x 2 root ubuntu    4096 2008-10-07 20:20 grub
-rw-r--r-- 1 root ubuntu 7884702 2008-10-07 20:20 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root    905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root   1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

/media/hdf2/boot/grub:
total 196
-rw-r--r-- 1 root ubuntu    197 2008-10-07 20:20 default
-rw-r--r-- 1 root ubuntu     30 2008-10-07 20:20 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-10-07 20:20 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-10-07 20:20 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-10-07 20:20 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-10-07 20:20 jfs_stage1_5
-rw-r--r-- 1 root root     4605 2008-10-07 20:20 menu.lst
-rw-r--r-- 1 root ubuntu   7324 2008-10-07 20:20 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-10-07 20:20 reiserfs_stage1_5
-rw-r--r-- 1 root ubuntu    512 2008-10-07 20:20 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-10-07 20:20 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-10-07 20:20 xfs_stage1_5
**ubuntu@ubuntu:~$ ls -l /media/sda2/grub**
total 169
-rw-r--r-- 1 root ubuntu    197 2008-10-08 05:42 default
-rw-r--r-- 1 root ubuntu     30 2008-10-08 05:42 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-10-08 05:42 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-10-08 05:42 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-10-08 05:42 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-10-08 05:42 jfs_stage1_5
-rw-r--r-- 1 root root     4580 2008-10-08 05:42 menu.lst
-rw-r--r-- 1 root ubuntu   7324 2008-10-08 05:42 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-10-08 05:42 reiserfs_stage1_5
-rw-r--r-- 1 root ubuntu    512 2008-10-08 05:42 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-10-08 05:42 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-10-08 05:42 xfs_stage1_5
**ubuntu@ubuntu:~$ **
```

---

### Post by caljohnsmith on 2008-10-10
According to your fstab, your hdf2 Ubuntu install is not using that sda2 /boot partition at all. Also, your menu.lst in hdf2 looks like it should boot Ubuntu fine when you boot from your hdf drive. So what happens now on start up? You get the Grub menu, you select the first Ubuntu entry, and do you still get error 21?

If that is true, then next time on start up, select the Ubuntu entry, press "e" to edit it, and just confirm that it uses "root (hd0,1)". If it does, press ESC to get the main Grub menu again, press "c" to get the Grub command line, and do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
Do you have a digital camera maybe that you could take a screen shot of the output of the two above commands? If you don't please let me know what they say.

---

### Post by freeqaz on 2008-10-10
I'm sitting next to Shade right now, so I can relay any info that you need. Like those 2 commands from the grub console...

OK, he just says he booted ubuntu now. w00t. :P

---

### Post by freeqaz on 2008-10-10
This is the output from caljohnsmith's request. 

```
**geometry (hd0)**
drive0x80; C/H/S/ = 1023/255/63, the number of sectors = 156250000, LBA
partition num: 0, filesystem type unknown, partition type 0x7
partition num: 1, filesystem type ext2fs, partition type 0x83

**geometry (hd1)**

error 21: selected disk does not exist
```
He doesn't mind reinstalling ubuntu also.

---

### Post by shade11 on 2008-10-10
Worth noting that Ubuntu booted properly on hd0, it never stays the same after I go back to GRUB however. It didn't boot properly however, may be a separate issue.

---

### Post by caljohnsmith on 2008-10-10
So how did he boot into Ubuntu? What exactly did he do? According to those geometry commands, the only drive Grub sees on start up is the Windows drive, not the Ubuntu drive. 

Next do this:
```
sudo dd if=/dev/sda bs=512 count=20 | gzip -c > ~/Desktop/sda.bin.gz
```
That will create a small "sda.bin.gz" file on your Ubuntu desktop, please attach that file in your next post. Also post:
```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
cat /media/sda2/boot/grub/menu.lst
```
Also, next time on reboot, press "c" again to get the Grub command line, then type the following exactly without pressing return:
```
grub> geometry (hd
```
And hit TAB for tab completion. What drives does it show?

---

### Post by shade11 on 2008-10-10
I'll post this now and tell you whats on grub when it restarts.

```
[B]ubuntu@ubuntu:~$ sudo mkdir /media/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/sda2
ubuntu@ubuntu:~$ cat /media/sda2/boot/grub/menu.lst[/B]
cat: /media/sda2/boot/grub/menu.lst: No such file or directory

```

Attached is the sda.bin.gz file.

---

### Post by freeqaz on 2008-10-10
```
geometry (hd0,
possible partitions are:
partition num 0, filesystem type unknown, partition type 0x7
partition num 1, filesystem type ext2fs, partition type 0x83
```

Damn this is confusing.

---

### Post by shade11 on 2008-10-10
It still refuses to boot properly.

---

### Post by meierfra. on 2008-10-10
> Worth noting that Ubuntu booted properly on hd0, 
What does this mean? Did you boot into Ubuntu?  Under what circumstances?

> it never stays the same after I go back to GRUB however.
?????? Please explain.


>  It didn't boot properly however, may be a separate issue
What does this mean?  What exactly happened? Did you get any error messages? 


> ubuntu@ubuntu:~$ sudo mkdir /media/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/sda2
ubuntu@ubuntu:~$ cat /media/sda2/boot/grub/menu.lst
cat: /media/sda2/boot/grub/menu.lst: No such file or directory

Caljohnsmith's instruction contain a typo. He meant to say:


```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
cat /media/sda2/grub/menu.lst
```

---

### Post by gpsmikey on 2008-10-10
In the original post, the comment was made that the "master" was plugged into one connector and the "slave" into another connector.  If that is the case, that is probably the problem - with IDE drives, you always (well, usually) need a "master" on the same cable as a "slave" - typically, if you have a drive configured as "slave" alone on a cable, you can get some strange things happening involving time-outs and the drive not being found.  If you have two drives on two different cables, they should both be configured as "master" (or CS if you are using "cable select").

mikey

---

### Post by shade11 on 2008-10-11
I changed both drives to master and reinstalled Ubuntu just to be sure. What should I flag as boot?

---

### Post by meierfra. on 2008-10-11
> What should I flag as boot? 

Usually the  boot loader is installed to  the MBR of one of the two hard drives. In this case the boot flag does not matter. Just set your bios to boot from that hard drive.

But if you changed the location of the boot loader in the advanced tab during the last step of the installation and  chose to install the boot loader to a partition, then you need to set the boot flag to that partition.

---

### Post by shade11 on 2008-10-11
> **meierfra. said:**
> Usually the  boot loader is installed to  the MBR of one of the two hard drives. In this case the boot flag does not matter. Just set your bios to boot from that hard drive.

But if you changed the location of the boot loader in the advanced tab during the last step of the installation and  chose to install the boot loader to a partition, then you need to set the boot flag to that partition.

My BIOS does not allow me to choose which hard drive to boot from.

---

### Post by meierfra. on 2008-10-11
> My BIOS does not allow me to choose which hard drive to boot from. 

O.K.  Then boot flags should not matter.

What is the current status? What happens during boot up?

---

### Post by shade11 on 2008-10-11
It turns out it was the PCI IDE bus. Neither my BIOS nor GRUB recognized it. For now I unplugged my CD drive and put it into the PCI IDE bus. I'll have to get a SATA hard drive in order to plug my CD drive back into the IDE slot. For now, it works.

---

