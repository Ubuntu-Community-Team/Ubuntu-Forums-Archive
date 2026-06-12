---
title: "error 15"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by ronnybob on 2007-09-01
My Ubuntu was working perfect until a strong power surge that wiped out the hard drive. Replaced the HDD, then installed Ubuntu Fiesty 7.04 AMD 64, rebooted and received error 17, then trying to work it every way possible gave up and installed Freespire and it works perfectly. then went back and reinstalled Ubuntu and now error 15 shows up, Also when I put in the disk and scroll down to "Boot from first Drive" it boots to that drive and runs off the HDD without a flaw. 
My question is what is error 15 and what do I do to correct it?

---

### Post by merlinus on 2007-09-01
Press e at the grub menu and look at what is says for boot, e.g. (hd0,1).

Try changing that to (hd0,0), if ubuntu is on the first partition of your first (or only) hdd.

Partition numbering for this begins at zero, not one.

-merlin

---

### Post by Agrezar on 2007-09-01
pretty sure it means that grub cant find the files...

make sure your menu.lst in /boot/grub/ reflect the appropriate files in /boot/ .... for example...

in my menu.lst:

[PHP]title		Debian GNU/Linux, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic ro quiet splash  <----
initrd		/boot/initrd.img-2.6.20-16-generic  <-----[/PHP] 

matches 

[PHP][agrezar] <( 03:11 PM )> ~ $:ls -la /boot
total 16688
drwxr-xr-x  3 root root    4096 2007-09-01 13:43 .
drwxr-xr-x 22 root root    4096 2007-08-31 21:00 ..
-rw-r--r--  1 root root  414274 2007-08-30 21:33 abi-2.6.20-16-generic
-rw-r--r--  1 root root   83217 2007-08-30 18:32 config-2.6.20-16-generic
drwxr-xr-x  2 root root    4096 2007-09-01 13:55 grub
-rw-r--r--  1 root root 6931852 2007-09-01 13:43 initrd.img-2.6.20-16-generic <----
-rw-r--r--  1 root root 6932150 2007-08-31 19:50 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root   94600 2006-10-20 07:44 memtest86+.bin
-rw-r--r--  1 root root  807071 2007-08-30 21:34 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 1747276 2007-08-30 21:33 vmlinuz-2.6.20-16-generic  <----[/PHP]

***make sure you make a copy of your existing menu.lst before mucking around with it***

[PHP]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak[/PHP]

---

### Post by ronnybob on 2007-09-01
the hd0,0 is correct also the error message says "Error 15: file not found"

---

### Post by merlinus on 2007-09-01
Boot into ubuntu, open a terminal and post results of:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by ronnybob on 2007-09-02
ron@ron-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401    b  W95 FAT32

Disk /dev/sdb: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          96       98096    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(94, 63, 32) logical=(95, 51, 32)
ron@ron-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=c0c8753c-9033-4185-9308-f1fcccb97c04 ro

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c0c8753c-9033-4185-9308-f1fcccb97c04 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c0c8753c-9033-4185-9308-f1fcccb97c04 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ron@ron-desktop:~$

---

### Post by ronnybob on 2007-09-03
Problem solved :) I ran Freespire for 1 day and then installed Linspire which would not run on it's own earlier, so I was surprised. So I tried once more Ubuntu this morning and lo and behold it is running on it's own. Thanks guys for your help in trying to get me going.

---

