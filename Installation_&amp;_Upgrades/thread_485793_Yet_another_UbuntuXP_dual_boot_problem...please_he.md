---
title: "Yet another Ubuntu/XP dual boot problem...please help!"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by ybh6336 on 2007-06-27
Hello all,

I read all the posts related to dual boot issues, but couldn't really find the solution to my problem. Pardon me if this has been answered before. I had a dual boot of Fedora and XP on my laptop, and I overwrote Fedora with Ubuntu 7.04 but now my system just hangs on the GRUB screen on startup.I installed Ubuntu using the Live DVD/CD and allowed the installer to put GRUB at its default location (hd0). When I boot up my system, this is all I see:

GRUB_

(_ is a blinking prompt)

This is what my **/boot/grub/menu.lst** looks like:

[B][I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=54c8603e-b1b0-4899-b370-ecf25174fc3c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=54c8603e-b1b0-4899-b370-ecf25174fc3c ro quiet splash
initrd        /boot/initrd.img- 2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=54c8603e-b1b0-4899-b370-ecf25174fc3c ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

The output of '**fdisk -l**' is as follows:

[B][I]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3214    25816423+   7  HPFS/NTFS
/dev/sda2            3215        7804    36869175    f  W95 Ext'd (LBA)
/dev/sda3            7805        7935     1052257+  82  Linux swap / Solaris
/dev/sda4            7936        9716    14305882+  83  Linux
/dev/sda5            3215        7804    36869143+   b  W95 FAT32[/I][/B][/I][/B]


And **/etc/fstab** looks like as follows:

[B][I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=54c8603e-b1b0-4899-b370-ecf25174fc3c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=DA6043A960438AE9 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=41B6-2D7D  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=40e74160-7791-4cdd-adcf-2287c2592299 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0[/I][/B]

I would really appreciate any ideas to fix this problem, can't wait to try out Ubuntu.

Regards.

---

### Post by dreadlord_chris on 2007-06-27
your **menu.lst** is all screwed up. GRUB is trying to find an OS at **root (hd0,3)** - but according to your fdisk output it should be **root (sd0,4)** for Ubuntu and **root (sd0,1)** for your Windows OS

You need to edit your **/boot/grub/menu.lst** and point the menu options at the proper places.

---

### Post by ybh6336 on 2007-06-27
Thanks for your response. Should it be 'root (sd0,4) for Ubuntu and root (sd0,1) for your Windows OS' or 'root (hd0,4) for Ubuntu and root (hd0,1) for your Windows OS'? (Notice hd0 Vs. sd0)

Regards.

---

### Post by dreadlord_chris on 2007-06-27
> **ybh6336 said:**
> Thanks for your response. Should it be 'root (sd0,4) for Ubuntu and root (sd0,1) for your Windows OS' or 'root (hd0,4) for Ubuntu and root (hd0,1) for your Windows OS'? (Notice hd0 Vs. sd0)

Regards.

your menu/lst needs to match the output of fdisk. So, in your case it would be **root (sd0,4)** for Ubuntu and **root (sd0,1)** for your Windows OS

---

### Post by ybh6336 on 2007-06-27
Thanks a lot :). I shall try that as soon as I get home tonight.

Regards.

---

### Post by merlinus on 2007-06-27
Uncertainly prevails.

IIRC, numbering for root and partitions begins at 0, not 1.  If that is so, then /boot/grub/menu.lst is correct.

e.g. sda1 = (hd0,0); sda4 = (hd0,3).

However, it may be that the grub root is incorrect.

At the grub menu, press e and look at what it says.  From what I can see, it should be:

(hd0,3).

In my case, sudo fdisk -l gives windows as sda1 and / as sda8.  But in my menu.lst, they are (hd0,0) and hd(0.7), and grub root is (hd0,7).

If I am mistaken, please let me know.

Thanks!

-merlin

---

### Post by ybh6336 on 2007-06-27
I was hoping that would work, but unfortunately it did not, still seeing only 'GRUB _' during startup. Pressing 'e' did not show anything, it just freezes at that screen. Any thoughts? Appreciate your time.

Thanks.

---

### Post by xzero1 on 2007-06-27
It seems grub is not installed completely anymore. I would try to reinstall grub. There is another thread "reinstall grub from live cd" or something that explains this.

---

### Post by confused57 on 2007-06-27
> **ybh6336 said:**
> I was hoping that would work, but unfortunately it did not, still seeing only 'GRUB _' during startup. Pressing 'e' did not show anything, it just freezes at that screen. Any thoughts? Appreciate your time.

Thanks.

Here's the only thing I could find for this error:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_)

---

### Post by ybh6336 on 2007-06-27
Thanks for all your help guys. I re-installed GRUB using the following commands

[B][I]sudo grub
find /grub/stage1 - this returned (hd0,3)
root (hd0,3)
setup (hd0)
quit[/I][/B]

That did not help either, still the same problem.

Thanks confused57, but I could not make much out of that link :).
Any ideas? Or else it's time to switch back to good ol' Fedora I guess :).

Thanks again.

---

### Post by merlinus on 2007-06-27
Have you tried booting with SuperGrub disk:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If that works, then probably your problem can be fixed.

-merlin

---

### Post by ybh6336 on 2007-06-28
Thanks for the suggestion merlinus! I can now boot both Ubuntu and XP using Super GRUB disk. I tried the option to 'Repair GRUB in MBR' using the disk, but GRUB still cannot boot by itself.
Using the disk, I was even able to see my GRUB menu and could boot up both OSs from that menu. At least hope is back now :). Any ideas what I could do to fix GRUB in MBR?

Thanks a ton.

---

### Post by xzero1 on 2007-06-28
You might try to install grub using the super grub disk.

---

### Post by ybh6336 on 2007-06-28
Thanks, I'll try that tonight.

Regards.

---

