---
title: "RAID0 (Striped) Install fails"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Crisps on 2007-08-29
EDITED:  Probably an fstab issue, files attached.
I have looked in the previous forum topics but I cannot answer this issue.

I have installed my system following the FakeRaidHowto (very good document).

I cannot now get my system to start up, The grub loader works and brings up the ubuntu splash screen, then after a few seconds it bombs out to the terminal and I just see the standard mem disk and the bin/sh. It gives me an erro about not being able to find tty.

The only issue I had with the whole installation was setting the root password in the recovery module, so I think this may be where I am going wrong. I set the root password by doing the following

mkdir /real
mount -t ext3 /dev/mapper/isw_cdfhgfaejj_RAID6 /real
chroot /real
passwd
<enter password twice>

<ctrl + alt + delete>

am I doing something wrong, or is there a step that I have missed such as installing an important package. I do not think that there is a RAID issue, apart from the fact I had to do the complicated version of the install. If it was a RAID not being recognized thing then I wouldn't expect to see GRUB at all (as happened the first time when I just clicked install from the cd :-) )

Any help would be great, thanks

EDIT:

OK, after much playing around with this, I think I am having a simple problem of not finding the root device. here are some of the related files

ls /dev/mapper/
```

ubuntu@ubuntu:/$ ls /dev/mapper/
control               isw_cdfhgfaejj_RAID3  isw_cdfhgfaejj_RAID6
isw_cdfhgfaejj_RAID   isw_cdfhgfaejj_RAID4
isw_cdfhgfaejj_RAID1  isw_cdfhgfaejj_RAID5
ubuntu@ubuntu:/$ 

```

fdisk /dev/mapper/isw_cdfhgfaejj_RAID
```

Command (m for help): p

Disk /dev/mapper/isw_cdfhgfaejj_RAID: 319.9 GB, 319995248640 bytes
255 heads, 63 sectors/track, 38903 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cdfhgfaejj_RAID1               1          17      136521   83  Linux
/dev/mapper/isw_cdfhgfaejj_RAID2              18       19546   156866692+   5  Extended
/dev/mapper/isw_cdfhgfaejj_RAID3           19547       19563      136552+  86  NTFS volume set
/dev/mapper/isw_cdfhgfaejj_RAID4           19564       38903   155348550   86  NTFS volume set
/dev/mapper/isw_cdfhgfaejj_RAID5              18         205     1510078+  82  Linux swap / Solaris
/dev/mapper/isw_cdfhgfaejj_RAID6             206       19546   155356551   83  Linux

Command (m for help): q

ubuntu@ubuntu:/$ 

```

sudo mkdir /real
sudo mount -t ext3 /dev/mapper/isw_cdfhgfaejj_RAID6 /real
sudo mount -t ext3 /dev/mapper/isw_cdfhgfaejj_RAID1 /real/boot
sudo chroot /real
cat /etc/fstab
```

ubuntu@ubuntu:/$ sudo mkdir /real
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/mapper/isw_cdfhgfaejj_RAID6 /real
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/mapper/isw_cdfhgfaejj_RAID1 /real/boot
ubuntu@ubuntu:/$ sudo chroot /real
root@ubuntu:/# cat /etc/fstab
#file system                         mount      type      options       dump/pass 
proc                                 /proc      proc      rw               0 0
/dev/mapper/isw_cdfhgfaejj_RAID1     /boot      ext3      rw,user          0 2 
/dev/mapper/isw_cdfhgfaejj_RAID5     none       swap      sw               0 0  
/dev/mapper/isw_cdfhgfaejj_RAID6     /          ext3      rw,user          0 1
 
root@ubuntu:/# 

```

cat /boot/grub/menu.lst
```

root@ubuntu:/# cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password --md5 (EDIT: Removed for security on posting) 

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro
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
## e.g. kopt=root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro
##      kopt_2_6_8=root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro
##      kopt_2_6_8_2_686=root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro
# kopt=root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro
# kopt_2_6=root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5) (EDIT: I have tried both (hd0,0) and (hd0,5) here

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/isw_cdfhgfaejj_RAID1 ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin

title           Windows XP
rootnoverify    (hd0,2)
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST


```

error message
```

root@ubuntu:/# cd /boot
root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls
e2fs_stage1_5  menu.lst  menu.lst~  stage1  stage2
root@ubuntu:/boot/grub# cp menu.lst menu.bak
root@ubuntu:/boot/grub# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/boot/grub# mv menu.bak menu.lst

```

---

