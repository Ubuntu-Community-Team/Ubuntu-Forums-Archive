---
title: "Dual boot - XP and HH 8.04 - error 22 : no such partition."
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by capnahab on 2008-09-14
I have Xp on one disk. I have installed hardy heron 8.04 to same disk and on boot Grub brings up the options to boot into windows and Ubuntu. When i select ubuntu I get the no such partition error. I can't boot into the live CD because of video driver issues tho have managed previously to do a safe graphics install. Am a new user and don't know how to get into a shell to fdisk -l etc. from here.
I have 2 other discs on the machine but they don't seem to have been a problem. spose grub could be looking at the wrong disc.
Thanks

---

### Post by capnahab on 2008-09-14
Have managed to open live cd terminal and this is the output from the recommended commands. 
My /boot/grub/menu.lst seems to be pointing at my linux partition so I can't understand whats wrong.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.1st
ubuntu@ubuntu:~$ **[B]sudo fdisk -lu**[/B]

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe44ce44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   390700799   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe3439a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sdb2       268414020   270406079      996030   82  Linux swap / Solaris
/dev/sdb3       270406080   488392064   108992992+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3cb49660

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *        1008   488397167   244198080    f  W95 Ext'd (LBA)
/dev/sdc5            1071   488397167   244198048+   7  HPFS/NTFS

Disk /dev/sdf: 3993 MB, 3993697792 bytes
4 heads, 32 sectors/track, 60938 cylinders, total 7800191 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          32     7800190     3900079+   b  W95 FAT32
ubuntu@ubuntu:~$ **sudo mount /dev/sdb3 /mnt**
ubuntu@ubuntu:~$ **cat /mnt/boot/grub/menu.lst**
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
# kopt=root=UUID=94b5d6e3-a5ab-4544-8bac-430743e1f568 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
# defoptions=quiet splash xforcevesa

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94b5d6e3-a5ab-4544-8bac-430743e1f568 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94b5d6e3-a5ab-4544-8bac-430743e1f568 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$** sudo grub**
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> **find /boot/grub/stage1**
find /boot/grub/stage1
 (hd1,2)
grub> quit
quit
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-09-14
You should let Grub installed to its default: (hd0)
If you have a mix of SATA and IDE; Grub might be installed in the wrong drive.
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by caljohnsmith on 2008-09-14
Do you know which HDD is first in the boot order? 

Next time you boot up, select the Ubuntu entry in the Grub menu, hit "e" to edit it, select the line with "root (hd1,2)", press "e" to edit it, change it to "root (hd0,2)", return to save the change, then press "b" to boot Ubuntu. If that doesn't work, try (hd2,2) instead. If one of those combinations works, you can make the change permanent by editing your menu.lst once you boot into Ubuntu. Let me know how it goes.

---

### Post by capnahab on 2008-09-15
Many thanks,
I can boot my windows install from Grub no problem. Would windows be able to find its install , and UBUNTU not ? - they are on separate partitions of the same disc.

---

