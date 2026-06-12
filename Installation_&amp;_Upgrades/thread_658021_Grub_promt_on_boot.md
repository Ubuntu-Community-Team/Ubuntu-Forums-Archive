---
title: "Grub promt on boot"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by Rickytoo on 2008-01-04
Problem: booting stops at a Grub prompt when I expect a list of boot entries.

I had working dual boot system with 6.10 and XP installed on separate hard discs. I reformatted the hard disc and installed 7.10 from a live cd. Since then booting stops at the Grub prompt.

Entering 'configfile /boot/grub/menu.lst' at the Grub prompt gives the list of boot entries and I can proceed as expected.

Can you explain the problem and help me solve it please?

Output from 'sudo fdisk -l':

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac96ac96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        3187     5116702+   7  HPFS/NTFS
/dev/sda3            3188        8286    40957717+   7  HPFS/NTFS
/dev/sda4            8287       24792   132584445    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000961c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24036   193069138+  83  Linux
/dev/sdb2           24037       24792     6072570    5  Extended
/dev/sdb5           24037       24792     6072538+  82  Linux swap / Solaris

 and 'cat /boot/grub/menu.lst':

:~$ cat /boot/grub/menu.lst
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
timeout         10

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
# kopt=root=UUID=4f37ab72-2732-462f-94a6-4bf9ad2817d2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4f37ab72-2732-462f-94a6-4bf9ad2817d2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4f37ab72-2732-462f-94a6-4bf9ad2817d2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by jw5801 on 2008-01-04
You could try setting up grub again. Once you've booted up run:
```
sudo grub #this will get you a grub prompt
root (hd1,0)
setup (hd1)
```

Assuming of course that grub is installed on the same harddrive as Ubuntu.

---

### Post by Rickytoo on 2008-01-04
> **jw5801 said:**
> You could try setting up grub again. Once you've booted up run:
```
sudo grub #this will get you a grub prompt
root (hd1,0)
setup (hd1)
```

Assuming of course that grub is installed on the same harddrive as Ubuntu.

Thanks for the reply. Tried it, no change. Output from terminal:
grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

Shouldn't stage1 be installed to (hd0)?

---

### Post by jw5801 on 2008-01-04
I wouldn't think it would matter which hard drive grub was installed to so long as that drive was first in your bios boot order, so there's the next thing to check. 

Otherwise you could try installing it to (hd0):```
sudo grub
root (hd1,0)
setup (hd0)
```

---

### Post by Rickytoo on 2008-02-29
> **jw5801 said:**
> I wouldn't think it would matter which hard drive grub was installed to so long as that drive was first in your bios boot order, so there's the next thing to check. 

Otherwise you could try installing it to (hd0):```
sudo grub
root (hd1,0)
setup (hd0)
```

Thanks for that. In fact my MOBO died shortly after posting. I managed to find a replacement after some time, plugged in the discs and everything just worked. I can only assume it was a hardware problem.

---

### Post by MONODA on 2008-02-29
no i think it was a problem with GRUB, I got the same problem after removing Opensuse from a dual boot with ubuntu but instead I used the SuperGRUB disk.

---

