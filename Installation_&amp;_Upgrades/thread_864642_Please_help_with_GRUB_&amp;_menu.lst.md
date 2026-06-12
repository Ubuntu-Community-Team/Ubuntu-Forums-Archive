---
title: "Please help with GRUB &amp; menu.lst"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by P@trick99 on 2008-07-19
Hi there

I have 2 hard drives on my Dell vostro, and I have installed Linux Ubuntu 8.04 on my second HD (hd1)
I have selected GRUB loader to be install on the same HD (hd1)(sdb) I don't want to have the grub loader on my (hd0)(sda) where my vista is installed. [COLOR="Navy"]**PLEASE HELP**[/COLOR]! [COLOR="Red"]**Grub Error 17: Cannot mount selected partition**[/COLOR]
***HERE ARE SOME RESULTS FROM TERMINAL (Live CD)***

 cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sda
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
                            Pri/Log   Free Space                          16.46*
    sda1                    Primary   NTFS             []              10742.22*
                            Pri/Log   Free Space                           0.01*
    sda2        Boot        Primary   NTFS             []             146500.47*
                            Pri/Log   Free Space                        2780.15

______________________________________________________________________

 cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sdb
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdb1        Boot        Primary   Linux ext3                      153500.18
    sdb5                    Logical   Linux swap / Solaris              6539.10

____________________________________________________________________

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               3        1308    10490442    7  HPFS/NTFS
/dev/sda2   *        1309       19119   143066855+   7  HPFS/NTFS
/dev/sda3           19120       19457     2714985    5  Extended

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb15a420

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

_____________________________________________________________________

GRUB :

grub> find /boot/grub/stage1
 (hd1,0)

grub> find /boot/grub/stage2
 (hd1,0)

grub> find /boot/grub/menu.lst
 (hd1,0)

_____________________________________________________________________

# menu.lst - See: grub(*) info grub, update-grub(*)
#            grub-install(*), grub-floppy(*),
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
# kopt=root=UUID=c7ee2157-02f4-44e8-9e5f-433ab1ff2223 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c7ee2157-02f4-44e8-9e5f-433ab1ff2223 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c7ee2157-02f4-44e8-9e5f-433ab1ff2223 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

_______________________________________________________________________
[COLOR="Blue"][B][I]Please can someone help me to fix the error 17
What do I need to change?[/I][/B][/COLOR]

THANK YOU


[SIZE="1"]Dell Vostro (Intel Core2 Duo CPU T7500 @ 2.2GHz, 3GB Ram, Nvidia GeForce 8600GT Vista H.
[/SIZE]

---

### Post by confused57 on 2008-07-19
If you get a grub boot menu when you boot first to your Ubuntu drive, highlight your first Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.  This change is temporary if it works, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

Check back if this works, you should be able to modify your Windows entry to boot Windows from grub, e.g.:
```
title  Windows
root (hd1,1)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by cdtech on 2008-07-20
If your using your BIOS to select the drive order just leave your grub/menu.lst to use (hd0,0) as your Ubuntu drive (sdb). GRUB see's this as the Primary drive when you change the boot order through BIOS.

Hope this helps......

---

