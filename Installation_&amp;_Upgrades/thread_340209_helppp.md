---
title: "helppp"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by spkenn5 on 2007-01-16
guys can you help me, i installed a windows xp sp2 and then after that, i installed this ubuntu. and now i can't go back to my windows, i was trying to dual boot my system

here's the partitions.

C: Windows
D: Windows Files
E: WIndows Files
F: Ubuntu

Guys how do i get myself back to windows and be able to select which OS to boot to.

thanks

---

### Post by Sef on 2007-01-16
> here's the partitions.

C: Windows
D: Windows Files
E: WIndows Files
F: Ubuntu

Open the terminal (Applications > Accessories > Terminal) and type this:

```
sudo fdisk -l
```

Then paste the results here.

---

### Post by spkenn5 on 2007-01-16
Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hdc2            7650       19929    98639100    f  W95 Ext'd (LBA)
/dev/hdc5            7650       10199    20482843+   7  HPFS/NTFS
/dev/hdc6           10200       14023    30716248+   7  HPFS/NTFS
/dev/hdc7           14024       19929    47439913+  83  Linux


there.

please i need to get back to windows ASAP

thanks

---

### Post by Sef on 2007-01-16
Have to go into grub and fix it.   Would havet to check for a thread on that.  Will give you one if I can find one.

Up date: Some [directions]("http://ubuntuforums.org/showthread.php?t=69500&highlight=GRUB+%2B+No+Windows") are quoted in this post.

---

### Post by spkenn5 on 2007-01-16
thanks ill be waiting.

---

### Post by meng on 2007-01-16
Type:

sudo nano -B /boot/grub/menu.lst
(enter your user password when prompted)

Add the following section to the end of the file and save it:

title Windows XP
rootnoverify (hd2,0)
makeactive
chainloader +1

Now reboot and Windows should be an option.

---

### Post by spkenn5 on 2007-01-16
will do that now, how do i save the modified menu.lst?

thanks

---

### Post by meng on 2007-01-16
ctrl-x

---

### Post by spkenn5 on 2007-01-16
stay with me guys, ill be back trying to reboot now..

---

### Post by spkenn5 on 2007-01-16
it says selected disk was not found.

btw i use one harddrive and create those partitions.

sorry for not being clear

---

### Post by meng on 2007-01-16
Please post your menu.lst here.

cat /boot/grub/menu.lst

---

### Post by spkenn5 on 2007-01-16
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdc7 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdc7 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
savedefault
boot

title           WindowsXP
rootnoverify    (hd2,0)
makeactive
chainloader     +1


### END DEBIAN AUTOMAGIC KERNELS LIST

thankss

---

### Post by meng on 2007-01-16
Well change (hd2,0) in that last section to (hd0,0)
It doesn't make sense to me, /dev/hdc should be (hd2,?) and /dev/hda should be (hd0,?), but if grub is finding your linux partition on (hd0,6) then it should find your windows partition on (hd0,0)

---

### Post by spkenn5 on 2007-01-16
let me try rebooting now

thanks

---

### Post by spkenn5 on 2007-01-17
thanks meng, it works.

im finally back on XP

Thanks!

---

