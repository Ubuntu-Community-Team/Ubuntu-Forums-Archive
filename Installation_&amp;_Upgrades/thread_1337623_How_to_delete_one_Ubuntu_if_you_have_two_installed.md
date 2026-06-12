---
title: "How to delete one Ubuntu if you have two installed"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by kixdrummond on 2009-11-25
I have Ubuntu 9.10 and Ubuntu Netbook Remix installed on my laptop, through a dual boot. How can I delete Ubuntu Netbook Remix with out deleting Ubuntu 9.10??

I have a Dell Latitude D610

---

### Post by mechro on 2009-11-25
You can format the relevant partition using Gparted or Palimpsest.

_**BUT**_ do you know which Ubuntu is managing your Grub boot process? If it's UNR then you'll need to reconfigure Grub in 9.10.

---

### Post by kixdrummond on 2009-11-25
> **mechro said:**
> You can format the relevant partition using Gparted or Palimpsest.

_**BUT**_ do you know which Ubuntu is managing your Grub boot process? If it's UNR then you'll need to reconfigure Grub in 9.10.


I dont know what is managing it.

Are Gparted and Palimsest Ubuntu programs or terminal commands?

---

### Post by audiomick on 2009-11-25
Gparted is a partitioning tool that is standard in Ubuntu, I think. If it is not on the computer, you can install it from the repositories with synaptic package manager.
I am not familiar with the other program, but I assume it is something similar.

---

### Post by mechro on 2009-11-25
Gparted and Palimpsest are Ubuntu programs. In 9.04 Gparted is available from **System > Administration > Partition Editor**. I'm guessing that takes you to Palimpsest in 9.10.

I could tell you how to check the Grub stuff in 9.04, but since you're using 9.10 with Grub2 I'm a bit lost. I'll go and have a read about it but hopefully someone will come along and give you some advice.

---

### Post by mechro on 2009-11-25
[IMG]http://farm3.static.flickr.com/2634/4134040893_9b7dafee40_o.png[/IMG]

OK, Palimpsest. Not much information there.

Can you open a Terminal (**Applications > Accessories > Terminal**) and enter the following command...

```
sudo fdisk -l
```

... that's a lower case L. It'll ask for your password.

Then enter the following command...

```
cat /etc/mtab
```

Post the results of these back here. You should be able to copy and paste the whole thing from the Terminal to your browser.

---

### Post by kixdrummond on 2009-11-25
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabb4abb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3798    30507403+  83  Linux
/dev/sda2            3799        4864     8562645    5  Extended
/dev/sda5            4681        4864     1477948+  82  Linux swap / Solaris
/dev/sda6            3799        4635     6723139+  83  Linux
/dev/sda7            4636        4680      361431   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by mechro on 2009-11-25
And the **cat /etc/mtab** please.

---

### Post by kixdrummond on 2009-11-25
christopher@andy-laptop:~$ sudo fdisk -l
[sudo] password for christopher: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabb4abb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3798    30507403+  83  Linux
/dev/sda2            3799        4864     8562645    5  Extended
/dev/sda5            4681        4864     1477948+  82  Linux swap / Solaris
/dev/sda6            3799        4635     6723139+  83  Linux
/dev/sda7            4636        4680      361431   82  Linux swap / Solaris

Partition table entries are not in disk order
christopher@andy-laptop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/christopher/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=christopher 0 0
christopher@andy-laptop:~$

---

### Post by mechro on 2009-11-25
OK. So assuming you're doing all this in your 9.10 install it means dev/sda6 is your UNR installation. That's shown as **6.9 GB Unrecognized** in Palimpsest.

You should be able to delete or reformat that partition in Palimpsest. I don't know the exact procedure because I haven't used Palimpsest.

Before you do that you'll need to check from which partition your grub bootloader is operating. I'll have a look at that tomorrow. Maybe someone else might chip in and help you.

---

### Post by kixdrummond on 2009-11-25
> **mechro said:**
> OK. So assuming you're doing all this in your 9.10 install it means dev/sda6 is your UNR installation. That's shown as **6.9 GB Unrecognized** in Palimpsest.

You should be able to delete or reformat that partition in Palimpsest. I don't know the exact procedure because I haven't used Palimpsest.

Before you do that you'll need to check from which partition your grub bootloader is operating. I'll have a look at that tomorrow. Maybe someone else might chip in and help you.
Ok cool thanks.

---

### Post by mechro on 2009-11-26
Can you do two more Terminal commands so we can find out the Grub2 boot configuration...


```
cat /etc/fstab
```

and...

```
cat /boot/grub/grub.cfg
```

Post the results here.

---

### Post by kixdrummond on 2009-11-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e7f51313-569b-44ab-a839-5ea79cf15010 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8793204e-d0d1-4e74-afeb-e88d1e244f60 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0









And....





christopher@andy-laptop:~$ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory
christopher@andy-laptop:~$ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory
christopher@andy-laptop:~$ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory
christopher@andy-laptop:~$

---

### Post by mechro on 2009-11-26
Oh! Perhaps you're not using Grub2. It doesn't matter. Can you do...

```
ls /boot/grub
```

---

### Post by kixdrummond on 2009-11-26
christopher@andy-laptop:~$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  minix_stage1_5     stage2
device.map     grubenv            menu.lst      reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  installed-version  menu.lst~     stage1
christopher@andy-laptop:~$

---

### Post by mechro on 2009-11-26
That's fine. Now do...

```
cat /boot/grub/menu.lst
```

... that's a lower case letter L in lst

---

### Post by kixdrummond on 2009-11-26
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e7f51313-569b-44ab-a839-5ea79cf15010

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=e7f51313-569b-44ab-a839-5ea79cf15010 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, memtest86+
uuid        e7f51313-569b-44ab-a839-5ea79cf15010
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mechro on 2009-11-27
It doesn't really matter now, but how were you booting UNR? :? It's not listed in your boot menu.

Anyway, you can now delete partition sda6 shown as **6.9 GB Unrecognized** in Palimpsest.

Also you have two swap partitions; Ubuntu is only using one of them. You can delete partition sda7 shown as **370 MB Swap Space** in Palimpsest.

When you've deleted these partitions you will have some unallocated space on your hard drive. You can either save it for future use or, with a bit of partition manipulation, you could add the space to your Ubuntu installation on sda1. I could tell you how to do that using Gparted but I can't really help you if you want to do it with Palimpsest.

---

