---
title: "Windows XP won't load on Dual boot Ubuntu 8.04"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by venir on 2008-10-17
I just intalled 8.04 along side existing WinXP PRO and now when I select Windows XP in grub, it says "Starting up" and just hangs until I do a hard reboot. Any help would be much appreciated. I ran fdisk -l and got:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fd39842

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24078   193398502    7  HPFS/NTFS
/dev/sda2           34465       60801   211551952+   f  W95 Ext'd (LBA)
/dev/sda5           34465       34726     2104452   82  Linux swap / Solaris
/dev/sda6           34727       60801   209447406   83  Linux




My /boot/grub/menu.lst contents:



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
# kopt=root=UUID=5d24a7d1-40d7-4b97-a4d4-b14a659af056 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5d24a7d1-40d7-4b97-a4d4-b14a659af056 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5d24a7d1-40d7-4b97-a4d4-b14a659af056 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5d24a7d1-40d7-4b97-a4d4-b14a659af056 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5d24a7d1-40d7-4b97-a4d4-b14a659af056 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-10-17
First, boot your Windows Install CD, go to the "recovery console" and run:
```
fixboot
chkdsk /r
```
You should run chkdsk as many times as it takes until it reports no errors. After that reboot, and see if Windows will boot. If it still won't boot, then boot into Ubuntu, open a terminal (applications > accessories > terminal), and do the following:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. :)

---

### Post by venir on 2008-10-17
Thanks so much for the quick reply. After running testdisk as you specified it will now attempt to load Windows but I get a BSOD that goes away before I can see the error code.

One thing I forgot to mention is that the WinXP that I am using on this disk is cloned from an older hard drive. It loaded fine on its own before I installed Ubuntu, but I thought that may be the source of my issues.

---

### Post by caljohnsmith on 2008-10-17
If you at least getting as far as a BSOD, then you most likely don't need to worry about running fixboot, but I would strongly recommend running the chkdsk command to see if it can fix your file system. If you don't have a Windows Install CD, you can download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Give that a shot and let me know if that changes anything. :)

---

### Post by venir on 2008-10-18
Fixboot repaired the MRB and chkdsk did find and fix some bad sectors and now Windows boots fine. Thank you so much for your help!!

---

### Post by caljohnsmith on 2008-10-18
That's great that Windows is working again, and glad I could help out. Cheers and have fun with it. :)

---

