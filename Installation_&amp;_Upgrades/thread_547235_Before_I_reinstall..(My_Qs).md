---
title: "Before I reinstall..(My Qs)"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by iAndrew on 2007-09-09
Okay, I'm about to reinstall ubuntu (feisty) on my desktop. Currently there are 2 hdds.

1 320 gig (w/ Windows XP Prof)
1 80 gig (w/ Ubuntu Feisty)

As I've read over and over it is always good to install windows before linux. So I was wondering if I had to do anything pre/post after my reinstallation of ubuntu. I also heard I have to reconfigure the grub manager ? (The 80gig hdd always boots first in bios).

Please feel free to ask any questions about cpu, specs, etc.

---

### Post by aJayRoo on 2007-09-09
If you are re-installing Ubuntu 'over the top' of your previous Ubuntu install and you already have Windows XP installed then I don't foresee any special issues. You can do exactly the same as you did to install Ubuntu the first time. People say to install Windows first because  if you install XP after Ubuntu it will overwrite GRUB with the Windows boot loader. When you re-install, at the install GRUB stage you will be given a list of other OS on your machine (which should just include Windows on your setup), if this is the case then you can go ahead and install GRUB to the MBR (default) and there should be no extra setup required. Hope that helps.

---

### Post by iAndrew on 2007-09-09
okay. Well, I reinstalled it using the livecd. I didn't not change any bios settings. But, it'll keep booting windows. I don't know how to access Ubuntu or Grub.

---

### Post by merlinus on 2007-09-09
You might try supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If you need more info on its use:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by iAndrew on 2007-09-09
Okay let me just explain what I did.

So, I have 2 hdds. 1 With windows xp, 1 with ubuntu feisty.

I deleted all the partitions off the ubuntu hdd, and made new ones.

I then installed linux through the liveCD. I did not see grub setup/configs anywhere in that installation.

I can boot ubuntu linux though the liveCD.

Now on bootup, it normally boots windows xp.

---

### Post by merlinus on 2007-09-09
OK.  Post results of

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

from a terminal whilst booted into ubuntu.

---

### Post by iAndrew on 2007-09-09
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+  82  Linux swap / Solaris
/dev/sda2              63        9729    77650177+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sdb2           19123       38913   158971207+   7  HPFS/NTFS

```

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
# kopt=root=UUID=787fff23-31ba-4786-8552-c2ca372451f1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=787fff23-31ba-4786-8552-c2ca372451f1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=787fff23-31ba-4786-8552-c2ca372451f1 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Okay also forgot to mention this (but I really don't think its that relevant)

MY 320 gb is partitioned into 2 disks. 1 contains the windows xp prof os, and the other just has a bunch of documents/photos/files

---

### Post by merlinus on 2007-09-09
You might try changing root in the windows stanza to rootnoverify.

Also post /boot/grub/device.map

---

### Post by iAndrew on 2007-09-09
uh..I'm not windows-savy either, what does that mean.

---

### Post by merlinus on 2007-09-09
title           Microsoft Windows XP Professional
[COLOR=Red]rootnoverify[/COLOR]            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by iAndrew on 2007-09-09
How can I do that ?

---

### Post by merlinus on 2007-09-09
In a terminal:

```

gksudo gedit /boot/grub/menu.lst

```

Then restart.

---

### Post by iAndrew on 2007-09-09
It still loads windows first.

---

### Post by merlinus on 2007-09-09
So you are not seeing the grub menu?

---

### Post by iAndrew on 2007-09-09
Yeah. I don't see the grub menu. On boot up, I see the bios load, then it proceeds directly to windows xp. However, as I stated before the grub menu loads when I use **the liveCD and pick the "boot from hard disk" option**

---

### Post by merlinus on 2007-09-09
Did you try using supergrub to reinstall grub to the mbr, following the links I posted awhile ago?

Also, what is the boot order of your hdds in BIOS?

---

### Post by iAndrew on 2007-09-09
No. Honestly, I was being cocky. I read part of it and thought it was gonna replace grub or something like that. Sorry merlinus, for not taking your advice earlier. I will try using supergrub now.

Sorry

---

### Post by iAndrew on 2007-09-10
Okay merlinus. That was one hell of a challenge. I really didn't understand how to use it.. Must be my 14yr old brain or something..

Anyways. After about 5~10 mins I think I got it working.

But, when I boot WinXP I have a **long shutdown time** that I didn't have before.

Any ideas?

---

