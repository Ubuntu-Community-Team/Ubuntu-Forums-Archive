---
title: "Update Wiped out XP"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by frank cox on 2010-06-09
Like a dummy I let the updater change my menu.lst file in Jaunty. It reported an error but I had no problems until I noticed Windows XP was gone. I rarely use it but now I am teaching a computer class on how to use Widows so I have to fix it tonight.

The system is a Dell 531 with 2 gigs of ram and 2 drives. 
There are 2 menu.lst files in Grub , menu.lst and menu.lst~ . Is the one with the ~ after it the backup? If so how do you restore it?

TIA

---

### Post by darkod on 2010-06-09
I guess you could just rename the files, menu.lst in menu.lst.bak and the other in menu.lst.

But I would first check your partitions with:

sudo fdisk -l

and also open the current menu.lst and check whether there is XP entry inside at all. If not, creating new XP entry in grub1 is very easy.

---

### Post by frank cox on 2010-06-09
> **darkod said:**
> I guess you could just rename the files, menu.lst in menu.lst.bak and the other in menu.lst.

But I would first check your partitions with:

sudo fdisk -l

and also open the current menu.lst and check whether there is XP entry inside at all. If not, creating new XP entry in grub1 is very easy.


Thanks for responding, both of them have an entry for XP  and I have posted that portion below. The Windows partition is the first partition of the first hd ,sda 1
I don't seem to understand how to rename them. When I right click the file there is no option to rename and it opens the menu.lst~ with open office.

This from the menu.lst

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


This is from menu.lst~

                                 ### END DEBIAN AUTOMAGIC KERNELS LIST  # This is a divider, added to separate the menu items below from the Debian # ones. title        Other operating systems: root   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sda1 title        Microsoft Windows XP Professional rootnoverify    (hd0,0) savedefault chainloader    +1 
They look identical to me 

I uploaded the files as .gz

---

### Post by kansasnoob on 2010-06-09
Just post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we can easily tell you how to edit the existing menu.lst.

BTW I can't get the second .gz to open.

---

### Post by frank cox on 2010-06-10
> **kansasnoob said:**
> Just post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we can easily tell you how to edit the existing menu.lst.

BTW I can't get the second .gz to open.
Here  is the results and the menu.lst~ , I cannot see any difference.

Thanks for the reply!

---

### Post by kansasnoob on 2010-06-10
In case someone else wants to have a look I stuck your RESULTS.txt in code tags:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 422156133.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 626294088.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda10 starts at sector 833757498.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a034a03

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,599,769   116,599,707   7 HPFS/NTFS
/dev/sda2         116,599,770   123,443,459     6,843,690  83 Linux
/dev/sda3         123,443,460   976,768,064   853,324,605   5 Extended
/dev/sda5         123,443,523   130,287,149     6,843,627  83 Linux
/dev/sda6         130,287,213   390,829,319   260,542,107  83 Linux
/dev/sda7         390,829,383   422,156,069    31,326,687  83 Linux
/dev/sda8         422,156,133   626,294,024   204,137,892   b W95 FAT32
/dev/sda9         626,294,088   833,757,434   207,463,347   b W95 FAT32
/dev/sda10        833,757,498   970,904,339   137,146,842   b W95 FAT32
/dev/sda11        970,904,403   976,768,064     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f73a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   204,796,619   204,796,557   b W95 FAT32
/dev/sdb2         204,796,620   462,077,594   257,280,975   5 Extended
/dev/sdb5         204,796,683   462,077,594   257,280,912  83 Linux
/dev/sdb3         462,077,595   482,030,324    19,952,730  83 Linux
/dev/sdb4         482,030,325   488,392,064     6,361,740  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       4B5A-D514                              vfat       Dual-Use3                     
/dev/sda11       3a09e702-45b7-4912-a829-fecb634126a2   swap                                     
/dev/sda1        9EC8A2D0C8A2A64D                       ntfs                                     
/dev/sda2        24305024-e76c-4ec6-9ecc-e7d64ca9550c   ext3                                     
/dev/sda5        d3edce97-12f5-4878-8827-49b4f4c1609f   ext3                                     
/dev/sda6        31ac9a84-03fb-4a45-898d-19db167e4c70   ext3                                     
/dev/sda7        ab9fd6e0-c069-4dba-99d8-9c8dd3579667   ext3                                     
/dev/sda8        4B5A-D509                              vfat       Dual-Use                      
/dev/sda9        4B5A-D511                              vfat       Dual-Use-2                    
/dev/sdb1        4B8A-096B                              vfat       250G-Fat1                     
/dev/sdb3        cc015933-b80c-4efb-bbfa-54fd951c957e   ext3       250GB_Puppy                   
/dev/sdb4                                               swap       Swap-Puppy                    
/dev/sdb5        0994244b-7c41-4ff3-ae72-d8fdee6c806f   ext3       250GB-Ext3                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda6        /home                    ext3       (rw,relatime)
/dev/sda7        /usr                     ext3       (rw,relatime)
/dev/sr0         /media/disk              iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


================================ sda1/menu.lst: ================================

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Parted Magic ISO
fallback 7
find --set-root /pmagic.iso
map /pmagic.iso (0xff) || map --mem /pmagic.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)



================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect





