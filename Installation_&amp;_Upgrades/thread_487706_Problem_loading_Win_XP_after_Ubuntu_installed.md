---
title: "Problem loading Win XP after Ubuntu installed"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by nirvman on 2007-06-29
Hello,

I am new here and I would appreciate any help to a solution.

I just installed Ubuntu and it loads fine. I even got my wireless connection going. However, when I select Windows in the Grub loader, the windows splash screen starts then the laptop reboots. It continues to do this until I go into Ubuntu.

So right now I can not log into windows.

I still have all the files intact and I can see them when I am in Ubuntu.

I just can't load it.

Thanks fot your help.

-Mike

I have seen other posts regarding this but no solution. I have already tried using my XP install recovery tool and using fixmbr. No luck.

---

### Post by confused57 on 2007-06-29
Open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

and

```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list
you can post just your Ubuntu & Windows boot entries

---

### Post by nirvman on 2007-06-29
output from sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4502    36162283+   7  HPFS/NTFS
/dev/sda2            4503        4515      104422+  83  Linux
/dev/sda3            4516        6484    15815992+  83  Linux
/dev/sda4            6485        7296     6522390    5  Extended
/dev/sda5            7176        7296      971901   82  Linux swap / Solaris
/dev/sda6   *        6485        7138     5253192   83  Linux
/dev/sda7            7139        7175      297171   82  Linux swap / Solaris

Partition table entries are not in disk order

output from gedit /boot/grub/menu.lst

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
# kopt=root=UUID=91df95af-4973-4c20-8cb4-da23cb77ce9e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=91df95af-4973-4c20-8cb4-da23cb77ce9e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=91df95af-4973-4c20-8cb4-da23cb77ce9e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Lamez on 2007-06-29
I also have the same problem, and I have yet to find a solution, but how did you get your wireless connectiong going? What type of adapter do you have?

---

### Post by nirvman on 2007-06-29
It was just there. I have a dell xps m140 and it worked from the start. I think it is an intel card
 
The probelm that i ahve with the reboot is nuts. i have yet to find a solution on boards and searching in google

---

### Post by Lamez on 2007-06-29
I know what you mean, I have found out that when you install Ubuntu, it messes with windows partition, at least I think.

---

### Post by vexorian on 2007-06-29
yoy probably think wrong else this would be a problem for almost everybody.

I once had a problem in which windows XP reboots when it is supposed to boot, I think it tends to happen with some drivers and I know that it happens when the main kernel files in C: don't have the correct attributes (hidden, readonly, system)
Something odd is that you have two swaps

did you defrag (on windows) before resizing the partition?

---

### Post by confused57 on 2007-06-29
> **nirvman said:**
> It was just there. I have a dell xps m140 and it worked from the start. I think it is an intel card
 
The probelm that i ahve with the reboot is nuts. i have yet to find a solution on boards and searching in google
Your current grub Window's entry looks like it should work...you can try this entry, using rootnoverify and removing the savedefault line:
```
title Windows NT/2000/XP (loader) test
rootnoverify  (hd0,0)
makeactive
chainloader +1
```

You can add the entry to the very end of your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
add the entry...quit & save...reboot & see if it works

Using rootnoverify works in some instances, when root doesn't...what I suggest is to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download & hopefully it will be able to boot your Windows or restore your Window's IPL to the mbr.

---

### Post by nirvman on 2007-07-01
Update.

I tried using super grub disk. and now the laptop says error loading operating system.

When I insert the WinXP install CD to try and reinstall windows it says it can't. The disk is not able to let me reinstall windows. I can still see the ntfs partition and everything is still on the disk.

Any guidance would be great. Seems like others have this problem but can not fix it.

---

### Post by confused57 on 2007-07-01
> **nirvman said:**
> Update.

I tried using super grub disk. and now the laptop says error loading operating system.

When I insert the WinXP install CD to try and reinstall windows it says it can't. The disk is not able to let me reinstall windows. I can still see the ntfs partition and everything is still on the disk.

Any guidance would be great. Seems like others have this problem but can not fix it.

If you have a Windows install cd(not a recovery), you might try restoring the Window's IPL to the mbr...press "r" for recovery mode, then enter FIXMBR...hopefully this will get you into Windows.

If you can boot to the Super Grub Disk, after you select your language, select Windows, then "Fix boot of Windows"...you might want to try the Windows install cd first.

---

### Post by nirvman on 2007-07-01
I tried that.  when i get into the recovery mode and type dir in the C nothing is there.

i tried using the fixboot in the super grub disk and now it says  " ntldr is missing  press any key to reboot" i can not even get back into ubuntu now.

this is rough

---

### Post by confused57 on 2007-07-01
> **nirvman said:**
> I tried that.  when i get into the recovery mode and type dir in the C nothing is there.

i tried using the fixboot in the super grub disk and now it says  " ntldr is missing  press any key to reboot" i can not even get back into ubuntu now.

this is rough
You can reinstall grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Here's some possible solutions for "ntldr missing":
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to)
the above  link provides another website with a utility for restoring your ntldr(you'll need a working Windows install to make the cd or floppy):
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Added:  Found this for ntldr is missing error:
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

---

