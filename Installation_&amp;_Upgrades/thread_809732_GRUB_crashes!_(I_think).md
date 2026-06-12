---
title: "GRUB crashes! (I think??)"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2008-05-27
I have a laptop that is setup to dual-boot Linux (Ubuntu 8.04) and Vista -- using GRUB in the MBR, and the GRUB menu to boot to Vista.  This has all been working well for days now.

Then today, after waking up from hibernate (the laptop, not me!), it suddenly wouldn't boot anymore.  I restarted the machine cold, and got the following:
1) BIOS/POST messages
2) Loading Grub
3) Grub stage 1.5 message
4) Black screen
5) Sudden reboot -- and back to line 1) above ...

It repeats this reboot cycle until I turn the machine off.  Frustrating, to say the least.

I have the GRUB menu.lst file setup to display the menu (in color), wait 10 seconds for a response, and if no response is given, boot to Vista.

I did boot to a Partimage CD and go to the console, mounted the Linux partition, to look for changes to the GRUB files -- but there are no file changes since last week, when everything worked OK.

I replaced the updated menu.lst file (the one modified to add Vista) with the original menu.lst file --hoping that would fix it.  But that has made no difference.

I could reload the MBR from the Vista DVD, and then reinstall GRUB and MBR contaning GRUB -- but I'd really rather find out what caused the failure first. Since no error message is displayed by GRUB, I was hoping it wrote an error log file to /boot/grub -- but there are no changes there since last week.

So, is there a log file anywhere I can examine to find out why GRUB is failing?

---

### Post by Rallg on 2008-05-27
Mark, pardon my ignorance, since I know little about problems that can arise with hibernation. But until the real experts find your message:

By any chance, did you install Grub to the linux-swap partition? I'm not even sure that can be done! But I can imagine that you hadn't needed to use swap until your system hibernated, in which case the memory would be written to swap (overwriting Grub, if it is there). No changes would be recorded.

You should also know that today, a kernel update to -.17 came out, but I doubt if that has anything to do with your problem, since -.16 is still in your files.

---

### Post by Mark Phelps on 2008-05-27
No, I used the LiveCD and since I have only one drive on this laptop, GRUB got installed to (hd0,0).  This overwrote the MBR (previously modified by Windows) so that I have to use GRUB to boot now -- which is OK, as long as it works.

Also, I should have mentioned that the laptop has returned just fine from hibernation numerous times over the last week.  It just started having problems today.

---

### Post by meierfra. on 2008-05-27
I suggest to run a file system check on your ubuntu root partition. 

See this  [post ]("http://ubuntuforums.org/showthread.php?t=564726#2")for some information how to use "e2fsck"

---

### Post by Mark Phelps on 2008-05-27
Actually .. ran the e2fsck commands, encountered no failures or bad blocks.

Then, went to the SuperGrubDisk website to download a new image ... and stumbled across this page:  [www.supergrubdisk.org/forum/index.php?topic=73.0 ](www.supergrubdisk.org/forum/index.php?topic=73.0 ) in which the administrator describes a problem where Vista overwrites the GRUB stage 1.5 code upon reboot.

To fix this, he's modified the SGD (SuperGrubDisk) to add a menu selection for rewriting the GRUB code to link stage 1 directly to stage 2, bypassing the overwritten code.

So, basically, it's yet another Vista "feature"!!

---

### Post by meierfra. on 2008-05-27
Thanks for the information.  I didn't know that SuperGrub has a solution for the case that Vista messes  with Grub. I always have been recommending EasyBCD  in that situation.

P.S Your link in the previous post is broken (although one can fix the address quite easily)

---

### Post by Mark Phelps on 2008-05-28
Thanks for the heads-up about the link -- is fixed now.

---

### Post by Mark Phelps on 2008-05-28
meierfra:

Sorry to report -- but the SGD fix is not permanent.  I thought it was because I rebooted several times last night into each of the OSs, and it worked fine every time.

Then, this morning, I needed to boot into Vista to apply a "critical" update, and when I rebooted, the machine went into the endless reboot loop -- again!  I've fixed it (again), but I don't want to be having to do this every day.

I have EasyBCD installed in Vista, so, please tell me how you fix this using EasyBCD.

Thanks.

---

### Post by meierfra. on 2008-05-28
Just start EasyBCD. I think it will install itself to the MBR
This link tells you how to add Ubuntu  to Vista Boot Menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

### Post by gasull on 2008-05-28
Could you post your /boot/grub/menu.lst?

---

### Post by Mark Phelps on 2008-05-28
meierfra:

Thanks for the link.  

Opening the program doesn't tamper with the MBR, or anything else, that I can tell.  

I read the link but I'm not sure how to proceed.  While the steps will add Ubuntu to the Vista boot loader, since I'm using GRUB at present, and installed that to the MBR, wouldn't I first have to overwrite the MBR using the Vista DVD and startup repair option? I didn't see anything in the EasyBCD screens about overwriting the MBR, just the Vista boot loader -- which is OK because I chainload that in the GRUB menu to boot Vista.

---

### Post by Mark Phelps on 2008-05-28
gasull:

menu.lst is posted below.  This was generated when I did the Manually Fix Boot of Linux (GRUB)(!NO stage 1_5) repair using the SuperGrubDisk (SGD):

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=ae6180dd-5e7f-4dc1-8f1e-77350e4eb979 ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=ae6180dd-5e7f-4dc1-8f1e-77350e4eb979 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet



title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=ae6180dd-5e7f-4dc1-8f1e-77350e4eb979 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ae6180dd-5e7f-4dc1-8f1e-77350e4eb979 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ae6180dd-5e7f-4dc1-8f1e-77350e4eb979 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I did a little minor tweaking, but most of the code is auto generated.

---

