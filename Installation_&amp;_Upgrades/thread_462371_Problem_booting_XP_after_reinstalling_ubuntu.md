---
title: "Problem booting XP after reinstalling ubuntu"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by ep3w on 2007-06-02
I am dual booting XP and Feisty on a dell M65.  I had everything working before but managed to mess something up in ubuntu so i just reinstalled it.  Everything seemed to go fine, everything in ubuntu works, i can access and write to the XP partition of my drive with no problem.  When I go to boot to XP it says that hal.dll is missing or corrupt and can't boot.  I tried downloading it and replacing it but still get the same error.  I can access all the windows files on the partition in ubuntu.  Any ideas how to fix this?

---

### Post by merlinus on 2007-06-02
Are you booting XP from grub?

If so, can you post:

```

cat /boot/grub/menu.lst

```

-merlin

---

### Post by dbott67 on 2007-06-02
You could always run fixmbr from the Windows Installation CD:

1. Boot the system from the Windows CD.
2. Select R to repair/recover
3. Get to command prompt
4. Type fixmbr
5. Reboot

Here's the caveat: FIXMBR nukes the master boot record, effectively destroying grub and preventing access to your linux partition. After this, you would need to boot from a Live CD of Ubuntu and restore grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

-Dave

---

### Post by ep3w on 2007-06-02
here is the cat/boot/grub/menu.lst  Will running FIXMBR delete any of my data?


ryan@ryan-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by dbott67 on 2007-06-02
> **ep3w said:**
> ...  Will running FIXMBR delete any of my data?

No.  FIXMBR will overwrite the grub bootloader and allow Windows XP to boot.  The problem is that after running FIXMBR, you will not be able to access Ubuntu unless you do one of the following:

1. Re-install grub as per the instructions above.
2. Install some other 'boot manager' program
3. Boot from the Live CD and mount the existing Ubuntu ext3 partition to access data.

-Dave

---

### Post by ep3w on 2007-06-02
Also, my copy of windows is legit but I dont know if I have the installation CD anywhere.  Can I use any installation CD aslong as it is XP Pro? Does it matter if it has SP2 integrated in it?

---

### Post by FarmerGiles on 2007-06-02
Any copy of XP Pro of the same version (Retail / OEM / Corporate) will work for the repair console.

don't forget if you need any specific drivers on floppy for SATA hardware etc you will need to press F6 almost immediately the CD boots and have the driver to hand in floppy drive A:

HTH

---

### Post by ep3w on 2007-06-02
thanks for the help! I will have to give it a shot....

---

### Post by ep3w on 2007-06-03
Ok, I have a XP Pro cd but when i go into recovery it tells me I need the administrator password.  I am 95% sure I left it blank but it tells me its the wrong password.  I have tried the 5 other things i use for passwords and i only use those.  Is it possible that this has something to do with it not being my CD?  Most likely no, so is there any way I can change the password or reset it? Maybe from ubuntu?

Edit: I am seeing there is some programs you can download and boot to them that will change it.  Some are free.  Anybody use any that are reliable?  I am kind of hesitant to try one...

---

### Post by ep3w on 2007-06-03
Ok I got it figured it out, ran fixmbr and now I am still getting the same error. Any more ideas how to get it to boot?

---

### Post by dbott67 on 2007-06-03
You may want to try an "in-place" re-installation:

[http://support.microsoft.com/kb/315341](http://support.microsoft.com/kb/315341)

This will re-install Windows, leaving all of your settings & data alone[COLOR=Red]**[/COLOR].  

[COLOR=Red]**[/COLOR] Be sure to read these 2 articles found at the bottom of the page:

[312369]("http://support.microsoft.com/kb/312369/") ([http://support.microsoft.com/kb/312369/](http://support.microsoft.com/kb/312369/))   You may lose data or program settings after reinstalling, repairing, or upgrading Windows XP  
[312368]("http://support.microsoft.com/kb/312368/") ([http://support.microsoft.com/kb/312368/](http://support.microsoft.com/kb/312368/)) Data loss occurs after you reinstall, repair, or upgrade Windows XP  


-Dave

---

### Post by ukripper on 2007-06-06
I had the same problem. Error message you get is very misleading it should be boot.ini not hal.dll but anyhow, I have resolved it by following steps:

1. Boot into XP Cd.
2. Go to recovery
3. Recovery console type: **bootcfg /rebuild**  and then press enter
4. The first prompt asks Add installation to boot list? (Yes/No/All )  Type **Y** press enter
5. Enter Load Identifier:: Windows XP press enter
6. Enter OS Load options:.
Type** /Fastdetec**t  and press Enter. 
7. Exit and reboot.

Hope it works for you as well.

---

### Post by ep3w on 2007-06-06
I started to get fed up with the problem, so i ended up moving all my important stuff to the linux side and just formated the NTFS side and reinstalled XP.  It had been a while anyways.  After that and reinstalling grub i still got the same error.   Turned out i just had to edit my menu.lst.  It was looking to the wrong partition for XP.  Worked perfectly after that :)

---

### Post by ukripper on 2007-06-06
Done the same thing but using Windows XP recovery disk. Conclusion is same amending the corrupted boot.ini.

---

