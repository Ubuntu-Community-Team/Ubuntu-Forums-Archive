---
title: "Installed Ubuntu, cannot load XP"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by arwilson529 on 2008-03-23
Howdy,

I recently decided to start fresh and create a dual-boot XP and Ubuntu computer.  I installed XP first, filled up the whole HD with it.  Then I resized the partition and installed Ubuntu.  Ubuntu works just fine but XP won't load.  When I select XP in Grub, it just says "Disk System Error, press ctrl-alt-del to restart."  I can access the partition in Ubuntu and everything seems fine, and the Grub menu file is properly set up (XP on hda0,0 ).  

I tried loading XP in Super Grub Disk, same error; and I tried the Fix MBR + Win option, same error.  Has anyone seen this error before and can at least point me in the right direction on how to fix it?  I've set up XP and Ubuntu like this before and can't see where I screwed it up this go around.  Thanks.

---

### Post by Pumalite on 2008-03-23
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by arwilson529 on 2008-03-23
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   170176544    85088241    7  HPFS/NTFS
/dev/sda2       170176545   287932994    58878225   83  Linux
/dev/sda3       287932995   293041664     2554335    5  Extended
/dev/sda5       287933058   293041664     2554303+  82  Linux swap / Solaris
arwilson529@Ubuntu64:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=695ade66-e043-440c-a309-001aec4673c4 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=695ade66-e043-440c-a309-001aec4673c4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=695ade66-e043-440c-a309-001aec4673c4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Pumalite on 2008-03-23
Change this:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

To this:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Then:
gksudo gedit /boot/grub/menu.lst
Edit, save and exit. Reboot.

---

### Post by arwilson529 on 2008-03-23
No luck, "a disk read error has occurred, press ctrl-alt-del to restart"

This is the menu.lst XP entry now:

title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Pumalite on 2008-03-23
Are you still able to get into Ubuntu?

---

### Post by arwilson529 on 2008-03-23
Yeah, Ubuntu works just fine.

---

### Post by Pumalite on 2008-03-23
Try reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Is it a Laptop or a Desktop?

---

### Post by arwilson529 on 2008-03-23
Desktop, and I reinstalled Grub after using the Super Grub Disk "MBR + Win" option.  That wiped out Grub and I reinstalled it via Super Grub Disk.

---

### Post by Pumalite on 2008-03-23
How did it go?

---

### Post by arwilson529 on 2008-03-23
No good.  I went for the Fix MBR - Win, rebooted, thinking that would just kick the old Win bootloader in.  Same error.  So I reinstalled grub, and got the same error when I selected XP.  After checking my partitions to see if I had two actives (I don't, the XP partition is active) I realized I was in over my head and hit the forum, lol

---

### Post by Pumalite on 2008-03-23
I don't know what to tell you. Your fdisk match your menu.lst

---

### Post by arwilson529 on 2008-03-23
I appreciate the help regardless.

---

### Post by adrian15 on 2008-03-25
> **arwilson529 said:**
> No luck, "a disk read error has occurred, press ctrl-alt-del to restart"

Search the internet for a howto on how to fix windows or repair a windows installation with a windows install disk.

Once you have fixed the windows installation recover your grub with super grub disk.

adrian15

---

### Post by arwilson529 on 2008-03-25
If it were that easy I wouldn't have a problem, lol.  Unfortunately it appears that whenever I install Ubuntu after installing XP it does something to the XP partition itself.  The Windows Install CD does not recognize a valid install of XP any more.  Chkdsk shows "One or more unrecoverable errors."  Bootcfg says run chkdsk.  

I wiped everything clean again (this is getting painful, lol), created my partitions before installing, put XP on with no issues.  Installed Ubuntu on the remaining free space.  Now I get the "Unmountable Boot Volume" error when I try to load XP.  Once again the XP CD's utilities does not recognize the XP partition any more.  When I go to repair the XP install, it just shows my hard drive with no partitions on it.  Same deal when I use the recovery console's chkdsk, bootcfg, etc.  I can FixMBR, but all that seems to avail is wiping out Grub and not kicking anything else into gear.  

I read that it is common for boot.ini to have some issues after installing Linux.  It can be fixed by changing the partition information in the boot.ini file ( as per here:  [http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/problem-with-dual-boot-unmountable-boot-volume-95257/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/problem-with-dual-boot-unmountable-boot-volume-95257/) ).  I edited this file through Ubuntu after setting up the ntfs tools and got the 'hal.dll' error.  Tried copying that file over from the XP CD to the XP partition (again through Ubuntu) and the error still popped up.  [ sarcasm ] Happy days are here again. [ /sarcasm ]  

So now I'm going to try to  trick XP by installing it to where the boot.ini file won't need to be modified, on the second partition of the drive.  A simple weekend computer tweak to make my life easier is quickly becoming much much more - its becoming personal, lol.

---

### Post by adrian15 on 2008-03-25
> **arwilson529 said:**
> If it were that easy I wouldn't have a problem, lol.  Unfortunately it appears that whenever I install Ubuntu after installing XP it does something to the XP partition itself.

I recommend you that when installing Ubuntu tell it to install grub into a partition, the linux partition. Then learn how to boot Grub from the Windows boot.ini file and you are done.

adrian15

---

### Post by hmaia on 2008-03-25
Hi,

I thinhk that XP is trying to boot in Ubuntu partition, or in non existent partition
I had that problem during some experiements i done, while trying to fix a dual boot problem in my computer.

Can you boot into Ubuntu?? 

if yes then make this changes in menu.lst and test it
 its in boot/grub/menu.lst

Also if you can boot into ubuntu that means that ubuntu parameters are fine in menu.lst and maybe the XP parameters need to be adjusted.

## ## End Default Options ##
# My Comments : This is Ubuntu Parameters

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=695ade66-e043-440c-a309-001aec4673c4 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=695ade66-e043-440c-a309-001aec4673c4 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# My Comments : This is XP Parameters
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1


You can also see my post here:
[http://ubuntuforums.org/showthread.php?t=732114]("http://ubuntuforums.org/showthread.php?t=732114")

---

