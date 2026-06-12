---
title: "Error loading operating system"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2008-02-14
I have recently installed a new motherboard on my computer I ran into some problems with that. But after a bios upgrade the problem was solved. Or so I thought.

I installed from the LIVE CD - 7.10 - and everything worked fine. Then after the first reboot I got the message "Error loading operating system". I searched the net and found that some people had this problem due to large harddrisk drives. 

Ubuntu is installed on my SATA disk which is the only one in my system and it seems that it's not considered the "first" device so the boot sector is written on the first IDE devices instead (which is fine by me since all my data is still on it). The first IDE device is a 200 GB maxtor disk. 

So I thought - large harddrive - ok, I'll move one of the other IDE disks I have on the system to the first position instead. This disk is 120 GB. I reinstalled the OS and rebooted and Ubuntu loaded. Weee.

Last night I shut down Ubuntu (can't rememeber if I got the latest updates - something about linux header files?) and now when I try to start up my PC is simply states:

"Error loading operating system"

I'm still able to load the LIVE CD without any problems. My first IDE device still has a boot sector on it (gparted says this anyway). What happend? and what can I do?

---

### Post by mlapaglia on 2008-02-14
did you check this out?
[http://ubuntuforums.org/showthread.php?t=386842](http://ubuntuforums.org/showthread.php?t=386842)

---

### Post by tbresson on 2008-02-14
No. But I'm reading it now.

tnx

---

### Post by tbresson on 2008-02-14
It doesn't give any solution as far as I can see..

---

### Post by tbresson on 2008-02-15
As suggested in the link I've posted the output on my system.        

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf3ce082

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+  83  Linux

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ef4cdf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf58cf58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24792   199141708+  83  Linux

Disk /dev/sdd: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb94756de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19929   160079661   83  Linux

Disk /dev/sde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x064d064d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       14569   117025461   83  Linux
/dev/sde2           14570       14946     3028252+   5  Extended
/dev/sde5           14570       14946     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo mkdir /mnt/rescue
ubuntu@ubuntu:~$ sudo mount /dev/sde1 /mnt/rescue
ubuntu@ubuntu:~$ cat /mnt/rescue/boot/grub/device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde
ubuntu@ubuntu:~$ cat /mnt/rescue/boot/grub/menu.lst
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
# kopt=root=UUID=6facb7ca-e5bc-458e-a860-1e534a11b8b5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,0)

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
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6facb7ca-e5bc-458e-a860-1e534a11b8b5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6facb7ca-e5bc-458e-a860-1e534a11b8b5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd4,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ cat /mnt/rescue/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=ae40daf3-bb91-4396-b7db-352672506eeb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sde5
UUID=f2696057-8beb-4b38-b9bf-fb661cfd411b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/dev/sda1       /home/cs/disk1        reiserfs        defaults        0       2
/dev/sdb1       /home/cs/disk2  reiserfs        defaults        0       2
/dev/sdc1       /home/cs/disk3 reiserfs        defaults        0       2
/dev/sdd1       /home/cs/disk4       reiserfs        defaults        0       2
ubuntu@ubuntu:~$ 

```

---

### Post by Epicfatigue on 2008-02-15
ahahah yeah well i have yet to install GRUB, 


Is there a link explaining how to install Grub?

or if anyone has the time could they explain it to me

---

### Post by tbresson on 2008-02-15
I found this on installing grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tbresson on 2008-02-15
I fixed my problem.

I loaded the LIVE CD and followed the directions on installing GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

In my case:
sudo grub
find /boot/grub/stage1
root (hd4,0)
setup (hd0)
quit

---

### Post by tbresson on 2008-02-16
Apparently I loose the GRUB after reboot.

So I used the LIVE CD again but this time it didn't work. Strange!

So I booted with the LIVE CD and choose, boot from the first harddisk - and that worked. Very strange indeeed.

I have no idea on how to fix this problem.

---

### Post by tbresson on 2008-02-20
By changing the boot order in the bios I fixed the problem.

Grub was not installed on the correct drive so by moving up the first harddrive (hd0) to the first position (in the boot order) the problem was solved.

---

