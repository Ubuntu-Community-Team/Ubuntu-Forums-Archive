---
title: "Reinstalling grub fails after Windows 7"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by PlatosGimp on 2011-01-15
I previously had a single 160gb drive with two partitions, dual booted for Ubuntu and XP. I then installed a new SSD drive and put Windows 7 on it and of course I lost grub on the MBR. I have gone through this before so I went ahead and booted the livd CD, installed grub then ran

root (hd0,1)
setup (hd0)


but then got these errors;

Error 22: No such partition
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition


Results of fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008507c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9689    77826861    7  HPFS/NTFS
/dev/sda2            9690       19457    78461460   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02c41b16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7650    61440000    7  HPFS/NTFS
/dev/sdb2            7650       14594    55777280    7  HPFS/NTFS

Disk /dev/dm-0: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008507c

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1        9689    77826861    7  HPFS/NTFS
/dev/dm-0p2            9690       19457    78461460   83  Linux

Disk /dev/dm-1: 79.7 GB, 79694705664 bytes
255 heads, 63 sectors/track, 9688 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 80.3 GB, 80344535040 bytes
255 heads, 63 sectors/track, 9768 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

---

### Post by presence1960 on 2011-01-15
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by PlatosGimp on 2011-01-16
Thanks kindly....GREAT script! Never knew about this. Also thanks for offering to help. Below is the output.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/nvidia_dccbbfaf

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

nvidia_dccbbfaf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

nvidia_dccbbfaf2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   122,882,047   122,880,000   7 HPFS/NTFS
/dev/sdb2         122,882,048   234,436,607   111,554,560   7 HPFS/NTFS


