---
title: "[SOLVED] Grub won't let me into Windows....."
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by kwboom on 2008-10-13
First off I know, why do I need Windows now that I have Hardy, but I still want Windows sometimes......

My problem is that it shows me Windows in the grub menu but when I select it I get a boot error and it tells me to hit ctrl/alt/del to restart.  It will not let me into Windows.....

During install I set about 15 Gb for my Windows partition and the rest of my 120 Gb for Linux.

---

### Post by tangibleorange on 2008-10-13
> **kwboom said:**
> First off I know, why do I need Windows now that I have Hardy, but I still want Windows sometimes......

My problem is that it shows me Windows in the grub menu but when I select it I get a boot error and it tells me to hit ctrl/alt/del to restart.  It will not let me into Windows.....

During install I set about 15 Gb for my Windows partition and the rest of my 120 Gb for Linux.

could you post the output of these two commands:

```
cat /etc/apt/sources.list
sudo fdisk -l
```

---

### Post by kwboom on 2008-10-13
Here is the output for  cat /etc/apt/sources.list

 ```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

And here is for sudo fdisk -l

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04c304c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2003    16089066    7  HPFS/NTFS
/dev/sda2            2004       14593   101129175    5  Extended
/dev/sda5            2004       14334    99048726   83  Linux
/dev/sda6           14335       14593     2080386   82  Linux swap / Solaris

```


Hope this helps you out...... I am just getting started understanding the terminal commands and how Linux works....:(

---

### Post by tangibleorange on 2008-10-13
haha mate im sorry! i was posting in another thread and i asked you to post the output of the wrong command :S. the fdisk one is correct, but the other output we need is:

```
cat /boot/grub/menu.lst
```

which tells us where grub thinks windows is. again, my bad:lolflag:!

---

### Post by kwboom on 2008-10-13
Ok that is ok here is the output for the grub list command.......


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=6968477b-048b-4734-9e97-ee625cf8e632 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6968477b-048b-4734-9e97-ee625cf8e632 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6968477b-048b-4734-9e97-ee625cf8e632 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


Hope this helps ya out


I am still learning this stuff out so an explanation would be great if you have the time....

---

### Post by caljohnsmith on 2008-10-13
Kwboom, your menu.lst entry for Windows is fine, so it looks like you have a Windows problem and not a Grub problem at this point. Do you have your Windows install CD? If you do, boot that up, go to the "recovery console", and run:
```
fixboot
chkdsk /r
```
After that, try booting Windows again and let me know exactly what happens. We can go from there if you want.

P.S. If you want to know more about Grub and everything that is in your menu.lst, a good place to start is:
[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
If after reading through that you have some specific questions, feel free to ask.

---

### Post by kwboom on 2008-10-13
after preforming fixboot and running chkdsk /r that came up with saying that it fixed one or more errors, I got out of repair by typing exit and rebooted (after removing the windows disk) and tried to run windows and got the same thing, Boot load error     press ctrl/alt/del to restart?????:confused:

---

### Post by caljohnsmith on 2008-10-13
It would be worth checking to make sure you have all of Windows necessary boot files, so try the following:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
And post the results of that. It should include the following three files:
```
boot.ini
ntldr
NTDETECT.COM
```
I won't be around again until tomorrow morning, so we can pick up from there if you want.

---

### Post by kwboom on 2008-10-13
ok well it is telling me that it can not mount cause the device or resource is busy but I get this from ls -l /mount


```
dad@Dad:~$ ls -l /mnt
total 720649
-rwxrwxrwx 1 root root         0 2008-10-12 18:55 AUTOEXEC.BAT
-rwxrwxrwx 1 root root      2724 2008-10-13 17:55 bootex.log
-rwxrwxrwx 1 root root       211 2008-10-12 18:49 boot.ini
-rwxrwxrwx 1 root root         0 2008-10-12 18:55 CONFIG.SYS
drwxrwxrwx 1 root root      4096 2008-10-12 19:01 Documents and Settings
-rwxrwxrwx 1 root root 737595392 2008-10-12 21:50 hiberfil.sys
-rwxrwxrwx 1 root root         0 2008-10-12 18:55 IO.SYS
-rwxrwxrwx 1 root root         0 2008-10-12 18:55 MSDOS.SYS
-rwxrwxrwx 1 root root     47564 2006-02-28 07:00 NTDETECT.COM
-rwxrwxrwx 1 root root    250032 2006-02-28 07:00 ntldr
drwxrwxrwx 1 root root      4096 2008-10-12 22:18 Program Files
drwxrwxrwx 1 root root      4096 2008-10-12 18:59 System Volume Information
drwxrwxrwx 1 root root     28672 2008-10-12 22:38 WINDOWS
dad@Dad:~$ 

```



I did have windows running on a fresh install just fine till I installed Hardy and after that is when I started having all the problems.... I even could see the drive and pull files off it till I tried the repair and after that I lost it completely ......Do you think I have to start from scratch or is there a better option?????

---

### Post by caljohnsmith on 2008-10-14
OK, at least you have your Windows boot files, so that's a good sign. So just to clarify, before you installed Ubuntu, was Windows working fine? And did you resize the Windows partition with Ubuntu's partition editor (gparted)? 

Also, I forgot to mention, but if "chkdsk" finds errors and tries to correct them, it is a good idea to run it as many times as necessary until it claims there are no problems; so I would recommend doing it again to make sure there aren't still any basic file system/bad sector errors it can fix.

The next thing I would try is making sure the Windows boot sector partition/file system parameters are OK, which you can do with a program called testdisk. To use testdisk, you can download it and run it with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. :)

---

### Post by kwboom on 2008-10-14
Well to answer your questions, yes Windows was working fine (brand new install), and yes I used which ever program Hardy has in its install to resize windows partition up to about 15 Gb.  I have read something about when you change the windows partition too much it will cause problems with your boot.....   

I just used fixboot and chkdsk /r again and it came back with no errors.

---

### Post by kwboom on 2008-10-14
Well I must say there is something to say about open source.....

It did what even the windows install cd and its utilities could not.....

Testdisk worked   :guitar:


It repaired my boot and now I am able to get into my windows if need be.....

Thankyou very much caljohnsmith for all the help

I must say this is the best forum for Linux that I have found thus far...   Thanx again.......

---

### Post by caljohnsmith on 2008-10-14
That's great news Windows is working again, and glad I could help. Cheers and have fun. :)

---

