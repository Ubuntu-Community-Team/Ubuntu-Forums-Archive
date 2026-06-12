---
title: "restoring grub after a &quot;successful&quot; hd clone"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by andrew732 on 2011-02-15
I used GParted Live CD to clone my hard drive to a larger one, keeping the dual boot partition structure intact.  This is the GParted view of the new hd after cloning, identical to the old one except for amount of free space:

[IMG]http://i7.photobucket.com/albums/y269/silentheart1/gp2.jpg[/IMG]

And here is the output from fdisk:

```
user@debian:/$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070e92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488381440    7  HPFS/NTFS
/dev/sda2           60801      121602   488379392    5  Extended
/dev/sda5   *       60801      120854   482368512   83  Linux
/dev/sda6          120854      121602     6008832   82  Linux swap / Solaris
```Little did I know that the apparently seamless cloning operation would wipe out grub and prevent me from booting as on the old hd.  The problem now is that I can't restore grub 0.97.  For starters, I can't boot into Windows or Linux regardless of which partition above has the boot flag.  (In that picture the Windows partition has the boot flag.)  Next, I tried a standard recovery of grub.  When I run grub from the GParted Live CD command line, I get this:

```

grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

grub> root (hd0, 4)

Error 11: Unrecognized device string

grub> root (hd0, 0)

Error 11: Unrecognized device string
```The Linux partition definitely has /boot/grub/stage1 on it and that partition on /dev/sda should be referred to in grub as (hd0,4) right?  What is going on and what can I do to fix it?  I've seen related issues discussed but never this exact problem plus a solution.  Thanks for any help~

---

### Post by oldfred on 2011-02-15
Are you sure you still have grub legacy & not grub2? You do not have both old & new drives mounted do you. Identical UUIDs will cause confusion.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by andrew732 on 2011-02-15
OK, thanks for the quick reply.  Yes it is grub legacy and only the new drive was connected.  Here is my results.txt file:



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 1379960832 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   976,764,927   976,762,880   7 HPFS/NTFS
/dev/sda2         976,764,928 1,953,523,711   976,758,784   5 Extended
/dev/sda5    *    976,766,976 1,941,503,999   964,737,024  83 Linux
/dev/sda6       1,941,506,048 1,953,523,711    12,017,664  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        54ECC055ECC03352                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3d7a8046-b657-4da1-8923-5b2d6142c933   ext3                                     
/dev/sda6        d29bdd38-19c7-4c73-a02e-c918021a6470   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=3d7a8046-b657-4da1-8923-5b2d6142c933 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d7a8046-b657-4da1-8923-5b2d6142c933

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid        3d7a8046-b657-4da1-8923-5b2d6142c933
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=3d7a8046-b657-4da1-8923-5b2d6142c933 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid        3d7a8046-b657-4da1-8923-5b2d6142c933
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=3d7a8046-b657-4da1-8923-5b2d6142c933 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        3d7a8046-b657-4da1-8923-5b2d6142c933
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
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3d7a8046-b657-4da1-8923-5b2d6142c933 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d29bdd38-19c7-4c73-a02e-c918021a6470 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 706.6GB: boot/grub/menu.lst
 706.5GB: boot/grub/stage2
 706.6GB: boot/initrd.img-2.6.28-16-generic
 706.6GB: boot/initrd.img-2.6.31-21-generic
 706.5GB: boot/initrd.img-2.6.32-23-generic
 706.6GB: boot/initrd.img-2.6.32-24-generic
 706.5GB: boot/initrd.img-2.6.32-25-generic
 706.6GB: boot/vmlinuz-2.6.28-16-generic
 706.5GB: boot/vmlinuz-2.6.31-21-generic
 706.6GB: boot/vmlinuz-2.6.32-23-generic
 706.5GB: boot/vmlinuz-2.6.32-24-generic
 706.6GB: boot/vmlinuz-2.6.32-25-generic
 706.5GB: initrd.img
 706.6GB: initrd.img.old
 706.6GB: vmlinuz
 706.5GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

---

### Post by presence1960 on 2011-02-15
Boot the ubuntu Live CD/USB. Choose "try ubuntu". When the desktop loads open a terminal and do this:

```
1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,4)", 
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

```

---

### Post by andrew732 on 2011-02-16
Thanks, worked like a charm.  That's exactly what I did at first, except I was using the GParted Live CD.  In case anyone comes across this thread, here's the lesson: don't use the GParted Live CD to restore grub, use a regular Ubuntu live cd!

---

### Post by presence1960 on 2011-02-16
> **andrew732 said:**
> Thanks, worked like a charm.  That's exactly what I did at first, except I was using the GParted Live CD.  In case anyone comes across this thread, here's the lesson: don't use the GParted Live CD to restore grub, use a regular Ubuntu live cd!

You are welcome- enjoy ubuntu.

---

