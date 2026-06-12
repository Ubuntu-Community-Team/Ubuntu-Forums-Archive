---
title: "dual boot two ubuntu installations"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by Jeffa on 2008-01-29
Hello all

I'm having a little trouble dual booting two ubuntu installations. At first I installed ubuntu 7.10 to give it a try. during the install, I partitioned the HDD into three partitions. I put 7.10 on one, used one small one for swap, then left the rest as unformatted for future use. Then I decided to give 64 bit a try and take full advantage of the system resources. So I installed kubuntu 64 bit 7.10 on the previously unformatted partition and used the previous swap partition again. The install seemed to go well, I didn't get any errors and it finished fine. But I expected a grub menu to allow me to choose which install to boot into on startup, but that didn't happen. It booted straight into the old 32 bit Ubuntu partition. I am able to mount the partition with the 64 bit install, and all the files appear to be there. Anyone know how I can boot into the 64 bit install? 

Thanks in advance!

---

### Post by Pumalite on 2008-01-29
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Jeffa on 2008-01-29
sudo fdisk -lu looks like this:

```
Disk /dev/sda: 999.9 GB, 999999668224 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124352 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953118439   976559188+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   204796619   102398278+  83  Linux
/dev/sdb2       204796620   206836874     1020127+  82  Linux swap / Solaris
/dev/sdb3       206836875   488392064   140777595   83  Linux

Disk /dev/sdc: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders, total 640 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdc doesn't contain a valid partition tabl
```

cat /boot/grub/menu.lst looks like this:

```
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
# kopt=root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro

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
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=f984db45-87cc-4e8b-aa15-9b06d4aadd77 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thanks!

---

### Post by Pumalite on 2008-01-29
'title           Ubuntu, kernel 2.6.20-16-generic'
If you had 7.10, you would have: 2.6.22-14-generic
???

---

### Post by Jeffa on 2008-01-29
Oops. Right. I'm not running 7.10, I'm running 7.04. Good catch.

---

### Post by Pumalite on 2008-01-29
Boot your 64 bit Live CD and reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Jeffa on 2008-02-01
hmm. Well, I tried reinstalling grub as per the instructions. the next time I rebooted, I got a grub menu, but every time i try and boot into one of the choices listed, I get the following error:  

Error 22: No such partition. 

that's worrisome. any thoughts?

---

### Post by Jeffa on 2008-02-05
Solved (although not particularly elegantly) by wiping the hard drive and reinstalling 64 bit version of 7.10.

on the plus side, the afforded me the opportunity to place my /home directory on its own partition!

---

