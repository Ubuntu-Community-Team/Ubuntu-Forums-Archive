---
title: "Grub -- error 11"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by j.hill on 2005-08-15
This morning I reinstalled Ubuntu (after it melted down unexpectedly -- but that's another story).  I set up Grub to dual boot with W2K, but it refuses to do this thing.  Instead I get "error 11:  unrecognized device string."

It boots into Linux just fine and there seem to be no problems with any of my devices.  Moreover, I had a perfect dual-boot setup the first time I installed Ubuntu, and I did everything *exactly* the same way this time.  

I am mystified.  Do I need to edit something really obscure in /usr/lib/joke/sadistic?

---

### Post by amohanty on 2005-08-15
[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)


Possibly the entry for a drive in your /boot/grub/menu.lst is messed up. Drop into grub interactively and change.

AM

---

### Post by j.hill on 2005-08-16
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows 2000 Professional
root            (hd1,0)
map             (hd0)(hd1)
map             (hd1)(hd0)
savedefault
makeactive
chainloader     +1
```


I think this is the relevant part of /boot/grub/menu.lst, but I can't see where the error is.  What am I missing?

---

### Post by amohanty on 2005-08-17
That seems fine, can you post the entire file?
Also I see map directives. The ones in your snippet kinda implies that you have two separate HDDs and windows is on the primary slave? Is that the case.

AM

---

### Post by j.hill on 2005-08-17
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows 2000 Professional
root            (hd1,0)
map             (hd0)(hd1)
map             (hd1)(hd0)
savedefault
makeactive
chainloader     +1
```

Above is the whole /boot/grub/menu.lst.  And to answer your question, yes, I have Ubuntu on the master drive and W2K on the slave drive.

Also:  here are a couple more lines from the aborted Windows boot, which I forgot to write down before:

```
root (hd1,0)
Filesystem type unknown, partition type 0x7
map (hd0)(hd1)
```

don't know if this is relevant....

---

### Post by amohanty on 2005-08-18
Did you install GRUB in MBR?
Now in theory you would need the map .... lines to boot into win. Have you tried removing it? AFAIK it should fail to boot into win, because NT loader expects to be on the primary master, but try it anyway to see what the error message says. If its not a NT loader error, then grub is fscked up, I would suggest reinstalling grub.

AM

---

### Post by j.hill on 2005-08-18
If I remove the mapping lines, and then try to boot into Windows, I get:

```
root (hd1,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```

Which is what I originally used to get, on my first dual-boot installation; but that time adding the mapping lines fixed it.

---

### Post by amohanty on 2005-08-18
Well the only thing I can think of is that if on the slave theres only one partition you could try:
root            (hd1)
instead of 
root            (hd1,0)

Put the map lines back in and try or else you might have to reinstall grub from Ubuntu.

AM

---

### Post by j.hill on 2005-08-20
Can I do that without reinstalling the whole system?  If so, how?

---

### Post by amohanty on 2005-08-25
[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

HTH
AM

---

