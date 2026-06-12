---
title: "Error 17 Message !!!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Ranger One on 2007-04-20
I'm new to Ubuntu but have past experience with Mandrake & RedHat.

I'm installing Ubuntu 7.04 (already tried 6.10) to my second hard drive, first partition. I set grub to install to hd1, I keep getting the error 17 message with both versions of Ubuntu. It will boot my various Windows installs on other hard drives but WILL not boot into Ubuntu. I really wanted to try Ubuntu to check it out & set it up with Mythtv. I do NOT want to install the Grub bootloader to any other drive other than the one it is installed on. Error 17... doesn't recognize file system.. I've tried both ext3 & rieserts fs.

I have two partitions.. (/) & swap.

I've already spent a lot of time on this.

Any ideas as to what's going on here?

---

### Post by Amorphous_Snake on 2007-04-21
I have the same problem. I also installed Ubuntu 7.04 from the desktop CD and configured Grub to be installed into hd1.

My first HDD: 20 GB NTFS (Windows), 140 GB NTFS
2nd HDD: 100 GB NTFS and 19 GB EXT3 for / and 1 GB for swap.

I have an idea but I will try it later. I will use the GParted live CD to set the / drive into boot drive if it's not.

---

### Post by bulldog on 2007-04-21
If you set grub on the second hdd,and you boot from it.it will become hd0.
So you have to modify the menu.lst and change (hd1,?) into (hd0,?) and it will work.

The best thing to do is to make the second hdd your default boot device,make a windows entry in menu.lst and choose from grub  if you want to boot ubuntu or windows.
No more hassling to choose another hdd to boot from and your windows can still be booted from it's own boot loader,because there's nothing changed.

You only have to make an entry for windows like this one.```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1
```

---

### Post by Amorphous_Snake on 2007-04-21
Actually I tried that by editing grub options for Windows XP in the grub screen. And windows worked. Doing the same for Ubuntu results in a splash screen and the loading bar just wouldn't move. I had to press Alt Crtl Del to exit.

I may add that the Gparted thing I wanted to try didn't work.

Previously when I had openSUSE 10.2, I installed it on the second HDD (after unpluging the first), then after installation I will plug the 1st HDD (the one with windows) and manually add grub entries for Windows and mount the other partitions manually too. Should I do so?

---

### Post by bulldog on 2007-04-21
I shouldn't disconnect any hdd,be sure that everything is listed correctly in fstab and menu.lst.
You may copy your menu.lst to the forum,and the output of```
sudo fdisk -l
``` and your fstab.

So somebody can have a look on it.

I'll be off for about 4 hours,than I'll return,and if nobody else looked at the problem,I'll do it.
But you have to be a little patient :)

---

### Post by Amorphous_Snake on 2007-04-21
Here is my menu.lst file:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=5f3b6a58-d8e8-4141-b734-d8b5dac18e37 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5f3b6a58-d8e8-4141-b734-d8b5dac18e37 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5f3b6a58-d8e8-4141-b734-d8b5dac18e37 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
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
chainloader	+1


and when running "sudo fdisk -l"

> Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       20023   141299707+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11978    96213253+   7  HPFS/NTFS
/dev/sdb2   *       11979       14467    19992892+  83  Linux
/dev/sdb3           14468       14589      979965   82  Linux swap / Solaris


Note that I am running this from the LiveCD, and I made sure that the listed files were from the root drive of the Ubuntu installation.

---

### Post by bulldog on 2007-04-21
You can boot windows from GRUB,that means GRUB is installed on the windows hdd called (hd0)
So your ubuntu is on (hd1) which is correct in menu.lst.
The only thing I can think of is the UUID isn't right either in menu.lst or fstab or even both.

Try the command```
ls /dev/disk/by-uuid -lh
``` which will list all the UUID's.
Compare them with the UUID in menu.lst and fstab as well.
Warning,it is on two places in menu.lst,in the kernel lines but also here```
## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5f3b6a58-d8e8-4141-b734-d8b5dac18e37 ro
```

Change them if they aren't the right one for your / partition which is called sdb2
After that ```
sudo update-grub
``` and try to boot.

---

### Post by Amorphous_Snake on 2007-04-21
NO. The 1st HDD wasn't touched by Grub. I can directtly boot from it by setting the BIOS to boot from HDD0. When I set it to boot from HDD1, I see Grub.

I managed to boot Windows from Grub by editing it in the Grub screen during boot and adding hd(1,0) instead of (hd0,0) and adding map (hd0) (hd1) map (hd1) (hd0).

And how can I do the commands that you want me to do? I can't access my installation. Can I do them from the Live CD?

---

