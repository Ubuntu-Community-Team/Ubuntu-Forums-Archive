---
title: "Boot stops at BusyBox after Grub2 re-install"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by wadedesk on 2010-08-18
I'm stuck with very limited Linux knowledge.  After copying partitions from 3 hard drives to one new 1-Tb hdd, I found that Windows XP would not boot on the new hard drive.  So I copied it back to an ATA drive and moved Ubuntu to sda1 on the 1-Tb sata drive.  Of course I had to re-install Grub2.  I did using the Ubuntu 10.04 LiveCD.  When I re-booted the Grub2 shell loaded and I had to use the following commands:

```
grub> set prefix=(hd0,1)/boot/grub
grub> set root=(hd0,1)
grub> linux /vmlinuz root=/dev/sda1
grub> initrd /initrd.img
grub> boot
```

Note: I did not use the "read only" command on vmlinuz (ooops)

Just before I get to the BusyBox line, I see the following"

mounting /dev on /root/dev failed
mounting /sys on /root/sys failed
mounting /proc on /root/proc failed
target system doesn't have /sbin/init
no int found. try passing init=bootarg

Any help that gets my Ubuntu 10.04 booting again will be greatly appreciated.

-wade

---

### Post by Rubi1200 on 2010-08-18
Hi,
please boot the computer with the LiveCD.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here and please wrap the text with the # tag.

The results of the bootscript will give us a better overview of your setup and make offering solutions easier.

Thanks.

---

### Post by wadedesk on 2010-08-18
I was hoping that the fix would be easy so I did not go into detail.

I had to install a SATA PCI card in my Gateway in order to use the new 1-Tb hdd.  I originally copied the root to the second primary partition on the 1-Tb drive and was able to get it to boot after reinstalling Grub2.

When Windows XP would not boot, I thought there might be a problem with Ubuntu being in a primary partition, so I moved it to sda11, but it was physically located at the beginning of the Extended Partition.  After reinstalling Grub2 it booted fine once again.  Windows XP would still not run.

So I copied Windows XP to an ATA drive and installed it as the first drive on the Primary controller (0:0).

The two DVD writers, the new SATA writer on (1:0) and the DVD RAM on ATA (1:0) have remained constant throughout the 1-Tb drive installation.

When I boot with the LiveCD, it places the 1-T SATA drive as sdb, however when I boot to Grub2 and do an "ls" it only shows the 1-Tb SATA as HD0 and no other drives.

I tried disconnecting the power on the ATA Windows drive and booting Grub2, but BusyBox came up.  The error before it loaded said that the system had timed-out waiting on a device.

Here is the script I was asked to run:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/home.disk /ubuntu/disks/swap.disk

