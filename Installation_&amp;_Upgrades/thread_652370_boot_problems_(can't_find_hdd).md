---
title: "boot problems (can't find hdd)"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Talako on 2007-12-28
OK, trying to install Ubuntu 7.10 on a Dell Dimension 4600, I had already installed Xubuntu 6.10, but in upgrading, decided to change to gnome. This machine will eventually be a file server for our home network (side note, anyone know of a good program to backup a single directory on network machines?) Anyway, the install seemed to go fine, 2 IDE HDDs, one 80GB, one 500GB (80 is master, 500 slave, jumpers set correctly, IDE ribbon order correct). For some reason, instead of hda1 and hda2, or hda and hdb, w.e, they are sda and sdb, why is that and is that correct? That's question one.

When the install finished, I rebooted, and it took a while sitting at "Starting up... Loading..." then kinit decided to do a normal boot. Then I get a bunch of mount errors:
mount: Mounting /dev/sda on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

*it then enters BusyBox/initramfs*

Now for the second problem/question, I have gone in and tried changing menu.lst (from the LiveCD) and change the boot option from hda1 to sda1 to sda0 to sda, and it *always* gives me some similar errors, can't find the device, no such file or directory, w.e. What should I do to get it to boot, is there another file (fstab perhaps?) that I should be editing?
Thanks
Talako

---

### Post by Pumalite on 2007-12-28
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Talako on 2007-12-28
ok, but will those work in initramfs or the liveCD?

---

### Post by Pumalite on 2007-12-28
Boot the Live CD and from the Terminal run those commands (you have to mount your partition for cat /boot/grub/menu.lst, so post sudo fdisk -lu first.)

---

### Post by Talako on 2007-12-28
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3903794     1951866   82  Linux swap / Solaris
/dev/sda2   *     3903795    42973874    19535040   83  Linux
/dev/sda3        42973875   156296384    56661255    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035a27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    b  W95 FAT32
```

---

### Post by Pumalite on 2007-12-28
At the Terminal in your Live CD:
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
Then, from that partition:
cat /boot/grub/menu.lst

---

### Post by Talako on 2007-12-28
```
ubuntu@ubuntu:/media/sda2$ cat boot/grub/menu.lst
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
# kopt=root=UUID=33488d03-c026-4c70-afb5-197c926069b4 ro
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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda ro quiet nosplash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Pumalite on 2007-12-28
Things look OK, except I'm curious: what do you have in sdb?

---

### Post by Talako on 2007-12-28
sdb has nothing on it... yet, we will be using that for network storage.

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda ro quiet nosplash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```

should the kernel line say sda, or should it be sda2, since that's the specific partition? Even then, i think I tried that and it didn't work.

---

### Post by Pumalite on 2007-12-28
An aside; I'd partition sda differently:
sda1 for '/'
sda2 for /home
/swap at the end.
Then install.

---

### Post by Talako on 2007-12-28
OK, interesting, I'm sorta curious why, but I have to get this running at the moment. I just tried fdisk on my laptop (also gutsy) and I didn't type it correctly, 
```
mariot@Falcon1:~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

```

so it's telling me that a drive designated sdx is a SCSI drive, that isn't right, these are IDE drives, but the fdisk i got (as well as when I installed it) said they are sda and sdb. wtf?

BTW, thanks for all ur help so far.

---

### Post by Pumalite on 2007-12-28
Since Feisty, IDE's are recognized as sda, sdb, etc by the kernel.

---

### Post by meierfra on 2007-12-28
> Should the kernel line say sda, or should it be sda2, since that's the specific partition? 

Yes, it needs to be /dev/sda2

---

