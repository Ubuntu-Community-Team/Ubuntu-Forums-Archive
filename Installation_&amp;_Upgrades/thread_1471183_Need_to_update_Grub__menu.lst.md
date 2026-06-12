---
title: "Need to update Grub / menu.lst"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Sockbag on 2010-05-03
I've just updated my Hardy 8.04 to 10.04. Although the update was successful, when I boot the Grub shows 8.04 in the list instead of 10.04.

This is because I (stupidly) chose to use my existing menu.lst throughout the upgrade process.

I'm currently booting from a Hardy Heron live CD, and I need to know how to get Grub to update 

Attached is the Results.txt from BootInfo script

Thank you

---

### Post by dino99 on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

are you sure you cant boot with your grub menu ? you should, see Grub2 Guide below 13)

---

### Post by oldfred on 2010-05-03
Your menu.lst shows the root as hd(0,0) but your install is on sdb or hd(1,0) so that may be why you cannot boot. You could just edit that and possibly boot also.

You can manually boot by editing a boot stanza,  chroot into your system and run the updates or just manually edit menu.lst. You only need one entry to let you boot. The /vmlinuz is a link to the most recent kenel in /boot.

Try this at the Grub prompt if partition known:

root (hd1,0)
kernel /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot
This should boot you into Ubuntu.
Open a terminal in Ubuntu and run

sudo update-grub

---

### Post by Sockbag on 2010-05-03
Thanks for that.

I don't have a Karmic or Lucid LiveCD, and I think I am using an earlier version of Grub (0.97)

Will the process in The Grub 2 Guide -section 13 still work?

---

### Post by Sockbag on 2010-05-03
Thank you, Oldfred - I'll try that now

---

### Post by Sockbag on 2010-05-03
Tried Oldfred's suggestion and got an error 17: cannot mount selected partition.

My apologies for being such an utter noob.

---

### Post by oldfred on 2010-05-03
Which instructions, since I gave a couple. 
Did you just try editing the grub entry from the menu on boot to hd1,0 or the full edit on boot to boot Lucid (as vmlinz boots most current) or use the live CD to add a new entry to menu.lst?

---

### Post by linuxonbute on 2010-05-03
There have been some changes in disc/partition notation in grub2 compared to the older grub.
This might help:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For example:
"Step 1*. Set the Root Partition

    *

      set root=(hdX,Y)

      Use the correct X,Y results from the ls command and ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. For example, if the Ubuntu system is on sda5, enter: set root=(hd0,5)"

---

