---
title: "Partition table error?"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by EngDrewman on 2011-02-05
I have an old HP laptop that I recently reinstalled WinXP on. The system is dual boot XP and Ubuntu 10.10. Prior to the re-installation, the partitions looked like this: (note: [sdXX] = extended partition)

| sda1 XP | sda2 Data [ sda5 Ubuntu | sda6 swap ]

After XP setup finished, I booted the Ubuntu CD to re-install grub. Looks like the XP installer got confused by the linux partitions--when you open Disk Utility, the partitions after sda2 are nonsense, and gparted thinks the disk is empty. I tried the usual grub re-installation commands:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo update-grub
```
Ran with no problems, other than a warning about flexnet.

Then I rebooted and grub went into recovery mode. Looks like the XP installer re-labeled sda5 as "msdos6". Don't know what "msdos4" is, and the swap partition is M.I.A. Here's the commands:

```
grub> ls
(hd0) (hd0,msdos6) (hd0,msdos4) (hd0,msdos2) (hd0,msdos1)
```

The following commands successfully boot Ubuntu:
```
set prefix=(hd0,msdos6)/boot/grub
set root=(hd0,msdos6)
set
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

Once I got Ubuntu up and running, I tried update-grub again, no luck. Am I right that the XP installer messed up the partition table? How do I fix it?

---

### Post by Rubi1200 on 2011-02-05
Hi,
please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

---

### Post by EngDrewman on 2011-02-05
Here are the results:
Note: sdb is my flash drive, sda is the hard drive

Also, filesystems: XP=NTFS, data ("exchange" label) = fat, ubuntu=ext3

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/sda2         245,762,370   247,850,819     2,088,450   6 FAT16
/dev/sda3         247,850,820   312,576,704    64,725,885   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         247,850,946   310,520,384    62,669,439  83 Linux
/dev/sda4         310,520,385   312,576,704     2,056,320  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 256 MB, 256900608 bytes
255 heads, 63 sectors/track, 31 cylinders, total 501759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       498,014       497,952   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        243413FA3413CDA4                       ntfs                                     
/dev/sda2        009C-DDF2                              vfat       EXCHANGE                      
/dev/sda3: PTTYPE="dos" 
/dev/sda4        f04328cb-6b2a-429e-9a3e-b5b53b06d01a   swap                                     
/dev/sda5        e08d4e88-019b-4082-b2f7-f550749db3aa   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        282E-2ABA                              vfat       GEEK SQUAD                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/GEEK SQUAD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

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
default		6

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
# kopt=root=UUID=e08d4e88-019b-4082-b2f7-f550749db3aa ro

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=e08d4e88-019b-4082-b2f7-f550749db3aa ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=e08d4e88-019b-4082-b2f7-f550749db3aa ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=e08d4e88-019b-4082-b2f7-f550749db3aa ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=e08d4e88-019b-4082-b2f7-f550749db3aa ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=e08d4e88-019b-4082-b2f7-f550749db3aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda2
UUID=009C-DDF2  /media/hda2     vfat    utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=E4A45FCDA45FA13A /media/hda1        ntfs    defaults,umask=007,gid=46 0       0
# /dev/hda5
UUID=f04328cb-6b2a-429e-9a3e-b5b53b06d01a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 133.8GB: boot/grub/core.img
 133.8GB: boot/grub/menu.lst
 133.8GB: boot/grub/stage2
 133.7GB: boot/initrd.img-2.6.24-21-generic
 133.8GB: boot/initrd.img-2.6.24-21-generic.bak
 133.7GB: boot/initrd.img-2.6.27-14-generic
 133.8GB: boot/initrd.img-2.6.28-17-generic
 134.5GB: boot/initrd.img-2.6.31-17-generic
 133.8GB: boot/initrd.img-2.6.32-25-generic
 133.8GB: boot/initrd.img-2.6.35-22-generic
 133.8GB: boot/initrd.img-2.6.35-23-generic
 133.8GB: boot/vmlinuz-2.6.24-21-generic
 133.7GB: boot/vmlinuz-2.6.27-14-generic
 133.8GB: boot/vmlinuz-2.6.28-17-generic
 133.8GB: boot/vmlinuz-2.6.31-17-generic
 133.8GB: boot/vmlinuz-2.6.32-25-generic
 133.8GB: boot/vmlinuz-2.6.35-22-generic
 133.8GB: boot/vmlinuz-2.6.35-23-generic
 133.8GB: initrd.img
 133.8GB: initrd.img.old
 133.8GB: vmlinuz
 133.8GB: vmlinuz.old

```

---

### Post by oldfred on 2011-02-05
Your sda6 was reset to sda4, but if it is sda4 it has to be a primary and connot be inside the extended or it has to change it name back to sda6.

First backup partition table and copy to another device.
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

Sometimes since it is just numbering this works.
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v

If that does not work we can try test disk or one of these:
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)
Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)

---

### Post by EngDrewman on 2011-02-05
Ran those commands, no problem, wrote new partition table. Now (hd0,msdos5) corresponds with /dev/sda5. Rebooted the live CD, ran the grub re-installation commands I listed earlier, reboot and I still get grub recovery mode. What is going on?

BTW here are the results of the fdisk commands:
```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# sfdisk -d /dev/sda > pt.txt
root@ubuntu:~# fdisk /dev/sda
omitting empty partition (5)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): r

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6e1f6e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       15428     1044225    6  FAT16
/dev/sda3           15429       19457    32362942+   5  Extended
/dev/sda4           19330       19457     1028160   82  Linux swap / Solaris
/dev/sda5           15429       19329    31334719+  83  Linux

Command (m for help): v
Remaining 5290 unallocated 512-byte sectors

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
root@ubuntu:~# 

```

---

### Post by Rubi1200 on 2011-02-05
Are you still on the LiveCD?

If yes, please run these commands:

```
sudo fdisk -lu

sudo sfdisk -V
```

Post the output.

I also recommend you run the boot script again and post it here since things have now changed.

Thanks.

---

### Post by EngDrewman on 2011-02-06
Ah ha- figured it out. My installation is several years old, and apparently the distribution upgrades did not auto upgrade me to grub 2, so I was left with part grub v1 and grub v2. Finishing the upgrade to grub 2 did the trick. Thanks for your help!

---

### Post by Rubi1200 on 2011-02-06
Glad you got things sorted out :-)

---