C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=================== sda1: Location of files loaded by Grub: ===================


   2.6GB: menu.lst

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=24305024-e76c-4ec6-9ecc-e7d64ca9550c

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-19-generic
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=31ac9a84-03fb-4a45-898d-19db167e4c70 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=ab9fd6e0-c069-4dba-99d8-9c8dd3579667 /usr ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=3a09e702-45b7-4912-a829-fecb634126a2 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


  60.4GB: boot/grub/menu.lst
  60.4GB: boot/grub/stage2
  60.3GB: boot/initrd.img-2.6.28-11-generic
  60.2GB: boot/initrd.img-2.6.28-16-generic
  60.3GB: boot/initrd.img-2.6.28-17-generic
  63.1GB: boot/initrd.img-2.6.28-18-generic
  60.3GB: boot/initrd.img-2.6.28-19-generic
  60.3GB: boot/vmlinuz-2.6.28-11-generic
  60.3GB: boot/vmlinuz-2.6.28-16-generic
  60.3GB: boot/vmlinuz-2.6.28-17-generic
  60.3GB: boot/vmlinuz-2.6.28-18-generic
  60.3GB: boot/vmlinuz-2.6.28-19-generic
  60.3GB: initrd.img
  63.1GB: initrd.img.old
  60.3GB: vmlinuz
  60.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 2e 00 49 2f 4f 20 65  72 72 6f 72 00 08 00 10  |...I/O error....|