### Post by oldfred on 2010-05-03
It would be a little more obvious to others if sockbag had posted results.txt in code tags ( the # on the edit menu) so they could see he still has grub legacy. 
Yes it is confusing as long as we have some on grub legacy and some on grub2 with different partition numbering.

---

### Post by Sockbag on 2010-05-03
Thank you for your replies.

My apologies for not posting the text in code tags. Here it is again.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   224,652,959   224,540,505   7 HPFS/NTFS
/dev/sda3         224,669,025   302,760,989    78,091,965   f W95 Ext d (LBA)
/dev/sda5         224,669,088   302,760,989    78,091,902   7 HPFS/NTFS
/dev/sda4         302,760,990   312,496,379     9,735,390  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e35a52b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,246,924   476,246,862  83 Linux
/dev/sdb2         476,246,925   488,392,064    12,145,140   5 Extended
/dev/sdb5         476,246,988   488,392,064    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D6-0B0D                              vfat       DellUtility                   
/dev/sda2        26B07A32B07A0917                       ntfs                                     
/dev/sda4        0000-0000                              vfat       DellRestore                   
/dev/sda5        FE04D4FB04D4B7BB                       ntfs       Backup                        
/dev/sdb1        6dd5d882-a159-4e6e-89d1-0d58af737ccb   ext3                                     
/dev/sdb5        3dc4da81-e729-43f1-93bb-73a5cb692e7a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdf1
UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdf5
UUID=3dc4da81-e729-43f1-93bb-73a5cb692e7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 233.1GB: boot/grub/menu.lst
 233.0GB: boot/grub/stage2
 233.1GB: boot/initrd.img-2.6.24-19-generic
 233.1GB: boot/initrd.img-2.6.24-19-generic.bak
 233.0GB: boot/initrd.img-2.6.24-21-generic
 233.0GB: boot/initrd.img-2.6.24-21-generic.bak
 233.1GB: boot/initrd.img-2.6.24-22-generic
 233.0GB: boot/initrd.img-2.6.24-22-generic.bak
 233.1GB: boot/initrd.img-2.6.24-23-generic
 233.0GB: boot/initrd.img-2.6.24-23-generic.bak
 233.1GB: boot/initrd.img-2.6.24-24-generic
 233.0GB: boot/initrd.img-2.6.24-24-generic.bak
 233.0GB: boot/initrd.img-2.6.24-25-generic
 233.0GB: boot/initrd.img-2.6.24-25-generic.bak
 233.1GB: boot/initrd.img-2.6.24-27-generic
 233.0GB: boot/initrd.img-2.6.24-27-generic.bak
 233.1GB: boot/initrd.img-2.6.32-21-generic
 233.0GB: boot/vmlinuz-2.6.24-19-generic
 233.0GB: boot/vmlinuz-2.6.24-21-generic
 233.0GB: boot/vmlinuz-2.6.24-22-generic
 233.0GB: boot/vmlinuz-2.6.24-23-generic
 233.0GB: boot/vmlinuz-2.6.24-24-generic
 233.0GB: boot/vmlinuz-2.6.24-25-generic
 233.0GB: boot/vmlinuz-2.6.24-27-generic
 233.0GB: boot/vmlinuz-2.6.32-21-generic
 233.1GB: initrd.img
 233.1GB: initrd.img.old
 233.0GB: vmlinuz
 233.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  b8 00 00 8e d0 bc 00 7c  8e d8 fc b9 80 00 8b f4  |.......|........|
00000010  bf 00 06 8e c0 f3 66 a5  ea 2d 06 00 00 10 00 01  |......f..-......|
00000020  00 00 06 00 00 00 00 00  00 00 00 00 00 e8 c5 00  |................|
00000030  b4 11 cd 16 74 48 3d 00  89 75 43 b4 10 cd 16 33  |....tH=..uC....3|
00000040  db c6 87 be 07 00 80 bf  c2 07 db 74 0e 83 c3 10  |...........t....|
00000050  83 fb 40 72 ec be 47 07  e9 92 00 c6 87 be 07 80  |..@r..G.........|
00000060  c6 87 c2 07 0c 2e c7 06  21 06 00 06 b8 43 00 86  |........!....C..|
00000070  c4 b2 80 be 1d 06 cd 13  72 db 0a e4 75 d7 33 db  |........r...u.3.|
00000080  33 c9 8a 87 be 07 3c 00  74 0c 3c 80 74 05 be 8a  |3.....<.t.<.t...|
00000090  07 eb 5a 41 8b eb 83 c3  10 83 fb 40 72 e4 be 95  |..ZA.......@r...|
000000a0  07 00 0c 80 f9 01 72 4b  77 43 be 58 07 8b c5 c1  |......rKwC.X....|
000000b0  e8 04 00 44 1b ff d7 66  8b 86 c6 07 66 2e a3 25  |...D...f....f..%|
000000c0  06 2e c7 06 21 06 00 7c  b4 42 b2 80 be 1d 06 cd  |....!..|.B......|
000000d0  13 be 80 07 72 17 0a e4  75 13 be 78 07 ff d7 be  |....r...u..x....|
000000e0  ab 07 81 3e fe 7d 55 aa  75 03 e9 13 75 ff d7 b4  |...>.}U.u...u...|
000000f0  00 cd 16 cd 18 b8 03 00  cd 10 b8 00 b8 8e c0 33  |...............3|
00000100  ff b8 20 1f b9 50 00 f3  ab b1 0c be 3b 07 bf 44  |.. ..P......;..D|
00000110  00 ac ab e2 fc b4 02 b7  00 ba 00 02 cd 10 b4 86  |................|
00000120  b9 1e 00 ba 80 84 cd 15  bf 2c 07 c3 ac 3c 00 74  |.........,...<.t|
00000130  09 b4 0e bb 07 00 cd 10  eb f2 c3 77 77 77 2e 64  |...........www.d|
00000140  65 6c 6c 2e 63 6f 6d 43  61 6e 6e 6f 74 20 72 65  |ell.comCannot re|
00000150  73 74 6f 72 65 0d 0a 00  4c 6f 61 64 69 6e 67 20  |store...Loading |
00000160  50 42 52 20 66 6f 72 20  64 65 73 63 72 69 70 74  |PBR for descript|
00000170  6f 72 20 31 2e 2e 2e 00  64 6f 6e 65 2e 0d 0a 00  |or 1....done....|
00000180  66 61 69 6c 65 64 2e 0d  0a 00 42 61 64 20 66 6c  |failed....Bad fl|
00000190  61 67 0d 0a 00 30 20 61  63 74 69 76 65 20 70 61  |ag...0 active pa|
000001a0  72 74 69 74 69 6f 6e 73  0d 0a 00 42 61 64 20 50  |rtitions...Bad P|
000001b0  42 52 0d 0a 00 00 00 00  16 f0 86 e6 00 00 00 01  |BR..............|
000001c0  01 00 de fe 3f 06 3f 00  00 00 08 b7 01 00 80 00  |....?.?.........|
000001d0  01 07 07 fe ff ff 47 b7  01 00 59 37 62 0d 00 00  |......G...Y7b...|
000001e0  81 47 0f fe ff ff 61 2d  64 0d bd 96 a7 04 00 00  |.G....a-d.......|
000001f0  c1 ff db fe ff ff 1e c4  0b 12 de 8c 94 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

I'm pretty much a novice at this, so all I have tried is oldfred's sugggestion of

root (hd1,0)
kernel /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

Which gave "Error 17 cannot mount selected partition"

I tried leaving the root at (0,0) but changing the rest and after going through various processes it alerts me that dev/sdb1 doesn't exist and it drops into BusyBox v1.13.3 . Then I'm really lost. I don't know how to use chroot etc.

I would have liked to try editing the menu.lst from the LiveCd, but I didn't really know what to change and scared myself.

---

### Post by oldfred on 2010-05-03
Lets try this.

gksudo gedit ??/boot/grub/menu.lst

??  may just be /dev/sdb1 but I have not used liveCD for a while and do not remember the exact path. Since you are on liveCD it should not ask for password but if it does just hit enter.

I copied one of your stanzas & updated kernel numbers, changed desc, checked UUID & I took out quiet & splash just so you can see the boot process in case it shows error.
Paste this at the bottom of menu.lst below the windows entries:

```
title        Ubuntu 10.04
root        (hd1,0)
kernel        /boot/initrd.img-2.6.32-21-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

```

---

### Post by Sockbag on 2010-05-04
Again, thanks for your help.

I used the terminal from LiveCD to edit the menu.lst on the hard disc, the path to which was /media/disk/boot/grub/menu.lst

I pasted in the code above, saved and reopened the file to check.

On startup, Ubuntu 10.04 appears at the bottom of the grub list. However, when I start from there I get the "Error 17 - cannot mount selected partition"

I then tried changing the Root (hd1,0) in the Grub to Root (hd0,0) and got "Error 13 - Invalid or unsupported executable format"

As I said, I'm really not sure of what I'm doing: but looking at the other entries in my menu.lst it would seem that my 8.04 used (HD0,0) as their root, and had "/boot/vmlinuz-*xxxxx*" as their kernel line, whereas this code has "/boot/initrd.img-2.6.32-21" as it's kernel line. Could this be a problem? Is it worth changing? What about the UUID number?

I don't know what I'm talking about - I'm probably just confusing myself and everyone else at this point....

---

### Post by frantid on 2010-05-04
the kernels have updated, so that's not a problem.  The problem is that grub is seeing the bios boot order, and ubuntu is using it's own boot order.  I think it's good you left grub alone on install/upgrade.  We just have to get the grub entry right.


You have a good eye, try oldfred's lines with your catches minus quiet so we can see what's going on.


