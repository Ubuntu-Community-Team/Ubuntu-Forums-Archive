---
title: "Unable to boot WinXP from GRUB"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Snoopyowns on 2007-08-26
Ok, so first off, here is my current setup. Windows XP on a SATA II into channel 1,  /dev/sda1 or (hd0,0) to GRUB. Then I installed Ubuntu to a second SATA I into channel 2, /dev/sdb1, or (hd1,0) to GRUB. I can boot into Ubuntu just fine, but when I select Windows XP, the screen clears and states "Starting Up..." and freezes right there. I can use XP's recovery console and fixmbr to boot back into windows, then to boot to Ubuntu i have to restore the GRUB from the live CD. Unfortunately that takes too long to switch like that :P 

Edit: Not sure if it makes a difference but i'm using the 64Bit Ubuntu 7.04.

No error messages come up at all when trying to boot to XP. I am fairly new to Ubuntu. Also, not sure if it may change anything, but I'm using an Abit KN9 SLI, BIOS revision 18. I had to upgrade to revision 18 as previously it wouldn't even boot to Ubuntu due to a bug in the BIOS that prevented the SATA I drive from showing in the BIOS. 


Here is the menu.lst.
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
# kopt=root=UUID=cc9818ce-7122-43c0-a3c7-e0bc8d6f3b8a ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cc9818ce-7122-43c0-a3c7-e0bc8d6f3b8a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cc9818ce-7122-43c0-a3c7-e0bc8d6f3b8a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cc9818ce-7122-43c0-a3c7-e0bc8d6f3b8a ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cc9818ce-7122-43c0-a3c7-e0bc8d6f3b8a ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader	+1
```

I have also tried having 'savedefault' after the 'makeactive' as well as 'boot' after the 'chainloader +1'. 

Here is the device.map in /boot/grub/.
```

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Here is the 'sudo fdisk -l'.
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864        5106     1951897+  82  Linux swap / Solaris

```

I'm not sure if there are any other things I need to put, just say so if there are. Any ideas? I've read through quite a few dual boot guides, and it seems like the settings are right, it just doesn't like Windows XP on this hardware.

---

### Post by be4truth on 2007-08-26
On my computer is another entry in menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
[COLOR="Red"]savedefault[/COLOR]
makeactive
chainloader     +1

Try to add "savedefault". Otherwise your posting is great. 

Maybe I found something something: Your Sata with XP: Why don't you plug that into your sata1 port and the Ubuntu sata drive in your sata 2 port?
Ihad once an XP installation on hdb and needed to boot it via a chain loader switch. I can't find this stuff but it is there somewhere. How to boot XP from a second harddrive...)
It could be because you XP sata drive is the second that Grub needs to be told to mirror the chain loading. Does that make sense to you?

---

### Post by Snoopyowns on 2007-08-26
Yep, I had that line in the menu.lst at one point in time too, then I removed it as a long shot to see if it would fix it based off of one of the examples in the menu.lst. Whether it's there or not, still has that problem :P Thanks for giving it a lookover though.

Hmm, due to the bios problems that i mentioned before with the Abit KN9 SLI that forced me to upgrade it to Revision 18, where they said in the patch notes "Enhanced compatibility with Linux", I think I'll do some checking at the Abit forums also. 

But if you guys have any other ideas, I'm all ears :)

Edited: Ok i'll remove that extra seperation that's not noted out in menu.lst, and i'll readd savedefault. I'll let ya know if it works here in about 15 minutes :P

---

### Post by Snoopyowns on 2007-08-26
> **be4truth said:**
> On my computer is another entry in menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
[COLOR="Red"]savedefault[/COLOR]
makeactive
chainloader     +1

Try to add "savedefault". Otherwise your posting is great. 

Maybe I found something something: Your Sata with XP: Why don't you plug that into your sata1 port and the Ubuntu sata drive in your sata 2 port?

Whoops, edited my original post for clarity. the SATA type II with XP is in channel (port) 1, and the SATA type I with Ubuntu is in channel (port) 2. 

I wasn't sure if the difference between the SATA types among the 2 drives might be screwing with GRUB, so I posted that info anyway :)

Also, i just commented out the lines you said, as well as readded 'savedefault'. It's still a no go.

---

### Post by Snoopyowns on 2007-08-26
Well, after scrounging all night on the web, I finally came across someone who had a similiar problem with the Abit KN9 SLI and GRUB.

[http://ubuntuforums.org/archive/index.php/t-262766.html]("http://ubuntuforums.org/archive/index.php/t-262766.html")

Looks like they solved it by using Lilo. Hrmm.. Well, I can definitely give it a go :P

---

### Post by Snoopyowns on 2007-08-26
My XP SATA is not second, it's first. It'd (hd0,0) so the map switch wouldn't apply.

---

### Post by Snoopyowns on 2007-08-26
Ok, so Lilo didn't work either. So then I installed GRUB into the MBR of /dev/sdb, and changed the boot order in the bios to point to /dev/sdb (the linux hard drive), and after changing around the menu.lst it was able to boot Linux, but still not Windows XP. 

So then, I booted the Win XP recovery CD and fixmbr on /dev/sda (winxp hard drive). So now when the bios points to the first channel hd (sda) it uses Windows Boot Loader and goes right into windows, when I point it to second channel (sdb) it'll go to Grub then I can go into Linux. That's about as close as I can get it at the moment. 

I'm not sure why only the Windows Boot Loader can boot Windows XP on this install. I had Ubuntu briefly about a year back and it worked fine, of course with entirely different hardware. lol. 

Well this is as satisfactory as I can get it, if anybody else has any ideas or knows something I don't, then please, speak up. :)

---