00000010  00 00 10 00 00 04 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 04 00 01  00 1f 00 00 01 00 00 00  |................|
00000030  fc 31 c0 90 8e d0 bc 00  7c 89 e5 50 bb 00 10 53  |.1......|..P...S|
00000040  50 88 56 24 16 b4 41 bb  aa 55 cd 13 1f 72 09 d0  |P.V$..A..U...r..|
00000050  d9 73 05 c6 06 c4 7d 42  66 31 c0 b0 02 57 16 9c  |.s....}Bf1...W..|
00000060  66 48 66 99 66 f7 76 28  66 52 66 99 66 c1 e0 05  |fHf.f.v(fRf.f...|
00000070  66 f7 76 0e 52 66 03 46  2c e8 0a 01 5e 66 58 8b  |f.v.Rf.F,...^fX.|
00000080  56 26 66 f7 e2 66 f7 76  0e 52 66 03 40 08 e8 f5  |V&f..f.v.Rf.@...|
00000090  00 5e 01 de 16 07 8d 7f  a8 b1 2c f3 a5 66 89 4d  |.^........,..f.M|
000000a0  b4 66 8b 45 ac 66 48 66  f7 76 0e 66 40 66 89 45  |.f.E.fHf.v.f@f.E|
000000b0  b0 66 ad 66 85 c0 74 1b  b7 80 e8 c6 00 66 ad 66  |.f.f..t......f.f|
000000c0  85 c0 74 0f b7 c0 e8 ba  00 66 ad 66 85 c0 74 03  |..t......f.f..t.|
000000d0  e8 b3 00 66 8b 5d b4 66  83 eb 0c 72 4f 53 66 2b  |...f.].f...rOSf+|
000000e0  5e 14 58 73 05 80 c4 1c  eb 41 66 53 66 2b 5e 10  |^.Xs.....AfSf+^.|
000000f0  72 1c 66 58 66 93 66 f7  76 10 66 52 66 85 d2 75  |r.fXf.f.v.fRf..u|
00000100  0d c1 e0 02 93 66 8b 01  bb 00 c0 e8 75 00 66 58  |.....f......u.fX|
00000110  66 99 66 f7 76 14 52 85  d2 75 0f c1 e0 02 93 66  |f.f.v.R..u.....f|
00000120  8b 81 00 b0 bb 00 80 e8  59 00 58 93 c1 e3 02 66  |........Y.X....f|
00000130  8b 01 9d 5b 07 9c e8 4d  00 9d 06 53 9c 72 2d 31  |...[...M...S.r-1|
00000140  f6 16 07 1e 8e df bf e2  7d 56 66 ad 66 50 ad 92  |........}Vf.fP..|
00000150  ad fe cc 91 f3 a6 75 02  91 ae 66 58 5e 8c df 1f  |......u...fX^...|
00000160  f9 0f 84 f8 fe 01 d6 3b  76 0e 72 d7 66 ff 45 b4  |.......;v.r.f.E.|
00000170  66 ff 4d b0 0f 85 5b ff  be df 7d 73 76 8b 56 24  |f.M...[...}sv.V$|
00000180  57 16 cb 16 07 f9 72 08  c4 5e fc 75 03 c4 5e fa  |W.....r..^.u..^.|
00000190  66 0f b6 4e 0d 66 f7 e1  66 03 46 1c 66 60 66 52  |f..N.f..f.F.f`fR|
000001a0  66 50 06 53 6a 01 6a 10  66 ff 76 18 59 66 f7 f1  |fP.Sj.j.f.v.Yf..|
000001b0  42 59 52 31 d2 66 f7 f1  86 d6 59 86 c5 c0 e4 06  |BYR1.f....Y.....|
000001c0  08 e1 40 b4 02 89 e6 8a  56 24 06 1e cd 13 1f 5b  |..@.....V$.....[|
000001d0  72 1e 8d 5f 20 8e c3 61  66 61 66 40 e2 be c3 4e  |r.._ ..afaf@...N|
000001e0  6f 20 67 72 6c 64 72 00  00 00 00 00 00 00 e2 59  |o grldr........Y|
000001f0  be 03 7c ac b4 0e cd 10  3c 00 75 f7 eb fe 55 aa  |..|.....<.u...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

But I need to study this a bit more. The grub-loader on the XP partition has me confused. You must have used Super Grub Disk or something in the past.

---

### Post by frank cox on 2010-06-10
Hi Kansas:

  I lost XP once before and tried to use grub for dos.
Windows is still there but if I need to reinstall I will . If that is easier on you .
Thanks for the help.

On second thought it may have been that updater was trying to install grub 2.

---

### Post by darkod on 2010-06-10
What I would check:

1. Open device.map to check the disk mapping. For just looking at files or editing I prefer gedit, and because it´s graphical program you need to use gksudo instead of sudo, so it would be:

gksudo gedit /boot/grub/device.map

It should say like

/dev/sda hd0
/dev/sdb hd1

or at least the first line if the second doesn´t exist.

If that confirms sda is hd0 it´s fine.

2. Open in Places the XP partition and move (for the moment don´t delete, just move) the files menu.lst and grldr from there. Like kansas said, they have no place on XP partition and could create the confusion. Just move them anywhere, your ubuntu home folder or where ever.

See if that helps. Otherwise your menu.lst from ubuntu looks correct and should work.

---

### Post by frank cox on 2010-06-10
Hi darkod

Grub is on the first hard drive. Here are the results.

(hd0)    /dev/sda
(hd1)    /dev/sdb

Going to try moving the files.
Thanks

---

### Post by frank cox on 2010-06-10
Hi darod:

  The test confirmed that is correct but moving the files did nothing. When it boots WinXpPro is not listed and when I click other operating systems it gives error message 11 string not recognized.
Thanks

---

### Post by darkod on 2010-06-10
> **frank cox said:**
> Hi darod:

  The test confirmed that is correct but moving the files did nothing. When it boots WinXpPro is not listed and when I click other operating systems it gives error message 11 string not recognized.
Thanks

I hate it when things look OK but don't work. :(

I'm confused with the fact that you say XP doesn't show in the grub menu, but you can clearly see the entry at the end of the menu.lst file in sda2/boot/grub.

As far as I know, if it's in menu.lst (and it is), then it HAS to show in the menu, even if selecting XP doesn't boot it correctly. But at least it has to show.

And ubuntu 9.04 boots fine, right?

---

### Post by frank cox on 2010-06-10
> **darkod said:**
> I hate it when things look OK but don't work. :(

I'm confused with the fact that you say XP doesn't show in the grub menu, but you can clearly see the entry at the end of the menu.lst file in sda2/boot/grub.

As far as I know, if it's in menu.lst (and it is), then it HAS to show in the menu, even if selecting XP doesn't boot it correctly. But at least it has to show.

And ubuntu 9.04 boots fine, right?

I will have to recheck but did you mean to say sda2 ?
Ubuntu 9.04 works fine. That was stupid of me letting it upgrade. Or rather try 2.
It had been working a good while.

---

### Post by darkod on 2010-06-11
Yes, your 9.04 root is /dev/sda2 and the grub config files are in the /boot/grub folder. That's why I said sda2/boot/grub.

From your results file:

=========================== sda2/boot/grub/menu.lst: ===========================

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

What ever happens, this should show as XP in grub1 boot menu, even if it doesn't load it correctly.
Is there any chance your grub1 from the MBR is pointed to a wrong menu.lst file? Maybe the one on /dev/sda1 which looks like remains of super grub (hate that program just because of confusions like this).

---

### Post by frank cox on 2010-06-12
]quote]

What ever happens, this should show as XP in grub1 boot menu, even if it doesn't load it correctly.
Is there any chance your grub1 from the MBR is pointed to a wrong menu.lst file? Maybe the one on /dev/sda1 which looks like remains of super grub (hate that program just because of confusions like this).[/QUOTE]

How would I check? I moved the menu.lst and the other file  to my home folder.
I am pretty sure it was leftover from trying to use grub for dos.
This must have been caused by the attempted upgrade. Do you think maybe they tried to install grub2?


Is there a way to wipe out grub and start over?

Thanks

---

### Post by wilee-nilee on 2010-06-12
Since you have done some work post that script again, in code tags in the results gui.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'm not real familiar with grub-legacy but others are, I'm just trying to get you set up for some analysis of the setup.

---

### Post by hansum_rahul on 2010-06-12
You can do a :
sudo grub-install /dev/sda

but looks like the **problem lies in the windoz grub**! can you try grabbing windoz XP disk and **erasing grub4dos**? 

You can do that with **fixmbr** from the recovery console of a windoz xp disk.

After than do a clean grub-install.

---

### Post by wilee-nilee on 2010-06-12
> **hansum_rahul said:**
> You can do a :
sudo grub-install /dev/sda

but looks like the **problem lies in the windoz grub**! can you try grabbing windoz XP disk and **erasing grub4dos**? 

You can do that with **fixmbr** from the recovery console of a windoz xp disk.

After than do a clean grub-install.

There is no windows grub and the op has done some changes so lets just wait to see the bootscript.

---

### Post by darkod on 2010-06-12
Run the script again as suggested. I'm confused, your menu.lst has got an entry for XP and grub1 has to show all entries in the boot menu. I have no idea why it wouldn't show XP.

---

### Post by frank cox on 2010-06-12
> **darkod said:**
> Run the script again as suggested. I'm confused, your menu.lst has got an entry for XP and grub1 has to show all entries in the boot menu. I have no idea why it wouldn't show XP.


Here is the Results.txt after I ran it again.

Appreciate your help.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 422156133.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 626294088.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda10 starts at sector 833757498.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a034a03

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,599,769   116,599,707   7 HPFS/NTFS
/dev/sda2         116,599,770   123,443,459     6,843,690  83 Linux
/dev/sda3         123,443,460   976,768,064   853,324,605   5 Extended
/dev/sda5         123,443,523   130,287,149     6,843,627  83 Linux
/dev/sda6         130,287,213   390,829,319   260,542,107  83 Linux
/dev/sda7         390,829,383   422,156,069    31,326,687  83 Linux
/dev/sda8         422,156,133   626,294,024   204,137,892   b W95 FAT32
/dev/sda9         626,294,088   833,757,434   207,463,347   b W95 FAT32
/dev/sda10        833,757,498   970,904,339   137,146,842   b W95 FAT32
/dev/sda11        970,904,403   976,768,064     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f73a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   204,796,619   204,796,557   b W95 FAT32
/dev/sdb2         204,796,620   462,077,594   257,280,975   5 Extended
/dev/sdb5         204,796,683   462,077,594   257,280,912  83 Linux
/dev/sdb3         462,077,595   482,030,324    19,952,730  83 Linux
/dev/sdb4         482,030,325   488,392,064     6,361,740  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       4B5A-D514                              vfat       Dual-Use3                     
/dev/sda11       3a09e702-45b7-4912-a829-fecb634126a2   swap                                     
/dev/sda1        9EC8A2D0C8A2A64D                       ntfs                                     
/dev/sda2        24305024-e76c-4ec6-9ecc-e7d64ca9550c   ext3                                     
/dev/sda5        d3edce97-12f5-4878-8827-49b4f4c1609f   ext3                                     
/dev/sda6        31ac9a84-03fb-4a45-898d-19db167e4c70   ext3                                     
/dev/sda7        ab9fd6e0-c069-4dba-99d8-9c8dd3579667   ext3                                     
/dev/sda8        4B5A-D509                              vfat       Dual-Use                      
/dev/sda9        4B5A-D511                              vfat       Dual-Use-2                    
/dev/sdb1        4B8A-096B                              vfat       250G-Fat1                     
/dev/sdb3        cc015933-b80c-4efb-bbfa-54fd951c957e   ext3       250GB_Puppy                   
/dev/sdb4                                               swap       Swap-Puppy                    
/dev/sdb5        0994244b-7c41-4ff3-ae72-d8fdee6c806f   ext3       250GB-Ext3                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda6        /home                    ext3       (rw,relatime)
/dev/sda7        /usr                     ext3       (rw,relatime)
/dev/sr0         /media/disk              iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


================================ sda1/menu.lst: ================================

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Parted Magic ISO
fallback 7
find --set-root /pmagic.iso
map /pmagic.iso (0xff) || map --mem /pmagic.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)



================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=================== sda1: Location of files loaded by Grub: ===================


   2.6GB: menu.lst

=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=24305024-e76c-4ec6-9ecc-e7d64ca9550c

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=31ac9a84-03fb-4a45-898d-19db167e4c70 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=ab9fd6e0-c069-4dba-99d8-9c8dd3579667 /usr ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=3a09e702-45b7-4912-a829-fecb634126a2 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


  60.4GB: boot/grub/menu.lst
  60.4GB: boot/grub/stage2
  60.3GB: boot/initrd.img-2.6.28-11-generic
  60.2GB: boot/initrd.img-2.6.28-16-generic
  60.3GB: boot/initrd.img-2.6.28-17-generic
  63.1GB: boot/initrd.img-2.6.28-18-generic
  60.3GB: boot/initrd.img-2.6.28-19-generic
  60.3GB: boot/vmlinuz-2.6.28-11-generic
  60.3GB: boot/vmlinuz-2.6.28-16-generic
  60.3GB: boot/vmlinuz-2.6.28-17-generic
  60.3GB: boot/vmlinuz-2.6.28-18-generic
  60.3GB: boot/vmlinuz-2.6.28-19-generic
  60.3GB: initrd.img
  63.1GB: initrd.img.old
  60.3GB: vmlinuz
  60.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 2e 00 49 2f 4f 20 65  72 72 6f 72 00 08 00 10  |...I/O error....|
00000010  00 00 10 00 00 04 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 04 00 01  00 1f 00 00 01 00 00 00  |................|
00000030  fc 31 c0 90 8e d0 bc 00  7c 89 e5 50 bb 00 10 53  |.1......|..P...S|
00000040  50 88 56 24 16 b4 41 bb  aa 55 cd 13 1f 72 09 d0  |P.V$..A..U...r..|
00000050  d9 73 05 c6 06 c4 7d 42  66 31 c0 b0 02 57 16 9c  |.s....}Bf1...W..|
00000060  66 48 66 99 66 f7 76 28  66 52 66 99 66 c1 e0 05  |fHf.f.v(fRf.f...|
00000070  66 f7 76 0e 52 66 03 46  2c e8 0a 01 5e 66 58 8b  |f.v.Rf.F,...^fX.|
00000080  56 26 66 f7 e2 66 f7 76  0e 52 66 03 40 08 e8 f5  |V&f..f.v.Rf.@...|
00000090  00 5e 01 de 16 07 8d 7f  a8 b1 2c f3 a5 66 89 4d  |.^........,..f.M|
000000a0  b4 66 8b 45 ac 66 48 66  f7 76 0e 66 40 66 89 45  |.f.E.fHf.v.f@f.E|
000000b0  b0 66 ad 66 85 c0 74 1b  b7 80 e8 c6 00 66 ad 66  |.f.f..t......f.f|
000000c0  85 c0 74 0f b7 c0 e8 ba  00 66 ad 66 85 c0 74 03  |..t......f.f..t.|
000000d0  e8 b3 00 66 8b 5d b4 66  83 eb 0c 72 4f 53 66 2b  |...f.].f...rOSf+|
000000e0  5e 14 58 73 05 80 c4 1c  eb 41 66 53 66 2b 5e 10  |^.Xs.....AfSf+^.|
000000f0  72 1c 66 58 66 93 66 f7  76 10 66 52 66 85 d2 75  |r.fXf.f.v.fRf..u|
00000100  0d c1 e0 02 93 66 8b 01  bb 00 c0 e8 75 00 66 58  |.....f......u.fX|
00000110  66 99 66 f7 76 14 52 85  d2 75 0f c1 e0 02 93 66  |f.f.v.R..u.....f|
00000120  8b 81 00 b0 bb 00 80 e8  59 00 58 93 c1 e3 02 66  |........Y.X....f|
00000130  8b 01 9d 5b 07 9c e8 4d  00 9d 06 53 9c 72 2d 31  |...[...M...S.r-1|
00000140  f6 16 07 1e 8e df bf e2  7d 56 66 ad 66 50 ad 92  |........}Vf.fP..|
00000150  ad fe cc 91 f3 a6 75 02  91 ae 66 58 5e 8c df 1f  |......u...fX^...|
00000160  f9 0f 84 f8 fe 01 d6 3b  76 0e 72 d7 66 ff 45 b4  |.......;v.r.f.E.|
00000170  66 ff 4d b0 0f 85 5b ff  be df 7d 73 76 8b 56 24  |f.M...[...}sv.V$|
00000180  57 16 cb 16 07 f9 72 08  c4 5e fc 75 03 c4 5e fa  |W.....r..^.u..^.|
00000190  66 0f b6 4e 0d 66 f7 e1  66 03 46 1c 66 60 66 52  |f..N.f..f.F.f`fR|
000001a0  66 50 06 53 6a 01 6a 10  66 ff 76 18 59 66 f7 f1  |fP.Sj.j.f.v.Yf..|
000001b0  42 59 52 31 d2 66 f7 f1  86 d6 59 86 c5 c0 e4 06  |BYR1.f....Y.....|
000001c0  08 e1 40 b4 02 89 e6 8a  56 24 06 1e cd 13 1f 5b  |..@.....V$.....[|
000001d0  72 1e 8d 5f 20 8e c3 61  66 61 66 40 e2 be c3 4e  |r.._ ..afaf@...N|
000001e0  6f 20 67 72 6c 64 72 00  00 00 00 00 00 00 e2 59  |o grldr........Y|
000001f0  be 03 7c ac b4 0e cd 10  3c 00 75 f7 eb fe 55 aa  |..|.....<.u...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf  
```

---

### Post by darkod on 2010-06-12
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs: [COLOR=Red]  /menu.lst[/COLOR] /boot.ini [COLOR=Red]/grldr[/COLOR] /ntldr /NTDETECT.COM

I thought you said you moved menu.lst and grldr from the XP partition, /dev/sda1?

And XP still doesn't show in the grub boot menu?

---

### Post by frank cox on 2010-06-12
> **darkod said:**
> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs: [COLOR=Red]  /menu.lst[/COLOR] /boot.ini [COLOR=Red]/grldr[/COLOR] /ntldr /NTDETECT.COM

I thought you said you moved menu.lst and grldr from the XP partition, /dev/sda1?

And XP still doesn't show in the grub boot menu?


I removed it from where it was and it is not there now, it may still be in the mbr . It was suggested I do that and then to just wait until the results were posted.
I will do so and get back to you.

Thanks

---

### Post by frank cox on 2010-06-13
I ran fixmbr and then the boot script. Here are the results.

```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 422156133.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 626294088.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda10 starts at sector 833757498.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a034a03

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,599,769   116,599,707   7 HPFS/NTFS
/dev/sda2         116,599,770   123,443,459     6,843,690  83 Linux
/dev/sda3         123,443,460   976,768,064   853,324,605   5 Extended
/dev/sda5         123,443,523   130,287,149     6,843,627  83 Linux
/dev/sda6         130,287,213   390,829,319   260,542,107  83 Linux
/dev/sda7         390,829,383   422,156,069    31,326,687  83 Linux
/dev/sda8         422,156,133   626,294,024   204,137,892   b W95 FAT32
/dev/sda9         626,294,088   833,757,434   207,463,347   b W95 FAT32
/dev/sda10        833,757,498   970,904,339   137,146,842   b W95 FAT32
/dev/sda11        970,904,403   976,768,064     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f73a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   204,796,619   204,796,557   b W95 FAT32
/dev/sdb2         204,796,620   462,077,594   257,280,975   5 Extended
/dev/sdb5         204,796,683   462,077,594   257,280,912  83 Linux
/dev/sdb3         462,077,595   482,030,324    19,952,730  83 Linux
/dev/sdb4         482,030,325   488,392,064     6,361,740  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       4B5A-D514                              vfat       Dual-Use3                     
/dev/sda11       3a09e702-45b7-4912-a829-fecb634126a2   swap                                     
/dev/sda1        9EC8A2D0C8A2A64D                       ntfs                                     
/dev/sda2        24305024-e76c-4ec6-9ecc-e7d64ca9550c   ext3                                     
/dev/sda5        d3edce97-12f5-4878-8827-49b4f4c1609f   ext3                                     
/dev/sda6        31ac9a84-03fb-4a45-898d-19db167e4c70   ext3                                     
/dev/sda7        ab9fd6e0-c069-4dba-99d8-9c8dd3579667   ext3                                     
/dev/sda8        4B5A-D509                              vfat       Dual-Use                      
/dev/sda9        4B5A-D511                              vfat       Dual-Use-2                    
/dev/sdb1        4B8A-096B                              vfat       250G-Fat1                     
/dev/sdb3        cc015933-b80c-4efb-bbfa-54fd951c957e   ext3       250GB_Puppy                   
/dev/sdb4                                               swap       Swap-Puppy                    
/dev/sdb5        0994244b-7c41-4ff3-ae72-d8fdee6c806f   ext3       250GB-Ext3                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda6        /home                    ext3       (rw,relatime)
/dev/sda7        /usr                     ext3       (rw,relatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=24305024-e76c-4ec6-9ecc-e7d64ca9550c

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        24305024-e76c-4ec6-9ecc-e7d64ca9550c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=24305024-e76c-4ec6-9ecc-e7d64ca9550c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=31ac9a84-03fb-4a45-898d-19db167e4c70 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=ab9fd6e0-c069-4dba-99d8-9c8dd3579667 /usr ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=3a09e702-45b7-4912-a829-fecb634126a2 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


  60.4GB: boot/grub/menu.lst
  60.4GB: boot/grub/stage2
  60.3GB: boot/initrd.img-2.6.28-11-generic
  60.2GB: boot/initrd.img-2.6.28-16-generic
  60.3GB: boot/initrd.img-2.6.28-17-generic
  63.1GB: boot/initrd.img-2.6.28-18-generic
  60.3GB: boot/initrd.img-2.6.28-19-generic
  60.3GB: boot/vmlinuz-2.6.28-11-generic
  60.3GB: boot/vmlinuz-2.6.28-16-generic
  60.3GB: boot/vmlinuz-2.6.28-17-generic
  60.3GB: boot/vmlinuz-2.6.28-18-generic
  60.3GB: boot/vmlinuz-2.6.28-19-generic
  60.3GB: initrd.img
  63.1GB: initrd.img.old
  60.3GB: vmlinuz
  60.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 2e 00 49 2f 4f 20 65  72 72 6f 72 00 08 00 10  |...I/O error....|
00000010  00 00 10 00 00 04 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 04 00 01  00 1f 00 00 01 00 00 00  |................|
00000030  fc 31 c0 90 8e d0 bc 00  7c 89 e5 50 bb 00 10 53  |.1......|..P...S|
00000040  50 88 56 24 16 b4 41 bb  aa 55 cd 13 1f 72 09 d0  |P.V$..A..U...r..|
00000050  d9 73 05 c6 06 c4 7d 42  66 31 c0 b0 02 57 16 9c  |.s....}Bf1...W..|
00000060  66 48 66 99 66 f7 76 28  66 52 66 99 66 c1 e0 05  |fHf.f.v(fRf.f...|
00000070  66 f7 76 0e 52 66 03 46  2c e8 0a 01 5e 66 58 8b  |f.v.Rf.F,...^fX.|
00000080  56 26 66 f7 e2 66 f7 76  0e 52 66 03 40 08 e8 f5  |V&f..f.v.Rf.@...|
00000090  00 5e 01 de 16 07 8d 7f  a8 b1 2c f3 a5 66 89 4d  |.^........,..f.M|
000000a0  b4 66 8b 45 ac 66 48 66  f7 76 0e 66 40 66 89 45  |.f.E.fHf.v.f@f.E|
000000b0  b0 66 ad 66 85 c0 74 1b  b7 80 e8 c6 00 66 ad 66  |.f.f..t......f.f|
000000c0  85 c0 74 0f b7 c0 e8 ba  00 66 ad 66 85 c0 74 03  |..t......f.f..t.|
000000d0  e8 b3 00 66 8b 5d b4 66  83 eb 0c 72 4f 53 66 2b  |...f.].f...rOSf+|
000000e0  5e 14 58 73 05 80 c4 1c  eb 41 66 53 66 2b 5e 10  |^.Xs.....AfSf+^.|
000000f0  72 1c 66 58 66 93 66 f7  76 10 66 52 66 85 d2 75  |r.fXf.f.v.fRf..u|
00000100  0d c1 e0 02 93 66 8b 01  bb 00 c0 e8 75 00 66 58  |.....f......u.fX|
00000110  66 99 66 f7 76 14 52 85  d2 75 0f c1 e0 02 93 66  |f.f.v.R..u.....f|
00000120  8b 81 00 b0 bb 00 80 e8  59 00 58 93 c1 e3 02 66  |........Y.X....f|
00000130  8b 01 9d 5b 07 9c e8 4d  00 9d 06 53 9c 72 2d 31  |...[...M...S.r-1|
00000140  f6 16 07 1e 8e df bf e2  7d 56 66 ad 66 50 ad 92  |........}Vf.fP..|
00000150  ad fe cc 91 f3 a6 75 02  91 ae 66 58 5e 8c df 1f  |......u...fX^...|
00000160  f9 0f 84 f8 fe 01 d6 3b  76 0e 72 d7 66 ff 45 b4  |.......;v.r.f.E.|
00000170  66 ff 4d b0 0f 85 5b ff  be df 7d 73 76 8b 56 24  |f.M...[...}sv.V$|
00000180  57 16 cb 16 07 f9 72 08  c4 5e fc 75 03 c4 5e fa  |W.....r..^.u..^.|
00000190  66 0f b6 4e 0d 66 f7 e1  66 03 46 1c 66 60 66 52  |f..N.f..f.F.f`fR|
000001a0  66 50 06 53 6a 01 6a 10  66 ff 76 18 59 66 f7 f1  |fP.Sj.j.f.v.Yf..|
000001b0  42 59 52 31 d2 66 f7 f1  86 d6 59 86 c5 c0 e4 06  |BYR1.f....Y.....|
000001c0  08 e1 40 b4 02 89 e6 8a  56 24 06 1e cd 13 1f 5b  |..@.....V$.....[|
000001d0  72 1e 8d 5f 20 8e c3 61  66 61 66 40 e2 be c3 4e  |r.._ ..afaf@...N|
000001e0  6f 20 67 72 6c 64 72 00  00 00 00 00 00 00 e2 59  |o grldr........Y|
000001f0  be 03 7c ac b4 0e cd 10  3c 00 75 f7 eb fe 55 aa  |..|.....<.u...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by frank cox on 2010-06-13
This apears to be the first difference I found after running fixmbr

From the previous results.txt {second run}

I put the code no longer there in bold. 

  	 	 	 	 	 	  dev  output: ===========================
 

 Device           Mount_Point              Type       Options
 

 /dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)
 /dev/sda6        /home                    ext3       (rw,relatime)
 /dev/sda7        /usr                     ext3       (rw,relatime)
 **xxx/dev/sr0         /media/disk              iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)**


[B]{Remember I added the XXX}
[/B]


After fixmbr {3rd run}


   	 	 	 	 	 	  dev  output: =========================== 
  
 Device           Mount_Point              Type       Options 
  
 /dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro) 
 /dev/sda6        /home                    ext3       (rw,relatime) 
 /dev/sda7        /usr                     ext3       (rw,relatime) 



That is all I found.

---

### Post by cossack on 2010-06-13
> **frank cox said:**
> Like a dummy I let the updater change my menu.lst file in Jaunty. It reported an error but I had no problems until I noticed Windows XP was gone. I rarely use it but now I am teaching a computer class on how to use Widows so I have to fix it tonight.

The system is a Dell 531 with 2 gigs of ram and 2 drives. 
There are 2 menu.lst files in Grub , menu.lst and menu.lst~ . Is the one with the ~ after it the backup? If so how do you restore it?

TIA
Is XP realy gone or just missing in the grub menu?
I have had a similar problem and the easy way out if windows is still on the drive is to get the free (EASEUS) drive partitioner off the net and install it on another  WINDOWS XP PC.
Take the drive with the problem and connect it to the PC ( I use a USB drive adapter) with the partition manager and carefully save your needed personal files, find the ubuntu partition and format it to ntfs then add it to the windows partition.Windows will still not be able to boot.
Put the drive back in its home pc and reload Ubuntu as a dual boot as before. Windows will now appear in the boot menue and should boot normaly.
 
I Have had windows get lost a few times and this has been the eazy way out for me.
Hope this helps.

---

### Post by frank cox on 2010-06-13
> **cossack said:**
> Is XP realy gone or just missing in the grub menu?
I have had a similar problem and the easy way out if windows is still on the drive is to get the free (EASEUS) drive partitioner off the net and install it on another  WINDOWS XP PC.
Take the drive with the problem and connect it to the PC ( I use a USB drive adapter) with the partition manager and carefully save your needed personal files, find the ubuntu partition and format it to ntfs then add it to the windows partition.Windows will still not be able to boot.
Put the drive back in its home pc and reload Ubuntu as a dual boot as before. Windows will now appear in the boot menue and should boot normaly.
 
I Have had windows get lost a few times and this has been the eazy way out for me.
Hope this helps.

You have a different definition of easy than I :}

Windows is still there but it won't boot. I am more willing to nuke XP than Ubuntu, I rarely use Xp and there were very few files on it and none of them important and even if they were it would easy to copy them. 

That will be the very last time I trust Ubuntus updates. I do not understand a system that forces you to wipe out a drive because the boot loader is messed up, there has to be a way to fix it.

Thanks

---

### Post by darkod on 2010-06-13
The XP boot files look good. Unfortunately we can only judge by the file names, not if they are corrupted or something.

Because it's easy to reinstall grub1 to the MBR, lets try forcing XP to boot directly, without grub1 first.

Boot ubuntu and install generic mbr on /dev/sda with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. That will install generic mbr on /dev/sda and on restart XP should boot automatically. If that is working fine, we'll return grub1 on the MBR.

You will need your 9.04 cd to do that, you have it, right?

The instructions to reinstall grub1 back are here, just make sure you use the ones for 9.04 and 9.04 cd:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

PS. I'm wondering if you could try just to reconfigure grub package. But I can't tell you how all the screens will look like, depending whether you know which choices to make (it's not hard anyway). I think you can bring up the reconfigure screen with:

sudo dpkg-reconfigure grub

---

### Post by frank cox on 2010-06-13
> **darkod said:**
> The XP boot files look good. Unfortunately we can only judge by the file names, not if they are corrupted or something.

Because it's easy to reinstall grub1 to the MBR, lets try forcing XP to boot directly, without grub1 first.

Boot ubuntu and install generic mbr on /dev/sda with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. That will install generic mbr on /dev/sda and on restart XP should boot automatically. If that is working fine, we'll return grub1 on the MBR.

You will need your 9.04 cd to do that, you have it, right?

The instructions to reinstall grub1 back are here, just make sure you use the ones for 9.04 and 9.04 cd:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

PS. I'm wondering if you could try just to reconfigure grub package. But I can't tell you how all the screens will look like, depending whether you know which choices to make (it's not hard anyway). I think you can bring up the reconfigure screen with:

sudo dpkg-reconfigure grub


I will have to make another 9.04 disk as I forgot to bring one to the office. No big deal ,
I will try and reconfigure it first.

---

### Post by frank cox on 2010-06-13
Here are the results.
 

 ubuntu@ubuntu:~$ sudo apt-get install lilo  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following extra packages will be installed:  
   mbr  
 Suggested packages:  
   lilo-doc  
 The following NEW packages will be installed:  
   lilo mbr  
 0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.  
 Need to get 407kB of archives.  
 After this operation, 1307kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main mbr 1.1.10-2 [23.0kB]  
 Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main lilo 1:22.8-7ubuntu1 [384kB]  
 Fetched 407kB in 1s (306kB/s)  
 Preconfiguring packages ...  
 Selecting previously deselected package mbr.  
 (Reading database ... 105940 files and directories currently installed.)  
 Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...  
 Selecting previously deselected package lilo.  
 Unpacking lilo (from .../lilo_1%3a22.8-7ubuntu1_i386.deb) ...  
 Processing triggers for man-db ...  
 Setting up mbr (1.1.10-2) ...  
 Setting up lilo (1:22.8-7ubuntu1) ...  
 

 WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)  
 WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.  
 WARNING: Please read /usr/share/doc/lilo/README.Debian  
 

 

 ubuntu@ubuntu:~$  
 

 Below is the /usr/share/doc/lilo/README.Debian readmefile
 

 --[ Distribution upgrade  
 

 If you are upgrading or dist-upgrading, it is recommended to run  
 /sbin/lilo after that.  
 

 --[ Large initrd files and lilo  
 

 By default, LILO loads the initrd file into the first 15MB of memory  
 to avoid a BIOS limitation with older systems (earlier than 2001).  
 

 However, with newer kernels the combination of kernel and initrd  
 may not fit into the first 15MB of memory and so the system will not  
 boot properly. It seems that the boot issues appear when the  
 kernel+initrd combination is larger than 8MB.  
 

 If this machine has a recent BIOS without the 15MB limitation, you can  
 add the 'large-memory' option to /etc/lilo.conf to instruct LILO to use  
 more memory for passing the initrd to the kernel. You will need to  
 re-run the 'lilo' command to make this option take effect.  
 

 If this machine has an older BIOS, you may need to reduce the size of  
 the initrd *before* rebooting.  
 

 If you are using initramfs-tools, you should replace MODULES=most with  
 MODULES=dep in your configuration and regenerate your initrd file:  
 

 sed -i -e s/MODULES=most/MODULES=dep/ /etc/initramfs-tools/initramfs.conf  
 update-initramfs -u  
 

 If you are using yaird or any other initrd generator, please consult  
 the documentation for your initrd generator.
 

 This is the only config file I found, there was nothing in etc

---

### Post by darkod on 2010-06-13
Didn't I say to ignore the warnings? :)

Don't read what it's asking you to read, just run the second command too to install generic mbr to /dev/sda.

sudo lilo -M /dev/sda mbr

---

### Post by frank cox on 2010-06-13
This is what happened when I ran liloconfig

WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device aufs as the root          &#9474; 
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block       &#9474; 
 &#9474; device. Either your fstab is broken and you should fix it, or you are     &#9474; 
 &#9474; using hardware (such as a RAID array) which this simple configuration     &#9474; 
 &#9474; program does not handle.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.                                            &#9474; 
 &#9474;

---

### Post by darkod on 2010-06-13
Do NOT run commands or follow the warnings. I told you there will be warnings to ignore. You only needed to run two commands, as I said. You did the first, now just do the second.

Forget about the stupid warnings, you won't use lilo anyway.

---

### Post by frank cox on 2010-06-13
> **darkod said:**
> Do NOT run commands or follow the warnings. I told you there will be warnings to ignore. You only needed to run two commands, as I said. You did the first, now just do the second.

Forget about the stupid warnings, you won't use lilo anyway.
  Okay

---

### Post by frank cox on 2010-06-13
It worked!

Thanks!

I guess now i need to reinstall grub

---

### Post by darkod on 2010-06-13
Hold on. So, XP is working and booting fine, right?

---

### Post by frank cox on 2010-06-13
> **darkod said:**
> Hold on. So, XP is working and booting fine, right?
Yes Xp is working

I am going to have to leave for a couple of hours-I will wait to install grub until you reply.

thank you very much!

Here is the fdisk -l if you need it.

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a034a03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7258    58299853+   7  HPFS/NTFS
/dev/sda2            7259        7684     3421845   83  Linux
/dev/sda3            7685       60801   426662302+   5  Extended
/dev/sda5            7685        8110     3421813+  83  Linux
/dev/sda6            8111       24328   130271053+  83  Linux
/dev/sda7           24329       26278    15663343+  83  Linux
/dev/sda8           26279       38985   102068946    b  W95 FAT32
/dev/sda9           38986       51899   103731673+   b  W95 FAT32
/dev/sda10          51900       60436    68573421    b  W95 FAT32
/dev/sda11          60437       60801     2931831   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f73a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   b  W95 FAT32
/dev/sdb2           12749       28763   128640487+   5  Extended
/dev/sdb3           28764       30005     9976365   83  Linux
/dev/sdb4           30006       30401     3180870   82  Linux swap / Solaris
/dev/sdb5           12749       28763   128640456   83  Linux

Disk /dev/sdc: 2004 MB, 2004353024 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000374b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         243     1951866   83  Linux

Disk /dev/sdd: 16.0 GB, 16064184320 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005b5c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1953    15687441    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by darkod on 2010-06-13
OK, use your 9.04 cd and the instructions here to reinstall grub1 to the MBR of the disk. Make sure you use the instructions for 9.04:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It should boot XP fine after that. Lets see.

---

### Post by frank cox on 2010-06-13
> **darkod said:**
> OK, use your 9.04 cd and the instructions here to reinstall grub1 to the MBR of the disk. Make sure you use the instructions for 9.04:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It should boot XP fine after that. Lets see.

Okay- I was going to but I have to leave to go to church-will run it about 9:00

Thanks!

---

### Post by frank cox on 2010-06-13
grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup [hd0]

Error 11: Unrecognized device string

grub> 

No luck.

---

### Post by confused57 on 2010-06-13
> **frank cox said:**
> grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup [hd0]

Error 11: Unrecognized device string

grub> 

No luck.

Did you type "setup [hd0]" in brackets, instead of parentheses?  Needs to be:
setup (hd0)
if this is what you did.

---

### Post by frank cox on 2010-06-13
> **confused57 said:**
> Did you type "setup [hd0]" in brackets, instead of parentheses?  Needs to be:
setup (hd0)
if this is what you did.

No-the instructions did not say to. -be right back

---

### Post by frank cox on 2010-06-14
> **frank cox said:**
> No-the instructions did not say to. -be right back

Well it seemed to work but there was a slew of error messages when it rebooted and now i have Ubuntu and no Win

---

### Post by frank cox on 2010-06-14
I repeated the whole procedure and I got no errors and now have 9.04 and XP

Thanks a million!

---

### Post by msambenny on 2010-06-14
/home/sambenny/Desktop/Screenshot.png

how do i correct this error??

---

### Post by wilee-nilee on 2010-06-14
> **msambenny said:**
> /home/sambenny/Desktop/Screenshot.png

how do i correct this error??

By starting your own thread and explaining where you got that from and what your problem actually is.

---

### Post by frank cox on 2010-06-14
> **msambenny said:**
> /home/sambenny/Desktop/Screenshot.png

how do i correct this error??

I have no idea how to access the pic. You need to upload it with manage attachments down below to have it appear.

---