Drive: nvidia_dccbbfaf ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_dccbbfaf: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581806 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_dccbbfaf1   *             63   155,653,784   155,653,722   7 HPFS/NTFS
/dev/mapper/nvidia_dccbbfaf2        155,653,785   312,576,704   156,922,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_dccbbfaf1 0260FF3560FF2DD3                       ntfs       Windows XP                    
/dev/mapper/nvidia_dccbbfaf2 c67fcc28-1a4b-46f3-95f1-17bec81fe76b   ext4                                     
/dev/mapper/nvidia_dccbbfaf: PTTYPE="dos" 
/dev/sda                                                silicon_medley_raid_member                               
/dev/sdb1        1AB6AA91B6AA6CC7                       ntfs       System                        
/dev/sdb2        C8DC3910DC38F9F0                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
error: and: No such file or directory
error: /dev/mapper//dev/sda:: No such file or directory
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: discovered: No such file or directory
error: formats: No such file or directory
error: "nvidia": No such file or directory
error: nvidia)!: No such file or directory
error: "sil": No such file or directory
error: (using: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_dccbbfaf
nvidia_dccbbfaf1
nvidia_dccbbfaf2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


========================== nvidia_dccbbfaf1/boot.ini: ==========================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTOUT


===================== nvidia_dccbbfaf2/boot/grub/menu.lst: =====================

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
# kopt=root=/dev/mapper/nvidia_dccbbfaf2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_dccbbfaf2 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_dccbbfaf2 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

#title		Ubuntu 10.10, kernel 2.6.32-24-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/nvidia_dccbbfaf2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/nvidia_dccbbfaf2 ro  single
#initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.10, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin

title Windows XP Pro
rootnoverify (hd0,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST







========================= nvidia_dccbbfaf2/etc/fstab: =========================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/mapper/nvidia_dccbbfaf2 :
UUID=c67fcc28-1a4b-46f3-95f1-17bec81fe76b	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc1 :
#UUID=BE78B33C78B2F1EF	/mnt/Removable	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/mapper/nvidia_dccbbfaf1 :
#UUID=0260FF3560FF2DD3	/media/Windows_XP	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sdb2 :
UUID=C28CFB6F8CFB5BFB	/mnt/Data(Local)	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sdb1 :
UUID=bccc498a-1dac-4f64-9a24-0ec45aaf1a06	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
#192.168.1.3:/					/mnt/Servers/Penguin		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.4:/					/mnt/Servers/Trixbox		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.182:/				/mnt/Servers/Epiphany		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.200:/				/mnt/Servers/Monitor		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Data/Shared	/mnt/NAS-Penguin/Data/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.3:/mnt/NAS-Penguin/Data/Private	/mnt/NAS-Penguin/Data/Private	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Media/Shared	/mnt/NAS-Penguin/Media/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Media/Private	/mnt/NAS-Penguin/Media/Private	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Data/Private/jstork	/home/jstork/Documents	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.250:/raid0/data/Media		/mnt/NAS-Thecus/Media		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.250:/raid0/data/Data			/mnt/NAS-Thecus/Data		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#//192.168.1.35/pvr-data			/home/jstork/Video-PVR		cifs	auto,credentials=/home/jstork/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
//192.168.1.35/pvr-data				/home/jstork/Video-PVR		cifs	auto,user=jstork,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
//192.168.1.210/video				/home/jstork/Video-NAS		cifs	auto,user=jstork	0	0
#sudo mount -t cifs //192.168.1.35/pvr-data 	/home/jstork/Videos/ -o user=jstork
#Temporary Mounts to OldPenguin
#192.168.1.165:/mnt/NAS-Penguin/Data/Private/jstork	/home/jstork/Documents		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0	
#192.168.1.165:/mnt/NAS-Penguin/Data/Shared	/mnt/NAS-Penguin/Data/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.165:/mnt/NAS-Penguin/Media/Shared	/mnt/NAS-Penguin/Media/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.165:/mnt/NAS-Penguin/Media/Private	/mnt/NAS-Penguin/Media/Private	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#/dev/sdc1      				/mnt/Removeable          		ntfs   defaults 0 0



============= nvidia_dccbbfaf2: Location of files loaded by Grub: =============


  87.4GB: boot/grub/menu.lst
  80.0GB: boot/grub/stage2
 115.0GB: boot/initrd.img-2.6.32-24-generic
 149.7GB: boot/initrd.img-2.6.35-22-generic
 106.9GB: boot/initrd.img-2.6.35-23-generic
 106.5GB: boot/initrd.img-2.6.35-24-generic
 108.5GB: boot/vmlinuz-2.6.32-24-generic
 100.5GB: boot/vmlinuz-2.6.35-22-generic
 105.5GB: boot/vmlinuz-2.6.35-23-generic
 106.4GB: boot/vmlinuz-2.6.35-24-generic
 106.5GB: initrd.img
 106.9GB: initrd.img.old
 106.4GB: vmlinuz
 105.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sda: "sil" and "nvidia" formats discovered (using nvidia)! 
=============================== StdErr Messages: ===============================

ERROR: nvidia: wrong # of devices in RAID set "nvidia_dccbbfaf" [1/2] on /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_dccbbfaf" [1/2] on /dev/sda
ERROR: only one argument allowed for this option
ERROR: nvidia: wrong # of devices in RAID set "nvidia_dccbbfaf" [1/2] on /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_dccbbfaf" [1/2] on /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_dccbbfaf" [1/2] on /dev/sda
ERROR: only one argument allowed for this option

---

### Post by Quackers on 2011-01-16
You appear to be using raid, is that correct?

---

### Post by presence1960 on 2011-01-16
Your sda disk is set up in RAID. You need to change that. Go into BIOS and disable RAID (if in fact it is enabled), save changes to CMOS and continue booting to the ubuntu Live CD/USB. Boot to the desktop (try ubuntu), open a terminal and run ```
dmraid -E -r /dev/sda
```

Open up gparted now (System > Administration > Gparted Partition Editor), once gparted loads make sure the 160 Gb disk is labeled sda, instead of /dev/mapper/nvidia_dccbbfaf.

If the nvidia name is gone reboot without the Live CD/USB and lets see what happens. If booting fails run another boot info script and post the results.

---

### Post by Quackers on 2011-01-16
Beware! If you are using raid0 and change to AHCI or other non-raid, you will lose any existing operating system!

---

### Post by PlatosGimp on 2011-01-16
Actually I am not running any RAID on the Asus P5KPL-cm MB. Not sure why the OS would "think" it was RAID

---

### Post by PlatosGimp on 2011-01-16
Actually I am not running any RAID on the Asus P5KPL-cm MB. Not sure why the OS would "think" it was RAID

---

### Post by Quackers on 2011-01-16
In that case from the live cd terminal run presence1960's suggestion preceding it with sudo, and the raid metadata should disappear. See if your problems disappear too :-)

---

### Post by PlatosGimp on 2011-01-20
No luck yet. I rebooted into the live cd, rand the dmraid command, then back to installing grub and trying to rerun the grub commands, but same errors.

root (hd0,1)
setup (hd0)



Error 22: No such partition
grub> setup (hd0)
setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

---

### Post by presence1960 on 2011-01-20
> **PlatosGimp said:**
> No luck yet. I rebooted into the live cd, rand the dmraid command, then back to installing grub and trying to rerun the grub commands, but same errors.

root (hd0,1)
setup (hd0)



Error 22: No such partition
grub> setup (hd0)
setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

Please post the output of a new boot info script since you ran the command, so we can see exactly what we have now.

---

### Post by Quackers on 2011-01-20
Firstly, what happened when you ran the dmraid command, and which command did you run? 
Secondly, are you trying to install grub legacy? Grub2 is the default for 10.10.
Are you perhaps using a guide that was written a long time ago?

---

### Post by PlatosGimp on 2011-01-21
Well I made progress, but things are certainly still hooped. When I first ran the dmraid command, it found metadata for sil and nvidia raid. First this is bizzare since there is NO RAID on this box/mb.

The grub commands in the previous post failed. So when I rebooted again into the live cd, I decided to check again with the dmraid command and so this time it still found the sil metadata. I guess I only removed the nvidia stuff the first time

After removing the sil metadata, running fdisk -l now only showed partitions on the two drives sda and sdb.

I then re-ran the grub commands

sudo apt-get install grub
sudo grub

root (hd0,1)
setup (hd0)
quit

This time NO ERRORS so I rebooted.

I was excited now since I DID GET THE ORIGINAL GRUB MENU! 

But trying to boot Ubuntu I noticed the

"Starting now" ( or something like that, I didnt write it down)

It sat there and then returned various messages I had never seen, but the improtant one seems to be


Alert! /dev/mapper/nvidia_dccbbfaf2 does not exist Dropping to a shell.

I then hit enter, or ctl-alt-del (forgot now) and I then got the Windows 7 boot boot menu? 

At least I can still boot into Windows 7 and the previous XP which is still on the second partition of the first drive.

I am losing faith that this can be fixed now but if anyone has any ideas I can still keep trying.

With so many people running both Windows and Ubuntu, I would think this might warrant some grub/mbr recovery tools for idiots, right off the live cd so we can fix these things easily.

:)



Here is the output. Clearly the entries in menu are still pointing to nvidia raid which for the life of me I dont know why they were there.

Given where the Ubuntu partition is installed, can I just edit the entries and point them to /dev/sda1?



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *             63   155,653,784   155,653,722   7 HPFS/NTFS
/dev/sda2         155,653,785   312,576,704   156,922,920  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   122,882,047   122,880,000   7 HPFS/NTFS
/dev/sdb2         122,882,048   234,436,607   111,554,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0260FF3560FF2DD3                       ntfs       Windows XP                    
/dev/sda2        c67fcc28-1a4b-46f3-95f1-17bec81fe76b   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1AB6AA91B6AA6CC7                       ntfs       System                        
/dev/sdb2        C8DC3910DC38F9F0                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTOUT


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
# kopt=root=/dev/mapper/nvidia_dccbbfaf2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_dccbbfaf2 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_dccbbfaf2 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

#title		Ubuntu 10.10, kernel 2.6.32-24-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/nvidia_dccbbfaf2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/nvidia_dccbbfaf2 ro  single
#initrd		/boot/initrd.img-2.6.32-24-generic

#title		Ubuntu 10.10, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin

title Windows XP Pro
rootnoverify (hd0,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST







=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/mapper/nvidia_dccbbfaf2 :
UUID=c67fcc28-1a4b-46f3-95f1-17bec81fe76b	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc1 :
#UUID=BE78B33C78B2F1EF	/mnt/Removable	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/mapper/nvidia_dccbbfaf1 :
#UUID=0260FF3560FF2DD3	/media/Windows_XP	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sdb2 :
UUID=C28CFB6F8CFB5BFB	/mnt/Data(Local)	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sdb1 :
UUID=bccc498a-1dac-4f64-9a24-0ec45aaf1a06	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
#192.168.1.3:/					/mnt/Servers/Penguin		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.4:/					/mnt/Servers/Trixbox		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.182:/				/mnt/Servers/Epiphany		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.200:/				/mnt/Servers/Monitor		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Data/Shared	/mnt/NAS-Penguin/Data/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.3:/mnt/NAS-Penguin/Data/Private	/mnt/NAS-Penguin/Data/Private	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Media/Shared	/mnt/NAS-Penguin/Media/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Media/Private	/mnt/NAS-Penguin/Media/Private	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
192.168.1.3:/mnt/NAS-Penguin/Data/Private/jstork	/home/jstork/Documents	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.250:/raid0/data/Media		/mnt/NAS-Thecus/Media		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.250:/raid0/data/Data			/mnt/NAS-Thecus/Data		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#//192.168.1.35/pvr-data			/home/jstork/Video-PVR		cifs	auto,credentials=/home/jstork/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
//192.168.1.35/pvr-data				/home/jstork/Video-PVR		cifs	auto,user=jstork,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
//192.168.1.210/video				/home/jstork/Video-NAS		cifs	auto,user=jstork	0	0
#sudo mount -t cifs //192.168.1.35/pvr-data 	/home/jstork/Videos/ -o user=jstork
#Temporary Mounts to OldPenguin
#192.168.1.165:/mnt/NAS-Penguin/Data/Private/jstork	/home/jstork/Documents		nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0	
#192.168.1.165:/mnt/NAS-Penguin/Data/Shared	/mnt/NAS-Penguin/Data/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.165:/mnt/NAS-Penguin/Media/Shared	/mnt/NAS-Penguin/Media/Shared	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#192.168.1.165:/mnt/NAS-Penguin/Media/Private	/mnt/NAS-Penguin/Media/Private	nfs	auto,intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,timeo=14,tcp,noatime	0	0
#/dev/sdc1      				/mnt/Removeable          		ntfs   defaults 0 0



=================== sda2: Location of files loaded by Grub: ===================


  87.4GB: boot/grub/menu.lst
  80.0GB: boot/grub/stage2
 115.0GB: boot/initrd.img-2.6.32-24-generic
 149.7GB: boot/initrd.img-2.6.35-22-generic
 106.9GB: boot/initrd.img-2.6.35-23-generic
 106.5GB: boot/initrd.img-2.6.35-24-generic
 108.5GB: boot/vmlinuz-2.6.32-24-generic
 100.5GB: boot/vmlinuz-2.6.35-22-generic
 105.5GB: boot/vmlinuz-2.6.35-23-generic
 106.4GB: boot/vmlinuz-2.6.35-24-generic
 106.5GB: initrd.img
 106.9GB: initrd.img.old
 106.4GB: vmlinuz
 105.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd

---

### Post by presence1960 on 2011-01-21
> **PlatosGimp said:**
> Well I made progress, but things are certainly still hooped. When I first ran the dmraid command, it found metadata for sil and nvidia raid. First this is bizzare since there is NO RAID on this box/mb.

The grub commands in the previous post failed. So when I rebooted again into the live cd, I decided to check again with the dmraid command and so this time it still found the sil metadata. I guess I only removed the nvidia stuff the first time

After removing the sil metadata, running fdisk -l now only showed partitions on the two drives sda and sdb.

I then re-ran the grub commands

sudo apt-get install grub
sudo grub

root (hd0,1)
setup (hd0)
quit

This time NO ERRORS so I rebooted.

I was excited now since I DID GET THE ORIGINAL GRUB MENU! 

But trying to boot Ubuntu I noticed the

"Starting now" ( or something like that, I didnt write it down)

It sat there and then returned various messages I had never seen, but the improtant one seems to be


Alert! /dev/mapper/nvidia_dccbbfaf2 does not exist Dropping to a shell.

I then hit enter, or ctl-alt-del (forgot now) and I then got the Windows 7 boot boot menu? 

At least I can still boot into Windows 7 and the previous XP which is still on the second partition of the first drive.

I am losing faith that this can be fixed now but if anyone has any ideas I can still keep trying.

With so many people running both Windows and Ubuntu, I would think this might warrant some grub/mbr recovery tools for idiots, right off the live cd so we can fix these things easily.

:)



PS: I will go back into them live cd and re-run the script....when I was able to re-run the grub commands without errors I thoguht it was fixed.

Run another boot info script and post the results. otherwise Quackers and I are going to have to try to find a crystal ball!

---

### Post by Quackers on 2011-01-21
Thanks for the boot script output.
Firstly, as you have 2 hard drives I would run both of these commands 
```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` as you may still have metadata on sdb
Secondly, you still seem to be trying to install grub legacy. Are you using an old guide? Grub2 is the default bootloader for 10.10.
As you have no grub.core.img at the moment, my suggestion is that you purge grub legacy and what exists of grub2 and re-install grub2 following the guide below.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

See if presence1960 agrees :-)

