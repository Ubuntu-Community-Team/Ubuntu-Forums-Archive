---
title: "Installed XP after/on to formated disk to dual boot with LTR"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by Yhor on 2010-04-21
I killed Win XP awhile back, but there are a couple games I need to format for Ubuntu to use, using XP to get there. 

What happened...
I have Ubuntu LTR.
I formatted disk to install XP.
I installed XP.
I can't boot into Ubuntu anymore unless from a live CD.
From Live CD, I can see my Ubuntu is still there, but from XP, disk manager it shows that space as empty (free). 

How can I dual boot, now? Please don't tell me I need to reinstall Ubuntu, I may cry. Any help is appreciated and my apologies if my search didn't get me the answers, the other similar problems I saw were in reverse order (Linux onto drive after XP). 

Thanks

---

### Post by oldfred on 2010-04-21
You should just have to reinstall grub legacy into the MBR. Besure to follow the directions for old grub as starting with Karmic we now also have grub2 which has different instructions.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Yhor on 2010-04-21
Awesome. You rock  :guitar:.

Sorry for my noob questions, but now how do I boot to XP when needed?
:oops:

---

### Post by takisan on 2010-04-21
It should just prompt you at startup, if not, type update-grub or grup-update (I forget which one) into the prompt that admins GRUB.

---

### Post by Yhor on 2010-04-21
I ran 'update-grub' in term and it seemed to update fine, but still no choice to use xp when I restarted my computer. I'll search around, it's probably around here somewhere. Thanks for the help :).

---

### Post by oldfred on 2010-04-22
Old grub often found the windows and added it to the menu.lst but sometimes we had to manually add entries. If you need help I would need more info but an entry would be like this:

title Windows 7 Ultimate, chainloader (on /dev/[COLOR=DarkRed]sda3[/COLOR])
rootnoverify ([COLOR=DarkRed]hd0,2[/COLOR])
savedefault
chainloader +1

You can change title to whatever, but have to have correct (hdx,y) for x= drive and y = partition starting count at 0 where drive numbering sda1 starts at drive a (=0) and partition 1 (=0 in grub legacy)

---

### Post by Yhor on 2010-04-22
I'm still beating my head against the wall, thanks for replying.

I think this is the related area in menu.lst I need to edit? (already edited as suggested, no results)
```
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
# title        Windows XP
# root        (hd0,2)
# savedefault
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
# kopt=root=UUID=4905f30d-a84c-4e44-886e-281c91bf1c03 ro

```

Do I need to un-comment something, or is there something I need to add? If so, where to add, beginning, middle, end of file? I'm really sorry, I truly wanted to be done with Windows, but alas...

---

### Post by oldfred on 2010-04-22
You normally add the windows entry at the bottom of menu.lst below the automagic line. If you want windows first in the menu about 1/3 the way down is the start of the automagic area and it has to be above that. Every kernel update rewrites the entire automagic area so any entries inside that area will be erased.

If you need more help post

```
sudo fdisk -l
```

and the entire menu.lst in code tags (# in edit panel )

---

### Post by Yhor on 2010-04-22
Thanks Fred.

fdisk..
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb00aa65e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      101986   819202513+  83  Linux
/dev/sda2   *      101987      107624    45287235    7  HPFS/NTFS
/dev/sda3          107625      120372   102398310   83  Linux
/dev/sda4          120373      121601     9871942+   5  Extended
/dev/sda5          120373      121601     9871911   82  Linux swap / Solaris
```Menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows XP
# root        (hd0,2)
# savedefault
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
# kopt=root=UUID=4905f30d-a84c-4e44-886e-281c91bf1c03 ro

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=4905f30d-a84c-4e44-886e-281c91bf1c03 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=4905f30d-a84c-4e44-886e-281c91bf1c03 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=4905f30d-a84c-4e44-886e-281c91bf1c03 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=4905f30d-a84c-4e44-886e-281c91bf1c03 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I appreciate your help here, I hope I can pass some of this on to someone  one day myself.

---

### Post by oldfred on 2010-04-22
after this:
### END DEBIAN AUTOMAGIC KERNELS LIST

Just paste this at the end:

title Windows XP, chainloader (on /dev/[COLOR=DarkRed]sda2[/COLOR])
rootnoverify ([COLOR=DarkRed]hd0,1[/COLOR])
savedefault
chainloader +1

We used to use root but rootnoverify seemed better for Vista & 7. I think for XP it does not matter.

It looks like you have hiddenmenu, so you will not see the menu unless you press escape.

I also like to change this line so kernel updates only keep 2.
from:
# howmany=all
to:
# howmany=2

---

### Post by Yhor on 2010-04-22
What a lifesaver. Thanks a lot Fred, all is well in dual boot land.

 I just need to be faster with my esc button pressing, it goes by too fast and I have to anticipate when it comes, or it's already gone.


Edit: Doh! I just edited timeout from 3 to 6 and everything is great. Thanks again!

---

### Post by oldfred on 2010-04-22
Glad you got it working. 

Except now Karmic and Lucid use grub2 which is totally different. Something new to learn.

---

### Post by Yhor on 2010-04-22
I'll get there, but the LTS versions is where I 'think' I belong until I get more fluent. I tried Jaunty, but the lockups sent me packing for Hardy.

Anyway, thanks for the help. :)

---