```

title        Ubuntu 10.04
root        (hd0,0)
kernel        /boot/vmzlinuz-2.6.32-21-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro 
initrd        /boot/initrd.img-2.6.32-21-generic

```also if this doesn't work on reboot, try to enter the lines one at a time by going to grub command line in the boot process.

---

### Post by frantid on 2010-05-04
do you by chance boot into xp by changing the bios boot order and not by using grub?

---

### Post by oldfred on 2010-05-04
If frantid suggestions do not work some more alternatives but not sure what the problem is:

Also look at /boot/grub/device.map.
This is mine:

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb

UUIDs are supposed to be the preferred way, but I have seen others have to use the old drive nomenclature. 

You could add both of these and see if either works:

Title sdb
root (hd1,0)
kernel /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img

Title sda
root (hd0,0)
kernel /vmlinuz root=/dev/sda1 ro
initrd /initrd.img

---

### Post by Sockbag on 2010-05-04
Hi Frantid,

Thanks for your help.

I have my Ubuntu on an external drive which I only plug in to use Ubuntu. I never use the grub to boot into XP.

I've tried the updated code you posted above, and with (HD 0,0) I get "Error 15 - File not Found" when I change to (HD1,0) I get the Error 17 message again.

---

### Post by Sockbag on 2010-05-04
Hey Oldfred,

With (hd 0,0) and sda1, when I attempt to boot I get an error saying:

'mounting /dev on /root/dev failed: No such file or directory' and 'target filesystem doesn't have /sbin/init. No init found'... After that it takes me to the BusyBox built in shell prompt.