---

### Post by presence1960 on 2011-01-21
```
title Ubuntu 10.10, kernel 2.6.35-22-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.35-22-generic root=/dev/[COLOR="Red"]mapper/nvidia_dccbbfaf2[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic
```

Boot to the GRUB menu. Highlight the 2.6.35-22 kernel. Hit "e" to edit. Change the red text above sda2

I am not quite sure which combination of keys to depress after you edit to boot, but look at the bottom and it will tell you.

If it boots to ubuntu open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```That is a lowercase L in .lst!

Edit all the ubuntu entries as you did at the grub menu. Click Save and close file. you should be good to go.

---

### Post by presence1960 on 2011-01-21
> **Quackers said:**
> Thanks for the boot script output.
Firstly, as you have 2 hard drives I would run both of these commands 
```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` as you may still have metadata on sdb
Secondly, you still seem to be trying to install grub legacy. Are you using an old guide? Grub2 is the default bootloader for 10.10.
As you have no grub.core.img at the moment, my suggestion is that you purge grub legacy and what exists of grub2 and re-install grub2 following the guide below.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

See if presence1960 agrees :-)

```
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

```
Let's see if it boots first, then he can convert if he wishes.

---

### Post by Quackers on 2011-01-21
No problem :-) my concern really is the metadata that may be on sdb. It's time I had a cup of tea anyway :wink:

---

### Post by presence1960 on 2011-01-21
> **Quackers said:**
> No problem :-) my concern really is the metadata that may be on sdb. It's time I had a cup of tea anyway :wink:

Tea sounds good right now!

---

### Post by Quackers on 2011-01-21
Lol, you're not in Boston then :wink:

---

### Post by presence1960 on 2011-01-21
> **Quackers said:**
> Lol, you're not in Boston then :wink:

LOL! I am in Philadelphia, PA

---

### Post by PlatosGimp on 2011-01-21
Thanks everyone. Finally got it. Yes, changing the path in menu.1st booted me back to Ubuntu! And when I select the "Windows XP" boot menu option, I get the new Windows 7 boot menu where I can launch either 7 or XP. So for now all is good and when I get a second SSD I will re-install Ubuntu fresh on the SSD and can then dump XP and the current Ubuntu running on a sata drive.

Thanks everyone for all your help. :)

---

### Post by Quackers on 2011-01-21
Nice one :-)  We like happy endings!

---

