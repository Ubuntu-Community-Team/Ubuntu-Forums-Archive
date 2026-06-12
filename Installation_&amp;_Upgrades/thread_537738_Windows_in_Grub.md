---
title: "Windows in Grub"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by neonl on 2007-08-29
Hi!

I installed Ubuntu yesterday deleting all the partitions in my HDD. When creating the partitions for GNU/Linux I left 10 GB free for a future FAT32 (WinXP) partition. Today, I installed Windows XP but than I couldn't boot Ubuntu (GRUB was damaged). I searched on Google how to restore GRUB and was able to restore it as it was before Windows installation (grub acts like no Windows was installed). What do I have to do to make GRUB boot Windows XP?

Thanks... :)

---

### Post by Pumalite on 2007-08-29
Post:
sudo fdisk -l (small L)
cat /boot/grub/menu.lst
blkid
cat /etc/fstab

---

### Post by neonl on 2007-08-29
> **Pumalite said:**
> Post:
sudo fdisk -l (small L)
cat /boot/grub/menu.lst
blkid
cat /etc/fstab

Hi, thank you for the answer but Windows option doesn't show up on the grub menu yet...

I ran in all the lines you wrote on Terminal... do I have to replace something with a specific value? I don't know what to do... :(

---

### Post by nbkr on 2007-08-29
These lines are commands. Run them on a Linux Terminal and post whatever they output. The information is used for diagnostics.

---

### Post by neonl on 2007-08-29
> **nbkr said:**
> These lines are commands. Run them on a Linux Terminal and post whatever they output. The information is used for diagnostics.

I ran them in Linux Terminal with "sudo". What I don't understand is what I have to do with that output information. Sorry I'm a Linux newbie ;)

---

### Post by nbkr on 2007-08-29
> **neonl said:**
> I ran them in Linux Terminal with "sudo". What I don't understand is what I have to do with that output information. Sorry I'm a Linux newbie ;)

sudo is not needed. 

Anyway just copy and paste the information to here so that we all can see it. These information are needed so that we can see how your system is configured and what might be wrong with the configuration.

---

### Post by neonl on 2007-08-29
> **nbkr said:**
> sudo is not needed. 

Anyway just copy and paste the information to here so that we all can see it. These information are needed so that we can see how your system is configured and what might be wrong with the configuration.

Damn I'm really stupid... I didn't associate the "post" word with the forum ;).

Here is the terminal code (with everything):

```
rui@rui-pc:~$ sudo  fdisk -l
Password:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217       37811   293949337+   5  Extended
/dev/sda3   *       37812       38321     4096575    c  W95 FAT32 (LBA)
/dev/sda5            1217        1338      979933+  82  Linux swap / Solaris
/dev/sda6            1339       37811   292969341   83  Linux
rui@rui-pc:~$ cat /boot/grub/menu.lst
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
# password topsecret

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
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=0fa255b5-ff5e-4856-9ec6-d6142068cd6a ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0fa255b5-ff5e-4856-9ec6-d6142068cd6a ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0fa255b5-ff5e-4856-9ec6-d6142068cd6a ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0fa255b5-ff5e-4856-9ec6-d6142068cd6a ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0fa255b5-ff5e-4856-9ec6-d6142068cd6a ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
rui@rui-pc:~$ blkid
/dev/sda1: LABEL="Sistema" UUID="0fa255b5-ff5e-4856-9ec6-d6142068cd6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="16d8ffca-8b37-42c7-add3-a232d1ef5a88" TYPE="swap" 
/dev/sda6: UUID="806b538d-fd18-4b7a-b3b5-d9fb88e7f9cb" SEC_TYPE="ext2" TYPE="ext3" 
rui@rui-pc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0fa255b5-ff5e-4856-9ec6-d6142068cd6a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=806b538d-fd18-4b7a-b3b5-d9fb88e7f9cb /home           ext3    defaults        0       2
# /dev/sda5
UUID=16d8ffca-8b37-42c7-add3-a232d1ef5a88 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
rui@rui-pc:~$ 

```

---

### Post by Pumalite on 2007-08-29
Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If it still does nor give you a menu to boot both OS's, that's easy to fix,

---

### Post by neonl on 2007-08-29
> **Pumalite said:**
> Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If it still does nor give you a menu to boot both OS's, that's easy to fix,

Well.... nope! NO f&%$#*n windows yet... ;) 

How do I work it out?

---

### Post by maybeway36 on 2007-08-29
```
gksu gedit /boot/grub/menu.lst
```
Add to the bottom:
```
title         Windows XP
root          (hd0,2)
makeactive
chainloader   +1
```

---

### Post by Pumalite on 2007-08-29
If it doesn't work with 'root', try 'rootnoverify' (before (hd2,0))

---

### Post by neonl on 2007-08-30
> **Pumalite said:**
> If it doesn't work with 'root', try 'rootnoverify' (before (hd2,0))

It did work with root thank you guys... :)

---

