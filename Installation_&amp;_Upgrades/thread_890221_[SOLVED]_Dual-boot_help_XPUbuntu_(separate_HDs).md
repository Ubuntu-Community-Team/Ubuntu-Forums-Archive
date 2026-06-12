---
title: "[SOLVED] Dual-boot help XP/Ubuntu (separate HDs)"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by mastaphoo on 2008-08-14
Okay, I am fairly new to Linux and wanted to try it out again. I made space on my 400GB SATA HD and resized it during the Ubuntu install to be split into two, one for Ubuntu and the other with all the data that was on it (not Windows though). The install went perfectly fine. 
Now, my XP is on an 80GB SATA HD, and the computer defaulted to that when I restarted. I figured this was normal, but when I tried to boot to the 400 GB to get to Ubuntu, I got the "Boot device not recognized" message, meaning (I think) that the GRUB loader failed to write to the 400. XP wasn't recognized during the install, so I figured it would just write to the 400. What can I do to get the GRUB loader to come up with both Ubuntu and XP? Can I just use Super GRUB Disc to put GRUB on my 80GB? Thanks in advance

---

### Post by Pumalite on 2008-08-14
This will help:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by louieb on 2008-08-14
The [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") would  probably be the easiest.

Or faster Boot to a live CD Ubuntu, Knoppix, System Rescue - doesn't matter as long as it has grub. 
For the Ubuntu live cd open Applications > Accessories > terminal 
And get a** grub> **prompt

```
sudo grub
```now have grub find where it is installed 

```
find /boot/grub/stage1
```will return something in the form of (hd#,#).  use that to set the grub root

```
root  (hd#,#)
```and finally change the MBR of the drive to boot to GRUB in your Ubuntu install

```
setup (hd#) 
```

Get that much done and get Ubuntu booting then we can go through how to add XP to the grub menu.

Hello Pumalite. See you beat me. Thats a good thread for a person new to dual booting.

---

### Post by mastaphoo on 2008-08-14
I think I understand, but I can't get Ubuntu booted in the first place to edit the GRUB loader.... What am I missing? Can I install the GRUB loader to the 400 with Super GRUB Disc? I don't want to mess any of this up...

---

### Post by Pumalite on 2008-08-14
Make the 400 first in the boot order in BIOS and then reinstall Grub following this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I advise you to read the link I gave you. It's very informative.

---

### Post by mastaphoo on 2008-08-15
Okay, I got GRUB back on hd3 (the 400) with the instructions above. Now, when I try to boot to any of the Ubuntu options from there, I get an error message: "Error 22: No such partition"
When I try to boot to XP (no idea how it got there...), I get "NTLDR missing. Restart now" error.
I am looking at the menu.lst file in the grub folder on the Ubuntu partition now, and it all looks correct. Here's what's there (minus comments of course):

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e816250-8f34-45c6-b9da-d7cded0df554 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e816250-8f34-45c6-b9da-d7cded0df554 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd3,4)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


I have not changed any of it. hd2 is my 80GB with XP on it, hd3 is the one I split and put Ubuntu on.
I'm totally confused. :confused:

---

### Post by Pumalite on 2008-08-15
Post:
sudo fdisk -lu

---

### Post by mastaphoo on 2008-08-15
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a751a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x122ae170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67f4faae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e064144

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   427248674   213624306    7  HPFS/NTFS
/dev/sdd2       427248675   781417664   177084495    5  Extended
/dev/sdd5       427248738   766959164   169855213+  83  Linux
/dev/sdd6       766959228   781417664     7229218+  82  Linux swap / Solaris

---

### Post by mastaphoo on 2008-08-15
I'm guessing I have to change the hd2 and hd3 in the menu.lst file to sdc and sdd respectively?

Edit: I can't edit and save menu.lst from the live cd.... any workaround? (if I need to, that is)

---

### Post by Pumalite on 2008-08-15
Post:
cat /boot/grub/menu.lst
(from the corresponding partition)

---

### Post by mastaphoo on 2008-08-15
All of it? It's a lot....

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
# kopt=root=UUID=0e816250-8f34-45c6-b9da-d7cded0df554 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e816250-8f34-45c6-b9da-d7cded0df554 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e816250-8f34-45c6-b9da-d7cded0df554 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd3,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by louieb on 2008-08-15
at least. your menu.lst and the output of fdisk -l are consistent.   

Looks like your pretty close just need to do a little tweaking.

(h3,4)   in grub is /dev/sdd5 in the fdisk output. (Ubuntu)
(hd2,0) in grub is /dev/sdc1 if the fdisk output ( XP).

The problem may be that somehow the boot order of your hard drives may be different when you boot to the hard drive. 

To test this. boot to the grub menu on the hard drive. and press **c to get the grub> prompt. **

now enter ```
find /boot/grub/menu.lst  

```

Whatever that returns will be the / (root) partition of your Ubuntu installation on the  hard drive.

Would like to know what it returned.

Also are all 4 of your hard drive internal SATA drives? 
Any of them external?
Any of then IDE?

Haven't used a Ubuntu live CD in quite a while to edit a file on the hard drive. (I use Knoppix or Puppy for that).  I'll dig one out and figure out how to get it to open a file so that you can edit it.

---

### Post by mastaphoo on 2008-08-15
It returned (hd0,4)
I'm guessing I have to edit the menu.lst file to see it as (hd0,4) instead of (hd3,4)?
How can I edit the file then?

To answer louieb: I have 2 internal SATA (80GB with XP and 400GB with 2 partitions: Ubuntu/NTFS data) and 2 internal IDE (160 GB and 200 GB, both NTFS data).

---

### Post by mastaphoo on 2008-08-15
In some looking around, I saw that device.map contains:```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

Will changing this work? I can't edit this either.... nor can I find any way to get permissions to do so.... eek :P

---

### Post by Pumalite on 2008-08-15
gksudo gedit...xxx
Backup first

---

### Post by confused57 on 2008-08-15
> **mastaphoo said:**
> In some looking around, I saw that device.map contains:```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

Will changing this work? I can't edit this either.... nor can I find any way to get permissions to do so.... eek :P
If you're getting a grub boot menu when you boot first to your Ubuntu drive, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd3,4) to (hd0,4), press "enter", then "b" to boot.  This is temporary if it works.

---

### Post by mastaphoo on 2008-08-15
Okay, thanks tons. I got Ubuntu booting from GRUB (permanently) and I'm about to start messing with the XP one to get that to boot. Thanks!

---

