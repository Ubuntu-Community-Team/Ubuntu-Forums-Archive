---
title: "Holy Crud What Happened to Windows!~"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by BionicBigfoot on 2006-12-09
I had one logical Drive that when I installed Ubuntu 6.06 I manually partitioned. The intsall went great, but I can't boot back to Windows. I get the autochk error and restart. I have read all the forums pertaining to using the unhide command in the etc/grub/boot/menu.lst folder but it doesn'y work. I can see all my windows files and I can back them up but this is time consuming. I noticed that when I do a fdsik -l it doesn't show my NTFS windows partition. Instead I get this:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13853   111274191   82  Linux swap / Solaris
/dev/hda2           13854       19379    44387595   83  Linux
/dev/hda3           19380       19457      626535   82  Linux swap / Solaris
/dev/hda4           19458       19458           0+  83  Linux
mike@mike-desktop:~$

The dev/hda1 has my Windows files.

When I do an fstab command it does show my NTFS partion. This is what I get when I go to edit my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=0222 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


any ideas on how to boot back into windows? Or will I be forced to reinstall.

I am very very very very new to Linux and don't know much yet. I am loving learning, but I need instructions as if I were a 3 year old.

Thanks so much for anybody who can walk me thru in details how to do it. This community has been such an awesome experience!

---

### Post by bulldog on 2006-12-09
If you can boot Ubuntu,try ```
sudo update-grub
``` into a teminal,to see if grub corrects itself.

But a strange thing indeed,your install listed twice......](*,)

---

### Post by BionicBigfoot on 2006-12-09
Ok I did that. I will restart, but I am not sure if it will help...here goes....

---

### Post by bulldog on 2006-12-09
Restart isn't necessary,just take a look at menu.lst if anything is changed.

I have my doubts with the hda4,it seems very small to me,like nothing is on it really.
Can you have a look at that one to see if there's any data on it?

---

### Post by BionicBigfoot on 2006-12-09
My menu list shows Windows, with the unhide command I added just as before. It almost looks like the windows partition was created as a giant swap partition?

---

### Post by bulldog on 2006-12-09
Can you post your menu.lst?
```
cat /boot/grub/menu.lst
```

---

### Post by BionicBigfoot on 2006-12-09
that last partition doesn't have anything on it. It was a mistake I made when I was partition, I forgot to delete the partition so it still shows. Here is what my menu list looks like:

mike@mike-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
unhide (hd0,0)
savedefault
makeactive
chainloader     +1

mike@mike-desktop:~$

---

### Post by bulldog on 2006-12-09
Nothing wrong with it,only the unhide option for windows is not a common thing.
Why is that,is windows a hidden partition?

---

### Post by BionicBigfoot on 2006-12-09
No but I had an autochk error when I boot into windows and I read that it happens if the partition is hidden, and this was a fix for it. Doesn't seem to help and I can see all my Windows files in Ubunto. I noticed that when other people do the Fdisk-l command, there windos partion looks like this (I have seen it in other posts)

/dev/hda1 * 1 1911 1530076 7 [COLOR="Red"]HPFS/NTFS[/COLOR]

But mine shows it as a swap/solaris like this

dev/hda1 * 1 13853 111274191 82 [COLOR="Red"]Linux swap / Solaris[/COLOR]

---

### Post by bulldog on 2006-12-09
Yep,you're right,but fstab list it as NTFS on th other hand,so it can't be all wrong.
Maybe reinstall GRUB will correct things.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

Give it a try,maybe it helps.

---

### Post by ovrprice on 2006-12-09
If you can See your windows files look in drive C: for these three files
boot.ini
ntdetect.com
ntldr
Copy these three files to the floppy, be sure the floppy is set to boot before the hard disk. This seems to bypass the MBR and takes you straight to windows. Welcome back

---

### Post by BionicBigfoot on 2006-12-09
Ok I want to backup some windows docs files and mp3's I have, just in case something really goes wrong, I don't have much so I will get back to this forum in a few

---

### Post by BionicBigfoot on 2006-12-09
ovrprice - I did what you said. I found the boot.ini file, the ntdetect.com file and the ntldr, but when I boot to a floppy it says non system disk.

---

### Post by BionicBigfoot on 2006-12-09
PS: This is what boot.ini shows:
boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by BionicBigfoot on 2006-12-09
Bulldog when I do your step by steps I get this:
grub> root (hd?,?)

Error 23: Error while parsing number

---

### Post by bulldog on 2006-12-09
Just read carefully and do the steps as listed.
The find command will give you a location,this exact location you have to set in the root command,the (hd?,?) is just an example because it's different for every one.

---

### Post by BionicBigfoot on 2006-12-09
well it added grub but still the same problem. Is there anyway to reformat the windows partition and add windows back to it? I am thinking this as a last resort since I am not sure what else to try

---

### Post by bulldog on 2006-12-09
If your windows don't have any valuable data it's no problem.
You will lose your GRUB,but you already know how to reinstall this.

So if you have the time to do so,just give it a go.

---

### Post by madsquirrel on 2007-06-13
This Solution may help you get back to normal:

[http://ubuntuforums.org/showthread.php?t=467691&highlight=autochk](http://ubuntuforums.org/showthread.php?t=467691&highlight=autochk)

---

