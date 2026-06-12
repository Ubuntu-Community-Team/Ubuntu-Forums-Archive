---
title: "Issues with Dual Boot w/ FreeBSD 5.3"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by s0c0 on 2005-06-06
I am trying to setup a dual boot system with Ubuntu 5.0 and FreeBSD 5.3.  BSD is installed on the second portion of the hard drive and Ubuntu is installed on the fist portion.  I am able to boot into Ubuntu, but GRUB is not finding my FreeBSD partition.  I am unable to mount it because I think I am to incompetant.  It keeps asking me to specify a file system type.  Anyways I know there is a way to place the proper string in the grub configuration file.  Can someone please point me to a good reference or walk me through this, thanks!

---

### Post by mingus on 2005-06-06
The command
#update-grub
rebuilds the grub control file, menu.lst.  The command should find your other installation and set it up.  It will do so by explicitly pointing to the FreeBSD root location.  There is another method of doing this, called chain-loading, that requires that whatever boot loader is used with FreeBSD is installed on the same partition as its /boot directory.

This is all documented to some extent in the menu.lst file.  Suggest you take a look there, and if needed, post the file back to this thread.

---

### Post by s0c0 on 2005-06-07
Okay when I installed FreeBSD I did not install the bootloader thinking that grub would auto-detect.  Update-grub did not find FreeBSD.  I tried entering the grub prompt and adding it, but whatever commands I had been told to use were not doing the trick either.  *Sigh* Any help would be appreciated!

**Here is what my partitioning scheme looks like:**
[INDENT]
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       29070    14651248+  83  Linux
/dev/hda2           29071       30425      682762+  82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/hda3   *       30425       59560    14684197+  a5  FreeBSD[/INDENT]


**Here is what /boot/grub/menu.lst looks like:**

[INDENT]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
[/INDENT]

---

### Post by mingus on 2005-06-07
Yep, FreeBSD is certainly not there.  I'm not familiar with FreeBSD, but if the setup  works like other distros, you have one or maybe two choices:

1.  Edit the menu.lst file to *explicitly* load the boot image.  So that would be a new section something like:

title FreeBSD
root (hd0,2)
kernel /boot/<kernel filename> root=/dev/hda3 ro quiet splash
initrd /boot/<boot initialization filename>
savedefault
boot

2.  Edit the menu.lst file to *chain-load* the FreeBSD loader.  This assumes that you have installed GRUB or LILO to the /dev/hda3 partition; sounds like you didn't do that.  So you would either need to use another method to get into FreeBSD and do that, or possibly you could within Ubuntu mount hda3 to a directory, chroot into that directory, and then do the FreeBSD loader installation from there.

title FreeBSD
root (hd0,2)
makeactive
chainloader +1

Probably #1 is easier.  This is the default method in Debian (#2 is the default in many other distros).

If you run #update-grub again, I think you will lose your additions.

So after getting menu.lst edited, you do
#grub-install
which will re-write the MBR

Given you are having a problem with this, you might consider temporarily bypassing the MBR and using a boot floppy instead (assuming your system can do that).  If your MBR gets hosed by the grub install, you can recover w/o reinstalling but its a bit of a nuisance.  All you need to do is add a line for fd0 to the /boot/grub/device.map file, and then do:
#grub-install /dev/fd0

Make sense?

---