sdb5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   320,159,384   320,159,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,965,749    40,965,687  83 Linux
/dev/sdb3          40,965,750 1,953,520,064 1,912,554,315   5 Extended
/dev/sdb5          40,965,813   491,524,739   450,558,927   b W95 FAT32
/dev/sdb6         491,524,803   942,083,729   450,558,927   b W95 FAT32
/dev/sdb7         942,083,793 1,392,642,719   450,558,927   b W95 FAT32
/dev/sdb8       1,392,642,783 1,843,185,644   450,542,862   b W95 FAT32
/dev/sdb9       1,843,185,708 1,949,423,489   106,237,782  83 Linux
/dev/sdb10   *  1,949,423,553 1,953,520,064     4,096,512  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       19cd5826-6409-4cc3-b5e3-aecc30dd65f6   ext4                                     
/dev/sda1        58DC09B0DC098A08                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        02b582b0-08d6-4b01-8fa5-784494a93066   ext3       ROOT                          
/dev/sdb10       46ac06b1-b61c-46ac-94fc-8578fb0e3b66   swap                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        1F0D-0F2B                              vfat       DATA-1                        
/dev/sdb6        3785-5F07                              vfat       DATA-2                        
/dev/sdb7        3833-2AF4                              vfat                                     
/dev/sdb8        176b1285-993f-485c-89f6-492df9d35c2b   ext4       DATA-4                        
/dev/sdb9        3bb3ad9b-46b3-4e1b-a0dd-8f7b0dfa868c   ext3       HOME                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		100

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=02b582b0-08d6-4b01-8fa5-784494a93066

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
# defoptions=

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-15-generic
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=02b582b0-08d6-4b01-8fa5-784494a93066 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Chainload into GRUB 2
root		02b582b0-08d6-4b01-8fa5-784494a93066
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		02b582b0-08d6-4b01-8fa5-784494a93066
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=02b582b0-08d6-4b01-8fa5-784494a93066 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=3bb3ad9b-46b3-4e1b-a0dd-8f7b0dfa868c /home           ext3    relatime        0       2
# swap was on /dev/sdb6 during installation
UUID=a4f0dfce-6d5c-4fb5-b5b1-b44c360e52f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  10.1GB: boot/grub/core.img
  10.1GB: boot/grub/menu.lst
  10.1GB: boot/grub/stage2
  10.1GB: boot/initrd.img-2.6.28-15-generic
  10.1GB: boot/initrd.img-2.6.31-20-generic
  10.1GB: boot/initrd.img-2.6.32-23-generic
  10.1GB: boot/initrd.img-2.6.32-24-generic
  10.1GB: boot/vmlinuz-2.6.28-15-generic
  10.1GB: boot/vmlinuz-2.6.31-20-generic
  10.1GB: boot/vmlinuz-2.6.32-23-generic
  10.1GB: boot/vmlinuz-2.6.32-24-generic
  10.1GB: initrd.img
  10.1GB: initrd.img.old
  10.1GB: vmlinuz
  10.1GB: vmlinuz.old

