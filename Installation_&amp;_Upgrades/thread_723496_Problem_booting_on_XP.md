---
title: "Problem booting on XP"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by soathiam on 2008-03-13
Hi,
i am a complete newbie
I tried to find a solution on several forums and website, but nothing seems to work or i havent search well.

Here is the problem:
i had windows XP running on my pc on one sata hard drive
and i installed Ubuntu Gutsy Gibon from the cd on another hard drive (IDE).
Following instructions from forums, i added 
"
title           Windows XP Home
root            (sd0,0)
savedefault
makeactive
chainloader     +1

to the menu.lst file, without any success (error 23: error while parsing number)
**Here is the sudo fdisk -l result:**

[COLOR="YellowGreen"]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2db82db7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x05f5d9f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      620178   312569680+   7  HPFS/NTFS

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb644b644

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         978     7855753+  83  Linux
/dev/hda2             979        1027      393592+   5  Extended
/dev/hda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6d5ae53

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24791   199133676    7  HPFS/NTFS

[/COLOR]
ubuntu is on the 8 Go HDD
XP is on the 80 Go HDD

Thank you for your help.

---

### Post by Pumalite on 2008-03-13
Change to (hd0,0) and add:
map (hd0,0)  (hd1,0)
map (hd1,0)  (hd0,0)
Before savedefault.

---

### Post by soathiam on 2008-03-13
Thanx for your answer Pumalite,

i tried that :
[COLOR="YellowGreen"]
title           Windows XP Home
root            (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader     +1
[/COLOR]
as you said, 
but when i select windows xp home from the menu i get the message:
"Error 23 : Invalid or unsupported executable format"
 What should i do?

---

### Post by Pumalite on 2008-03-13
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by soathiam on 2008-03-13
sudo fdisk -lu
[COLOR="YellowGreen"]
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb644b644

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    15711569     7855753+  83  Linux
/dev/hda2        15711570    16498754      393592+   5  Extended
/dev/hda5        15711633    16498754      393561   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6d5ae53

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   398267414   199133676    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2db82db7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f5d9f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625139423   312569680+   7  HPFS/NTFS
[/COLOR]
 cat /boot/grub/menu.lst
[COLOR="YellowGreen"]
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
# kopt=root=UUID=b3ee877e-cede-4f6d-90f7-463ce6d2f458 ro

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b3ee877e-cede-4f6d-90f7-463ce6d2f458 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b3ee877e-cede-4f6d-90f7-463ce6d2f458 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           Windows XP Home
root            (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader     +1



### END DEBIAN AUTOMAGIC KERNELS LIST

[/COLOR]

---

### Post by Pumalite on 2008-03-13
I thought you had changed 'root'.
This:
title Windows XP Home
root (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1
Change it to this:
title Windows XP Home
rootnoverify (hd1,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1
And move it below this line:
### END DEBIAN AUTOMAGIC KERNELS LIST
You might have to try (hd2,0) if the other doesn't work
(you have ntfs file systems in two hard drives)

---

### Post by soathiam on 2008-03-14
Thank you for your answer,
i will try that when i get home tomorow.
:D

---

### Post by soathiam on 2008-03-14
Hi pumalite,

i did it (tried both hd1 and hd2), and now i have the message "[COLOR="YellowGreen"]NTLDR missing. Pres crtl, Alt, del to restart[/COLOR]", 
I think that's a problem related to the xp boot, may be it doesn't recognize the HD with Ubuntu on it, but i really don't know
Do you have a clue?


Thanx again

---

### Post by Pumalite on 2008-03-14
I think you have the old IDE+SATA Mix problem:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by soathiam on 2008-03-15
Hi,
i think i srewed up everything, 
so i will reinstall both xp and ubuntu using the tutorials, hope this will work.

Thanks a lot for your time and help, i hope i will soon be able to help people as you did for me.

---

### Post by Pumalite on 2008-03-15
You are welcome. I'd suggest you install both systems on the master drive and leave the other one for storage. (or /home)

---

