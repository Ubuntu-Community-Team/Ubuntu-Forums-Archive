---
title: "Cannot boot after install on Edgy"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by cbelanger on 2006-12-07
Tried installing Edgy with LiveCD and alternate with same result.  The regular install, on the remaining space (dual boot with winxp) went well.  I rebooted, and Ubuntu stays stuck on the progress bar before opening a shell (BusyBox).

I've booted in diag mode, I see the following error before it opens a shell:

> ALERT! /dev/sde2 does not exist!  Dropping to a shell

It appears just after my USB card reader is initialised (I see my SD card reader as /dev/sde.

Why would it hang on sde2?  What's this error about?  How can I fix?  My system is a stock Dell 9200C.

Thanks
Carl

---

### Post by taurus on 2006-12-07
Are you trying to install Ubuntu on your USB card reader?  From the LiveCD, what is the output of this command?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kweiner on 2006-12-09
> **cbelanger said:**
> Tried installing Edgy with LiveCD and alternate with same result.  The regular install, on the remaining space (dual boot with winxp) went well.  I rebooted, and Ubuntu stays stuck on the progress bar before opening a shell (BusyBox).

I've booted in diag mode, I see the following error before it opens a shell:



It appears just after my USB card reader is initialised (I see my SD card reader as /dev/sde.

Why would it hang on sde2?  What's this error about?  How can I fix?  My system is a stock Dell 9200C.

Thanks
Carl

I also have a Dell 9200C and had a similar problem after doing a network installation (because my CDROM wouldn't work during installation).  I found out that the grub configuration had /dev/sd1 when it should have had /dev/sda1.  From your BusyBox shell, try mounting /dev/sda1 and then open up /boot/grub/menu.lst and change any occurances of /dev/sde1 with /dev/sda1.  Then reboot.  It worked for me.

---

### Post by cbelanger on 2006-12-12
Ok after many tryout, I managed to reinstall a working copy of it (live cd, regular installation, don't understand why it worked this time).  But the problem seems to be elsewhere, as i try to start a different kernel the same problem arise.



> **taurus said:**
> Are you trying to install Ubuntu on your USB card reader?  From the LiveCD, what is the output of this command?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

```
cbelanger@technik:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       29676   135974160   83  Linux
/dev/sda3           29677       30394     5767335    5  Extended
/dev/sda5           29677       30394     5767303+  82  Linux swap / Solaris
```

---

### Post by cbelanger on 2006-12-12
> **kweiner said:**
> I also have a Dell 9200C and had a similar problem after doing a network installation (because my CDROM wouldn't work during installation).  I found out that the grub configuration had /dev/sd1 when it should have had /dev/sda1.  From your BusyBox shell, try mounting /dev/sda1 and then open up /boot/grub/menu.lst and change any occurances of /dev/sde1 with /dev/sda1.  Then reboot.  It worked for me.

menu.lst seems to contain good informations:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
```

---

### Post by taurus on 2006-12-12
Why don't you post the whole /boot/grub/menu.lst here then!!!

```
cat /boot/grub/menu.lst
```

---

### Post by cbelanger on 2006-12-12
To be more precise, here is diag before it open the busybox 

```
USB mass storage support registered.
Done.
Begin:Waiting for root file system ... ...
scsi 0:0:0:0 Direct-Access TEAC USB HS-CF Card
scsi 0:0:0:1 Direct-Access TEAC USB HS-xD/SM Card
scsi 0:0:0:2 Direct-Access TEAC USB HS-MS Card
scsi 0:0:0:3 Direct-Access TEAC USB HS-SD Card
sd 0:0:0:0: Attached scsi removable disk sda
sd 0:0:0:1: Attached scsi removable disk sda
sd 0:0:0:2: Attached scsi removable disk sda
sd 0:0:0:3: Attached scsi removable disk sda
Done.
ALERT! /dev/sda2 does not exist. Dropping to a shell
```

which makes me think...  would it be that under this particular bios it dosn't detect the HD?
Is there a dmesg that the system logs when going into Busybox?

PS ill post my menu.lst file in a sec

---

### Post by cbelanger on 2006-12-12
```

cbelanger@technik:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=11b9bff5-c318-4434-9dc5-9df33ca1aebc ro
# kopt_2_6=root=/dev/sda2 ro

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

title           Ubuntu, kernel 2.6.19.1-custom
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.19.1-custom root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.19.1-custom
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.19.1-custom (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.19.1-custom root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.19.1-custom
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by taurus on 2006-12-12
Can I have a look at your /etc/fstab too?

```
cat /etc/fstab
```

---

### Post by kweiner on 2006-12-13
Can you explain what diag mode is?  Is that something I should try?  I was never able to get the Edgy Live CD to come up on my Dell 9200c.

---

### Post by cbelanger on 2006-12-13
> **taurus said:**
> Can I have a look at your /etc/fstab too?

```
cbelanger@technik:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=11b9bff5-c318-4434-9dc5-9df33ca1aebc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=944ec150-4b95-4c3e-92f2-bbb18f6640a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by cbelanger on 2006-12-13
> **kweiner said:**
> Can you explain what diag mode is?  Is that something I should try?  I was never able to get the Edgy Live CD to come up on my Dell 9200c.

I was able to boot the live CD though...

What I mean by diag mode is when the grub loader is up you can select "recovery mode" for your kernel, it shows you the bootup sequence, where it hang, etc.

---

### Post by cbelanger on 2006-12-13
I *think* I've found my problem
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

I'll try when I'm back home and I'll let you know!

EDIT : okay didn't solved it but I think I'm getting closer
Replacing /dev/sda2 in menu.lst with the UUID=blabla from the fstab changed the error at the bootup

Same error as it can't find the drive.

So it must be something regarding the drive detection

Any thoughts?

---

### Post by cbelanger on 2006-12-18
Bump!

---

### Post by permieshane on 2007-01-09
I am having the exact same problem as cbelanger.  Can anyone help?? PLEASE.

---