======================== sdb5/Wubi/boot/grub/grub.cfg: ========================

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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 10d8-132e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 10d8-132e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 10d8-132e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 10d8-132e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set faecf926ecf8de37
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 94ceb73eceb71786
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/home.disk /home           ext4    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb5/Wubi: Location of files loaded by Grub: =================


    .9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.32-21-generic
   1.6GB: boot/initrd.img-2.6.32-23-generic
    .3GB: boot/vmlinuz-2.6.32-21-generic
   1.2GB: boot/vmlinuz-2.6.32-23-generic
   1.6GB: initrd.img
    .5GB: initrd.img.old
   1.2GB: vmlinuz
    .3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  6b 46 be ea c2 a5 d7 5b  75 81 48 d4 63 90 62 20  |kF.....[u.H.c.b |
00000010  bc 40 1e e9 d4 7a 85 28  bb 10 c7 83 1a 16 73 b7  |.@...z.(......s.|
00000020  94 8a f9 d6 ff d8 f3 79  f1 b8 6f 5c af 29 72 bb  |.......y..o\.)r.|
00000030  f9 dc e6 5d 7e 1d 33 92  17 13 85 99 99 b4 f4 ca  |...]~.3.........|
00000040  5b db 9f 93 92 69 1f ac  ff fb 42 c0 eb 02 0b 40  |[....i....B....@|
00000050  2b 6b a7 e1 e2 29 3d 0c  6e 74 f3 08 e4 55 53 f5  |+k...)=.nt...US.|
00000060  cb 3f fd aa 73 a0 b6 e2  7e 6b 50 b7 39 39 4a 2e  |.?..s...~kP.99J.|
00000070  6a 7f e0 ea 88 02 bb 0d  39 32 c6 8c 52 22 97 a2  |j.......92..R"..|
00000080  ab 01 c7 11 11 08 56 53  c0 78 d4 93 90 71 f6 1a  |......VS.x...q..|
00000090  74 59 4b 9e 69 f6 43 88  b0 8a 43 79 73 3a e4 49  |tYK.i.C...Cys:.I|
000000a0  00 80 80 c4 d9 72 c8 20  dc e9 99 1d b5 84 df 1b  |.....r. ........|
000000b0  1e 5d ad 24 3d e0 82 2c  71 af fd 16 7a 7f fd bf  |.].$=..,q...z...|
000000c0  df ea bb 4e 40 02 db 8e  69 49 26 63 aa 0f 12 3c  |...N@...iI&c...<|
000000d0  8d 53 2a 77 4a 40 f6 08  b4 a2 e0 41 2a 08 23 84  |.S*wJ@.....A*.#.|
000000e0  99 a1 19 30 14 64 d1 2b  c8 5a 5d 24 04 8e 01 88  |...0.d.+.Z]$....|
000000f0  d6 8e 47 4e ef 89 61 8c  66 56 68 cf 8e 62 82 ff  |..GN..a.fVh..b..|
00000100  fb 42 c0 e7 03 ca 88 73  58 0d 61 05 81 15 06 eb  |.B.....sX.a.....|
00000110  41 97 a5 50 90 61 20 82  86 01 0c ab 32 84 64 c7  |A..P.a .....2.d.|
00000120  5b ce 63 10 a1 0e 20 71  9b b9 90 e4 06 ad 91 96  |[.c... q........|
00000130  e0 aa 10 7e fa b3 5c e1  f9 9b d6 1b f0 7c 32 72  |...~..\......|2r|
00000140  33 2f 0d ed 2b 10 a4 3a  64 e6 95 d2 84 24 05 67  |3/..+..:d....$.g|
00000150  86 1c bc 39 89 55 5c a9  99 31 0b 1a cc 29 49 6d  |...9.U\..1...)Im|
00000160  cd 84 46 cb 11 c0 ef 17  3c f0 44 c0 53 b3 a8 c8  |..F.....<.D.S...|
00000170  d0 9e c0 72 64 41 bf 4b  4a 41 c9 c0 e9 08 6a 95  |...rdA.KJA....j.|
00000180  b4 1c 8a 6a 07 a3 ae 85  c1 ec 07 29 65 66 e6 f6  |...j.......)ef..|
00000190  5a 01 e2 4d 21 43 d6 e2  a8 e9 fe f7 ff ff fb ab  |Z..M!C..........|
000001a0  0f e0 c6 44 35 50 88 f2  6b cc 5d 0e 38 17 61 70  |...D5P..k.].8.ap|
000001b0  b2 17 7a 37 1a ab ff fb  40 c0 eb 02 09 c8 00 fe  |..z7....@.......|
000001c0  ff ff 0b fe ff ff 3f 00  00 00 cf fb da 1a 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff 0e fc  da 1a 0e fc da 1a 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

I'm now guessing that the problem is Windows XP on and old ATA drive, but have no idea how to resolve the issue.

-wade

---

### Post by wadedesk on 2010-08-18
I disconnected the ATA hard drive (with Windows XP installed) from the Gateway and then removed it from BIOS.  I then powered up the computer and configured Grub2 to load Ubuntu 10.04 with no problem on the single SATA hdd.

It appears that the ATA hdd is changing the numbering of the drives during boot-up.  I plan on getting some work done today and will reattach the Windows drive is evening and see if Ubuntu will still load since I now have Grub2 successfully re-installed (or if it defaults to BusyBox again.  I will post the results after the test.

-wade

---

### Post by wadedesk on 2010-08-19
I was able to eliminate the BusyBox messages by setting the Windows ATA drive as the first boot HDD.  This makes the Ubuntu SATA drive the second HDD.

After making the Windows drive the first boot drive, Windows loaded automatically, so I had to re-install Grub2.

After multiple attempts to configure Grub2, when I start up the system, the system halts at the "Grub>" prompt.

Attempts to re-install Grub2 and update the Grub menu list to include Window XP failed.

Windows XP is able to see and access the 1-Tb SATA drive.  Ubuntu is able to see and access the Windows NTFS drive.

Does anyone have any ideas as how to get the Grub2 menu to load and update it to include Windows XP as a boot option?

---