Whenever I try to boot any with parameters that specify (hd1,0) as the root, I always get the Error 17: Cannot mount selected partition. :(

---

### Post by frantid on 2010-05-04
ok, please try the lines one at a time from within grub.  press c from the grub menu

edit - just read your last hang on.

---

### Post by frantid on 2010-05-04
hd(0,0) is correct.  busybox means grub has handed off.

I think your upgrade did not complete correctly.

---

### Post by Sockbag on 2010-05-04
my device map shows

(hd0)	/dev/sda
(hd1)	/dev/sdf

---

### Post by Sockbag on 2010-05-04
Ah, bummer.

Is downloading an ISO and doing a clean install an idea? Would I lose any documents?

---

### Post by frantid on 2010-05-04
I think you should try kansasnoob's directions here to attempt a chroot aptitude update from the livecd, for background:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I think in your case your external will show as sdb1, just do a blkid command to verify the mapping before attempting his instructions.

the aptitude commands you want to run are in this post.  I'm not sure you want to run the proposed kernel.  Just read this post and do things slowly.  You don't have to do both links just this one:

[http://ubuntuforums.org/showpost.php?p=9226662&postcount=5](http://ubuntuforums.org/showpost.php?p=9226662&postcount=5)

---

### Post by kansasnoob on 2010-05-04
I have a totally different outlook on this. IMO it would be best to mount and chroot Ubuntu (sdb1), upgrade to grub2, and then install grub to the mbr of both drives. If you choose to do this first read the following just so you have a general idea of what we're doing:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And Appendix #2 of this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Then if you choose to:

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
apt-get update
```

Note: **[COLOR="Red"]Only if that returns a bunch of errors[/COLOR]** stop, post the terminal output, and also the output of:

```
aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
```

```
mv /boot/grub /boot/grub_legacy
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub
```

```
apt-get --purge remove grub-common
```

```
apt-get install grub-pc
```

Note: you'll notice that does reinstall 'grub-common', that's OK, just proceed:

```
update-grub
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

Note: should either of those two 'grub-install' commands return any errors use the 'grub-install --recheck' command, eg: "grub-install --recheck /dev/sda" or "grub-install --recheck /dev/sdb".

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

I would hope that will get you booting, of course you might then want to learn a bit about grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by kansasnoob on 2010-05-04
> **frantid said:**
> I think you should try kansasnoob's directions here to attempt a chroot aptitude update from the livecd, for background:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I think in your case your external will show as sdb1, just do a blkid command to verify the mapping before attempting his instructions.

the aptitude commands you want to run are in this post.  I'm not sure you want to run the proposed kernel.  Just read this post and do things slowly.  You don't have to do both links just this one:

[http://ubuntuforums.org/showpost.php?p=9226662&postcount=5](http://ubuntuforums.org/showpost.php?p=9226662&postcount=5)

Most of the commands in that post won't help here.

Edit: I should say, it's possible that the kernel failed to upgrade but I think it's more likely that only legacy grub failed to update, that is to recognize the kernel upgrade. We'll know after the OP upgrades to grub2.

---

### Post by Sockbag on 2010-05-04
Thank you all very much for your inputs. 

I'll have a read while I'm downloading a new LiveCD, (as I only have Heron atm) then try to work out where to go from there.

---

### Post by kansasnoob on 2010-05-04
> **Sockbag said:**
> Thank you all very much for your inputs. 

I'll have a read while I'm downloading a new LiveCD, (as I only have Heron atm) then try to work out where to go from there.

You can use your Hardy Live CD for what I suggested. That's actually why I use a chroot for even "reinstalling" grub or grub2 to any mbr (that way it doesn't matter which grub is used on the Live CD).

Once you're in the chroot you're dealing with the installed distros package management :)

Although that's also why I've begun initiating 'apt-get update' early in the process. There have been times when repository problems will interfere with installation of packages :(

Even that can be dealt with though by using 'wget' and 'dpkg -i'. It's just more of a pain.

It's just best to be sure that the packages are available for installation, example:

```
lance@lance-desktop:~$ aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
Package: grub
State: not installed
Version: 0.97-29ubuntu60
Priority: optional
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu6
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu6

```

---

### Post by frantid on 2010-05-04
I was thinking along the lines that he doesn't want to boot his original drive off of grub, only off the external when he wants ubuntu.  His bios must be booting the external drive first, but ubuntu or the latest kernels enumerate the drives by bus instead of bios order.

He can boot the kernel (drive is still ext3) and start the loading, it seems like he's missing some config or packages in the upgrade process.  Thus the init errors.  So I was thinking finish the upgrade, try to continue with grub 0.97 -- only if that fails o to grub2.

but, you've got more experience with this than I do.

edit:  these errors aren't grub errors?
> 'mounting /dev on /root/dev failed: No such file or directory' and  'target filesystem doesn't have /sbin/init. No init found'... After that  it takes me to the BusyBox built in shell prompt.

---

### Post by frantid on 2010-05-04
sockbag, try changing:

```
# groot=(hd1,0)
```

to:


```
# groot=(hd0,0)
```

/boot/grub/menu.lst

kansasnoob is probably right it's a grub error.

---

### Post by kansasnoob on 2010-05-04
> **frantid said:**
> I was thinking along the lines that he doesn't want to boot his original drive off of grub, only off the external when he wants ubuntu.  His bios must be booting the external drive first, but ubuntu or the latest kernels enumerate the drives by bus instead of bios order.

He can boot the kernel (drive is still ext3) and start the loading, it seems like he's missing some config or packages in the upgrade process.  Thus the init errors.  So I was thinking finish the upgrade, try to continue with grub 0.97 -- only if that fails o to grub2.

but, you've got more experience with this than I do.

edit:  these errors aren't grub errors?

That's why I added my edit. You could well be right.

The reason I said to install grub to both mbr's is because his RESULTS.txt showed:

> No known boot loader is installed in the MBR of /dev/sda


Just one less thing to worry about and if (s)he ever wants a Windows mbr just boot a *buntu Live CD and:

```
sudo apt-get install lilo
sudo lilo -M /dev/sdX mbr
```

Where X is the proper drive designation.

---

### Post by frantid on 2010-05-04
sda MBR looks like a dell boot loader of some sort.

---

### Post by kansasnoob on 2010-05-04
> **frantid said:**
> sda MBR looks like a dell boot loader of some sort.

I have no idea what you're saying :confused:

Do you understand drive and partition designations?

Like sda = drive #1, sdb = drive #2, sdc = drive #3, etc.

Partitions end in "numbers", like sda1 = drive #1 and partition #1, sdb2 = drive #2 and partition #2, sdc3 = drive #3 and partition #3.

Some distros still use the "hd" prefix but otherwise the third and fourth designations always indicate drive and partition!

Where and how do you see a Dell bootloader?

---

### Post by kansasnoob on 2010-05-04
Just FYI if you want to leave the mbr of sda alone that's fine! It shouldn't matter.

---

### Post by frantid on 2010-05-04
at the end of the bootinfoscript results file, there's a hex of the mbr internal drive.  That's a dell MBR to allow the restore from the hidden restore partition.

I have been trying to track down what caused the change in ubuntu to not see the hard drives in the bios boot order -- some release notes, etc.  Grub sees the drives in the bios boot order, perhaps by init 13 support.  However, the latest kernel enumerates by bus order.  I can see it in grub2 by ls (hd0,1)/...  the files listed are those in my bios boot drive.  However, in Lucid this drive is sdb1.  Karmic used to agree with grub, until the last kernel upgrade.  In OP's fstab file you can see Lucid called his external drive sdf1, though in grub it was the bios boot drive hd(0,0).

So I've bee trying to help people and see if others are experiencing this as well.  Maybe it's the removal of hal, or the use of upstart I'm not sure.

if any of that makes sense....

---

### Post by oldfred on 2010-05-04
My drive order has not changed but something with grub 1.98 and boot info script has.

I boot Lucid from sda and Karmic from sdc. My lucid is in sdc7 but the boot script info says that the grub2 in sda boots the same drive partition 7 and it boots ok. I thought it was the script but maybe its grub changing order mid-stream?

---

### Post by kansasnoob on 2010-05-04
> **frantid said:**
> at the end of the bootinfoscript results file, there's a hex of the mbr internal drive.  That's a dell MBR to allow the restore from the hidden restore partition.

I have been trying to track down what caused the change in ubuntu to not see the hard drives in the bios boot order -- some release notes, etc.  Grub sees the drives in the bios boot order, perhaps by init 13 support.  However, the latest kernel enumerates by bus order.  I can see it in grub2 by ls (hd0,1)/...  the files listed are those in my bios boot drive.  However, in Lucid this drive is sdb1.  Karmic used to agree with grub, until the last kernel upgrade.  In OP's fstab file you can see Lucid called his external drive sdf1, though in grub it was the bios boot drive hd(0,0).

So I've bee trying to help people and see if others are experiencing this as well.  Maybe it's the removal of hal, or the use of upstart I'm not sure.

if any of that makes sense....

I've even tried to reproduce that effect on both of my machines unsuccessfully. I know it's happening - obviously.

Believe me, I'm as frustrated as you are :o

If it wouldn't hurt my foot I'd kick something! But I'm bare-footin'!

This is horribly frustrating ](*,)

And it's certainly not limited to just a few.

---

### Post by kansasnoob on 2010-05-04
> **oldfred said:**
> My drive order has not changed but something with grub 1.98 and boot info script has.

I boot Lucid from sda and Karmic from sdc. My lucid is in sdc7 but the boot script info says that the grub2 in sda boots the same drive partition 7 and it boots ok. I thought it was the script but maybe its grub changing order mid-stream?

How does the info script compare with 'fdisk -l' or gparted?

---

### Post by frantid on 2010-05-04
I think it happens when you have drives on different pci tree's.   My case I have one on an IDE interface via the southbridge, the others are on the sata controller via an add-on chip.  I set my bios to boot of my lead sata drive.  So grub see's it as hd0.  However, whatever is mapping the /dev/ is doing bus order -- choosing the old IDE first then hitting the sata bus.

In the OP, lucid is hitting the internal bus, then hitting the external (usb/firewire).

I had to set a new drive.map up to get the grub-install, etc to run correctly.

---

### Post by oldfred on 2010-05-04
I have all SATA drives and the order has always been the port order on the motherboard.

fdisk, gparted, device.map everything shows drives sda, sdb, & sdc the same. It is only the grub entry in sda that says partition 7 on same drive and I only have 3 partitions on sda, but it boots sdc7. I assumed something in boot script parsed 1.98 differently than 1.97.

---

### Post by Sockbag on 2010-05-05
And I fall at the first hurdle...

I've had a read through both this thread and a few others, and Kansasnoob's ideas in post#23 kind of make sense to me, so I'm going to have a go at that. I'm booted from my original Hardy Heron LiveCD.

However...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       13984   112270252+   7  HPFS/NTFS
/dev/sda3           13986       18846    39045982+   f  W95 Ext'd (LBA)
/dev/sda4           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda5           13986       18846    39045951    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e35a52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       29645   238123431   83  Linux
/dev/sdf2           29646       30401     6072570    5  Extended
/dev/sdf5           29646       30401     6072538+  82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: special device /dev/sdb1 does not exist
ubuntu@ubuntu:~$ 

```

fdisk -l shows that sdf1 is my boot partition. This is consistent with my device map where

(hd0) /dev/sda
(hd1) /dev/sdf

The question is; can I just replace sdb1 in Kansasnoob's code with sdf1?

Also, I want to leave my Internal XP disc alone, so I am assuming I can just leave out the "grub-install /dev/sda" line later in his code (?)

---

### Post by oldfred on 2010-05-05
I think you will mount sdf1 instead of sdb1 in Kansas's first command and you still want grub in sdf, so on the last commands use sdf instead of sda. If you then set BIOS to boot sdf first you will boot grub, but have not changed the boot sda.

---

### Post by kansasnoob on 2010-05-05
Well, it's odd that the Boot Info Script shows:

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   224,652,959   224,540,505   7 HPFS/NTFS
/dev/sda3         224,669,025   302,760,989    78,091,965   f W95 Ext d (LBA)
/dev/sda5         224,669,088   302,760,989    78,091,902   7 HPFS/NTFS
/dev/sda4         302,760,990   312,496,379     9,735,390  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e35a52b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,246,924   476,246,862  83 Linux
/dev/sdb2         476,246,925   488,392,064    12,145,140   5 Extended
/dev/sdb5         476,246,988   488,392,064    12,145,077  82 Linux swap / Solaris
```

And Hardy's fdisk -l shows:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       13984   112270252+   7  HPFS/NTFS
/dev/sda3           13986       18846    39045982+   f  W95 Ext'd (LBA)
/dev/sda4           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda5           13986       18846    39045951    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e35a52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       29645   238123431   83  Linux
/dev/sdf2           29646       30401     6072570    5  Extended
/dev/sdf5           29646       30401     6072538+  82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: special device /dev/sdb1 does not exist
ubuntu@ubuntu:~$
```

But the simple answer to "The question is; can I just replace sdb1 in Kansasnoob's code with sdf1?" is YES! Always work with the info provided by the Live CD you're working with!

In answer to, "Also, I want to leave my Internal XP disc alone, so I am assuming I can just leave out the "grub-install /dev/sda" line later in his code (?)" again YES! It was not being used by grub previously so that should be fine.

Great catch on the difference between sdb and sdf!

Also once you've mounted and chrooted the partition you can check to see if you have the *buntu OS you want with:

```
lsb_release -a
```

Good luck!

---

### Post by kansasnoob on 2010-05-05
> **kansasnoob said:**
> Just FYI if you want to leave the mbr of sda alone that's fine! It shouldn't matter.

Just bumping this forward so you can see I already said it's fine to leave the mbr on sda alone.

---

### Post by Sockbag on 2010-05-05
Hi kansasnoob,

Thanks for all your advice. I'm following through your code at the moment and it all seems to be going ok (fingers crossed) however I've just had this error - can I ignore it/get round it? 

root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get --purge remove grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/#


EDIT: Re the sda mbr - I just wanted to check that was what you meant, I appreciate you drawing my attention to it again. Thanks.

---

### Post by Sockbag on 2010-05-05
In addition to the above post, I'm not at all sure what's going on here.

```
root@ubuntu:/# apt-get --purge remove grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
  grub: Depends: grub-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
  grub: Conflicts: grub-pc but 1.98-1ubuntu6 is to be installed
  grub-pc: Depends: grub-common (= 1.98-1ubuntu6) but 1.98-1ubuntu5 is to be installed
           Conflicts: grub (< 0.97-54) but 0.97-29ubuntu60 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/# 
```

---

### Post by frantid on 2010-05-05
Sockbag, I'll let others who know more help with your install, there.


kansasnoob & oldfred, I believe the drive.map has to be altered.  Grub sees hardy's sdf as hd0, because it is the bios boot drive.  Grub sees hardy's sda as hd1.  This is the mismatch we were talking about.  In order for update-grub to be successful the drive.map should be:

(hd0) /dev/sdf
(hd1) /dev/sda


This is will let hardy, lucid, grub agree on the boot drive.  What do you guy's think.

---

### Post by Sockbag on 2010-05-05
I'm posting this as I'm going to try a restart and with lose it otherwise

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       13984   112270252+   7  HPFS/NTFS
/dev/sda3           13986       18846    39045982+   f  W95 Ext'd (LBA)
/dev/sda4           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda5           13986       18846    39045951    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e35a52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       29645   238123431   83  Linux
/dev/sdf2           29646       30401     6072570    5  Extended
/dev/sdf5           29646       30401     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdf1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
root@ubuntu:/# apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://gb.archive.ubuntu.com lucid Release.gpg                   
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Hit http://archive.ubuntu.com lucid Release                          
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Get:1 http://gb.archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://gb.archive.ubuntu.com lucid Release 
Get:2 http://gb.archive.ubuntu.com lucid-updates Release [38.5kB]
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://archive.ubuntu.com lucid/main Sources                     
Hit http://gb.archive.ubuntu.com lucid/main Packages                 
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://gb.archive.ubuntu.com lucid/restricted Packages
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid/restricted Sources
Hit http://gb.archive.ubuntu.com lucid/main Sources
Hit http://gb.archive.ubuntu.com lucid/universe Sources
Hit http://gb.archive.ubuntu.com lucid/universe Packages
Get:3 http://gb.archive.ubuntu.com lucid-updates/main Packages [24.9kB]
Get:4 http://gb.archive.ubuntu.com lucid-updates/restricted Packages [14B]
Get:5 http://gb.archive.ubuntu.com lucid-updates/multiverse Packages [14B]
Get:6 http://gb.archive.ubuntu.com lucid-updates/restricted Sources [14B]
Get:7 http://gb.archive.ubuntu.com lucid-updates/main Sources [10.8kB]
Get:8 http://gb.archive.ubuntu.com lucid-updates/universe Sources [1,959B]
Get:9 http://gb.archive.ubuntu.com lucid-updates/universe Packages [7,966B]
Fetched 84.3kB in 1s (76.9kB/s)                         
Reading package lists... Done
root@ubuntu:/# mv /boot/grub /boot/grub_legacy
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get --purge remove grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/# apt-get --purge remove grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
  grub: Depends: grub-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
  grub: Conflicts: grub-pc but 1.98-1ubuntu6 is to be installed
  grub-pc: Depends: grub-common (= 1.98-1ubuntu6) but 1.98-1ubuntu5 is to be installed
           Conflicts: grub (< 0.97-54) but 0.97-29ubuntu60 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 filezilla libqt4-opengl libxfce4mcs-client3 libqt4-assistant libavutil1d
  libdc1394-13 libwxgtk2.6-0 libqt4-test libwxgtk2.8-0 libqt4-dbus libjack0.100.0-0
  libdns35 openoffice.org-hyphenation-en-us libqt4-core libpostproc1d mysql-common
  libboost-thread1.34.1 libservlet2.4-java libboost-date-time1.34.1 libdvbpsi4
  libavformat1d binutils-static libxosd2 libmysqlclient15off libx264-57 libvlc0
  nvidia-kernel-common bsh libqt4-gui libjaxp1.3-java libwxbase2.6-0 libwxbase2.8-0
  python-pyopenssl libjline-java libxerces2-java libmjpegtools0c2a libqt4-svg
  libxalan2-java libiso9660-5 libdvdread3 libqt4-xml libzip1 libqt4-network libqt4-designer
  libavcodec1d filezilla-common libboost-filesystem1.34.1 libgmyth0 libxfce4mcs-manager3
  odt2txt libqt4-script ladcca2 libaudit0 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 41 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
Package: grub
State: installed
Automatically installed: no
Version: 0.97-29ubuntu60
Package: grub-pc
State: not installed
Version: 1.98-1ubuntu6
Priority: optional
Package: grub-common
New: yes
State: installed
Automatically installed: yes
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/vmlinuz-2.6.24-27-generic
Found kernel: /boot/vmlinuz-2.6.24-25-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       13984   112270252+   7  HPFS/NTFS
/dev/sda3           13986       18846    39045982+   f  W95 Ext'd (LBA)
/dev/sda4           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda5           13986       18846    39045951    7  HPFS/NTFS

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e35a52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       29645   238123431   83  Linux
/dev/sdf2           29646       30401     6072570    5  Extended
/dev/sdf5           29646       30401     6072538+  82  Linux swap / Solaris
root@ubuntu:/#  grub-install /dev/sdf
Probing devices to guess BIOS drives. This may take a long time.
/dev/sdb1: Not found or not a block device.
root@ubuntu:/#  grub-install /dev/sdf
/dev/sdb1: Not found or not a block device.
root@ubuntu:/#  grub-install /dev/sdf
/dev/sdb1: Not found or not a block device.
root@ubuntu:/# grub-install --recheck /dev/sdf
Probing devices to guess BIOS drives. This may take a long time.
/dev/sdb1: Not found or not a block device.
root@ubuntu:/# 

```

My feeling is that the new grub did not install onto the mbr of sdf :(

---

### Post by oldfred on 2010-05-05
I am not sure what you are doing. If you are reinstalling grub2 you should install common also so you have consistent versions:

This uninstalls old grub and grub2, then reinstalls grub2:
```
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common

```

---

### Post by kansasnoob on 2010-05-05
This error:

```
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

is preventing apt from completing the removal and/or installation of packages. So that must be fixed. There's a very good chance that's where the whole upgrade "broke down". Now how to fix it?

You'll get no where until we straighten that out so give me a little bit to ponder this. Hopefully we can get that resolved and then resume the dist-upgrade, fix grub, and possibly create a new device.map.

---

### Post by kansasnoob on 2010-05-05
First of all be sure "sdf" is still correct on the reboot to the Live Desktop!

There are additional clues here:

> 1 upgraded, 1 newly installed, 0 to remove and [B][COLOR="Red"]41 not upgraded.
1 not fully installed or removed[/COLOR][/B].
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: [B][COLOR="Red"]error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/COLOR][/B]
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)


So we must resolve the conflict with "flashplugin-nonfree" before the "dist-upgrade" can complete! That's probably where the whole upgrade process "choked"!

So once again mount and chroot your Ubuntu then this becomes almost trial and error, first:

```
apt-get autoremove
```

```
apt-get autoclean
```

```
apt-get clean
```

```
rm /var/lib/dpkg/info/adobe-flashplugin.prerm
```

```
apt-get --purge remove flashplugin-nonfree
```

```
dpkg --configure -a
```

```
apt-get -f install
```

```
apt-get dist-upgrade
```

You'll have to say yes (y), then if "dist-upgrade completes successfully you'll need to resume with fixing grub, **[COLOR="Red"]but if you're still getting that error about "flashplugin" there's no point in proceeding![/COLOR]**

Since "update-grub" did run with the old legacy grub still installed you'll need to run all of the following (note that I've changed the suffix on the grub_backup):

```
mv /boot/grub /boot/grub_old
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub
```

```
apt-get --purge remove grub-common
```

```
apt-get install grub-pc
```

```
update-grub
```

```
grub-install /dev/sdf
```

Note: I suspect that a successful "purge" of the grub configuration files will have cleared up this error:

```
Probing devices to guess BIOS drives. This may take a long time.
/dev/sdb1: Not found or not a block device.
root@ubuntu:/#  grub-install /dev/sdf

```

But if not you can create a new device.map with:

```
grub-mkdevicemap
```

Then of course repeat the following as needed:

```
grub-install /dev/sdf
```

```
grub-install --recheck /dev/sdf
```

Then exit the chroot and unmount as previously explained.

Once you're booted into Ubuntu run:

```
sudo apt-get install ubuntu-restricted-extras
```

To resolve that flash thing.

---

### Post by kansasnoob on 2010-05-05
BTW sorry that took so long, it seems like everyone wants to call me today! And they're not even bill collectors ;)

---

### Post by oldfred on 2010-05-05
kansas I see you uninstall grub-common but do not reinstall? 

I think you need it to be updated/consistent with the version of grub-pc to work correctly.

---

### Post by kansasnoob on 2010-05-06
> **oldfred said:**
> kansas I see you uninstall grub-common but do not reinstall? 

I think you need it to be updated/consistent with the version of grub-pc to work correctly.

When you install grub-pc it's automatically pulled in as a dependency. I only purge it to get rid of the configuration files.

---

### Post by Sockbag on 2010-05-06
Throughout the course of this nightmare I have been so far out of my comfort zone that it's been like wearing sandpaper underpants. It's probably been obvious that I, largely, haven't known what I'm doing at any point.

Today I followed the Kansasnoob's instructions in post no 49. These, unfortunately, failed to remove the flashplugin error, but armed with blind faith, ignorance and determination I used this code from a different thread:

```
rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```

and that seems to have worked, and allowed the update(s) to happen.

I went on to install GRUB as per the post, which I messed up by not understanding the grub installer's instructions. So I removed grub again, renaming the folder in "mv /boot/grub /boot/grub_old" to "grub-rubbish", and installed grub onto sdb. (My drive is called sdb again today, for some reason)

Then there were loads of confusing "/proc/devices: No entry for device-mapper found" and "Is device-mapper driver missing from kernel? Failure to communicate with kernel device-mapper driver." messages and I was panicking like a kernel, but I stayed strong and "Installation finished. No error reported."

That's right - I'm booted into Lucid via GRUB at this very moment.

Obviously, I deserve no credit here. I would truly like to thank everyone for their input, but especially to you, Kansasnoob - thank you very much.

I'm going to mark this thread as solved, and I hope it will be useful to someone else.

Cheers!

Sockbag

---

### Post by frantid on 2010-05-06
Sockbag,  I'm glad you got it sorted.  

Could you please do me the favor of posting one last bootinfoscript results.  I'm still trying to track down issues with drive /dev/sdx switching and boot order.

frantid

---

### Post by kansasnoob on 2010-05-06
> Obviously, I deserve no credit here.

YES! You do!

These issues are always easier to fix when the computer is right in front of me because I pretty well know what to try next if something fails. Of course it would require writing a book to address each and every possible failure, it's possible cause, and possible solutions ........... and quite often I have to refer to notes that I sometimes have poorly organized.

Anyway you deserve a lot of credit! Every step of the way you've provided excellent feedback. Quite often people just come back with, "that didn't work". Like that tells me anything ;) Communication is of great importance.

You did great and you hung in there :guitar:

---

### Post by Sockbag on 2010-05-07
Hello again,

Frantid, here is the latest BootInfo Script, plus the output of "fdisk -l"
One of the confusing aspects of all this was that my external hard disc was referred to as either sdb or sdf. Yesterday when I was installing etc, it was sdb  - today it's back to sdf it seems. My internal XP drive has always been seen as sda. I hope this helps you somehow. If you need anything else, please let me know.


```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       13984   112270252+   7  HPFS/NTFS
/dev/sda3           13986       18846    39045982+   f  W95 Ext'd (LBA)
/dev/sda4           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda5           13986       18846    39045951    7  HPFS/NTFS

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e35a52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       29645   238123431   83  Linux
/dev/sdf2           29646       30401     6072570    5  Extended
/dev/sdf5           29646       30401     6072538+  82  Linux swap / Solaris

```


```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdf1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   224,652,959   224,540,505   7 HPFS/NTFS
/dev/sda3         224,669,025   302,760,989    78,091,965   f W95 Ext d (LBA)
/dev/sda5         224,669,088   302,760,989    78,091,902   7 HPFS/NTFS
/dev/sda4         302,760,990   312,496,379     9,735,390  db CP/M / CTOS / ...


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   476,246,924   476,246,862  83 Linux
/dev/sdf2         476,246,925   488,392,064    12,145,140   5 Extended
/dev/sdf5         476,246,988   488,392,064    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-0B0D                              vfat       DellUtility                   
/dev/sda2        26B07A32B07A0917                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4                                               vfat       DellRestore                   
/dev/sda5        FE04D4FB04D4B7BB                       ntfs       Backup                        
/dev/sda: PTTYPE="dos" 
/dev/sdf1        6dd5d882-a159-4e6e-89d1-0d58af737ccb   ext3                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        3dc4da81-e729-43f1-93bb-73a5cb692e7a   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdf1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


=========================== sdf1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-27-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-27-generic ...'
	linux	/boot/vmlinuz-2.6.24-27-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-25-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-25-generic ...'
	linux	/boot/vmlinuz-2.6.24-25-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-24-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-24-generic ...'
	linux	/boot/vmlinuz-2.6.24-24-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-23-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-23-generic ...'
	linux	/boot/vmlinuz-2.6.24-23-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-22-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-22-generic ...'
	linux	/boot/vmlinuz-2.6.24-22-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-21-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-21-generic ...'
	linux	/boot/vmlinuz-2.6.24-21-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux	/boot/vmlinuz-2.6.24-19-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	echo	'Loading Linux 2.6.24-19-generic ...'
	linux	/boot/vmlinuz-2.6.24-19-generic root=UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 6dd5d882-a159-4e6e-89d1-0d58af737ccb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d6-0b0d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 26b07a32b07a0917
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda4)" {
	insmod fat
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 0000-0000
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdf1
UUID=6dd5d882-a159-4e6e-89d1-0d58af737ccb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdf5
UUID=3dc4da81-e729-43f1-93bb-73a5cb692e7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdf1: Location of files loaded by Grub: ===================


 233.2GB: boot/grub/core.img
 233.1GB: boot/grub/grub.cfg
 233.1GB: boot/initrd.img-2.6.24-19-generic
 233.1GB: boot/initrd.img-2.6.24-19-generic.bak
 233.0GB: boot/initrd.img-2.6.24-21-generic
 233.0GB: boot/initrd.img-2.6.24-21-generic.bak
 233.1GB: boot/initrd.img-2.6.24-22-generic
 233.0GB: boot/initrd.img-2.6.24-22-generic.bak
 233.1GB: boot/initrd.img-2.6.24-23-generic
 233.0GB: boot/initrd.img-2.6.24-23-generic.bak
 233.1GB: boot/initrd.img-2.6.24-24-generic
 233.0GB: boot/initrd.img-2.6.24-24-generic.bak
 233.0GB: boot/initrd.img-2.6.24-25-generic
 233.0GB: boot/initrd.img-2.6.24-25-generic.bak
 233.1GB: boot/initrd.img-2.6.24-27-generic
 233.0GB: boot/initrd.img-2.6.24-27-generic.bak
 233.1GB: boot/initrd.img-2.6.32-21-generic
 233.1GB: boot/initrd.img-2.6.32-22-generic
 233.0GB: boot/vmlinuz-2.6.24-19-generic
 233.0GB: boot/vmlinuz-2.6.24-21-generic
 233.0GB: boot/vmlinuz-2.6.24-22-generic
 233.0GB: boot/vmlinuz-2.6.24-23-generic
 233.0GB: boot/vmlinuz-2.6.24-24-generic
 233.0GB: boot/vmlinuz-2.6.24-25-generic
 233.0GB: boot/vmlinuz-2.6.24-27-generic
 233.0GB: boot/vmlinuz-2.6.32-21-generic
 233.1GB: boot/vmlinuz-2.6.32-22-generic
 233.1GB: initrd.img
 233.1GB: initrd.img.old
 233.1GB: vmlinuz
 233.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  b8 00 00 8e d0 bc 00 7c  8e d8 fc b9 80 00 8b f4  |.......|........|
00000010  bf 00 06 8e c0 f3 66 a5  ea 2d 06 00 00 10 00 01  |......f..-......|
00000020  00 00 06 00 00 00 00 00  00 00 00 00 00 e8 c5 00  |................|
00000030  b4 11 cd 16 74 48 3d 00  89 75 43 b4 10 cd 16 33  |....tH=..uC....3|
00000040  db c6 87 be 07 00 80 bf  c2 07 db 74 0e 83 c3 10  |...........t....|
00000050  83 fb 40 72 ec be 47 07  e9 92 00 c6 87 be 07 80  |..@r..G.........|
00000060  c6 87 c2 07 0c 2e c7 06  21 06 00 06 b8 43 00 86  |........!....C..|
00000070  c4 b2 80 be 1d 06 cd 13  72 db 0a e4 75 d7 33 db  |........r...u.3.|
00000080  33 c9 8a 87 be 07 3c 00  74 0c 3c 80 74 05 be 8a  |3.....<.t.<.t...|
00000090  07 eb 5a 41 8b eb 83 c3  10 83 fb 40 72 e4 be 95  |..ZA.......@r...|
000000a0  07 00 0c 80 f9 01 72 4b  77 43 be 58 07 8b c5 c1  |......rKwC.X....|
000000b0  e8 04 00 44 1b ff d7 66  8b 86 c6 07 66 2e a3 25  |...D...f....f..%|
000000c0  06 2e c7 06 21 06 00 7c  b4 42 b2 80 be 1d 06 cd  |....!..|.B......|
000000d0  13 be 80 07 72 17 0a e4  75 13 be 78 07 ff d7 be  |....r...u..x....|
000000e0  ab 07 81 3e fe 7d 55 aa  75 03 e9 13 75 ff d7 b4  |...>.}U.u...u...|
000000f0  00 cd 16 cd 18 b8 03 00  cd 10 b8 00 b8 8e c0 33  |...............3|
00000100  ff b8 20 1f b9 50 00 f3  ab b1 0c be 3b 07 bf 44  |.. ..P......;..D|
00000110  00 ac ab e2 fc b4 02 b7  00 ba 00 02 cd 10 b4 86  |................|
00000120  b9 1e 00 ba 80 84 cd 15  bf 2c 07 c3 ac 3c 00 74  |.........,...<.t|
00000130  09 b4 0e bb 07 00 cd 10  eb f2 c3 77 77 77 2e 64  |...........www.d|
00000140  65 6c 6c 2e 63 6f 6d 43  61 6e 6e 6f 74 20 72 65  |ell.comCannot re|
00000150  73 74 6f 72 65 0d 0a 00  4c 6f 61 64 69 6e 67 20  |store...Loading |
00000160  50 42 52 20 66 6f 72 20  64 65 73 63 72 69 70 74  |PBR for descript|
00000170  6f 72 20 31 2e 2e 2e 00  64 6f 6e 65 2e 0d 0a 00  |or 1....done....|
00000180  66 61 69 6c 65 64 2e 0d  0a 00 42 61 64 20 66 6c  |failed....Bad fl|
00000190  61 67 0d 0a 00 30 20 61  63 74 69 76 65 20 70 61  |ag...0 active pa|
000001a0  72 74 69 74 69 6f 6e 73  0d 0a 00 42 61 64 20 50  |rtitions...Bad P|
000001b0  42 52 0d 0a 00 00 00 00  16 f0 86 e6 00 00 00 01  |BR..............|
000001c0  01 00 de fe 3f 06 3f 00  00 00 08 b7 01 00 80 00  |....?.?.........|
000001d0  01 07 07 fe ff ff 47 b7  01 00 59 37 62 0d 00 00  |......G...Y7b...|
000001e0  81 47 0f fe ff ff 61 2d  64 0d bd 96 a7 04 00 00  |.G....a-d.......|
000001f0  c1 ff db fe ff ff 1e c4  0b 12 de 8c 94 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```


Kansasnoob, you are too kind, sir. Thank you.

---

