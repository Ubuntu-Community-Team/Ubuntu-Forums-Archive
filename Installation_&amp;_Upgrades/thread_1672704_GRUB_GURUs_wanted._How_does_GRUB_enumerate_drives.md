---
title: "GRUB GURUs wanted. How does GRUB enumerate drives?"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Paulzy on 2011-01-21
GRUB experts wanted.
I need to know how GRUB is enumerating my drives.
My disk layout as seen by the System Monitor is thulsy (??):

SATA HDD
/sda1	System part for Win7
/sda2	Win7 OS part

SEAGATE
/sdb1	Recovery part for XP
/sdb2	XP OS part

MAXSTOR
/sdc1	NTFS data drive (non-parted)

USB HITACHI
/sdd5	/ext3 Linux OS part
/sdd7	NTFS data part

USB WD
/sde1	FAT32 data drive (non-parted)

My PC is an AMD quad core (Phenom IIX4 965, 4GB RAM) and has
W7 on a SATA drive. I, for the moment, do not want to to tri-boot
with Linux, XP and 7. I just want to boot to Linux and XP via the 
F12 boot key, which works. Sort of, I can't get to either because
GRUB is getting the wrong partition numbers. I get the menu, but hit
Error 22 (Partition doesn't exist).

Previously, XP was root (hd0,1). However, since being put in the
new PC the hd# enumeration changed. GRUB is still located in hd3,4
as it was before. I assumed W7 was hd0,0 so when I tried hd1,1 for
XP I got Error 22 (Part not exist). I tried 0,1 and it appeared to
hang at the "Starting up..." verbose.

My request is this: can some GRUB GURU help me figure out how
GRUB enumerated my drives so I can place the right numbers in?

---

### Post by presence1960 on 2011-01-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by psusi on 2011-01-21
It enumerates them in the order your bios provides them.  It sounds like you are using grub legacy.  You should upgrade to grub2, which does away with this sort of problem.  Otherwise, you need to configure your /boot/grub/device.map file to explain to grub legacy which linux device corresponds to which bios device.

---

### Post by Rubi1200 on 2011-01-21
+1 to the boot script suggested by presence1960

The results will show us clearly where everything is and make offering solutions a lot easier.

In fact, it may simply involve changing some lines in fstab to achieve what you want.

---

### Post by Paulzy on 2011-01-23
Thanks gentlemen, I will do as you suggest and report back.


Paul James Chatman  
Posted via my &#63723; Bold II 9700

---

### Post by Paulzy on 2011-01-25
> **presence1960 said:**
> Let's get a better look at your setup & boot process...
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```


Here is the output. So how should I setup the menu.lst, I'll install GRUB2 later, but for now I just want to be able to boot the volumes.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => HP/Gateway is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd7 starts 
                       at sector 125. But according to the info from fdisk, 
                       sdd7 starts at sector 6249411.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:   
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     9,359,279     9,359,217   b W95 FAT32
/dev/sdb2    *      9,359,280   156,280,319   146,921,040   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 10.1 GB, 10110320640 bytes
240 heads, 63 sectors/track, 1306 cylinders, total 19746720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    19,746,719    19,746,657   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd2    *      6,249,285   625,137,344   618,888,060   5 Extended
/dev/sdd5         310,263,408   616,028,489   305,765,082  83 Linux
/dev/sdd6         616,028,553   625,137,344     9,108,792  82 Linux swap / Solaris
/dev/sdd7           6,249,411   310,263,344   304,013,934   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        54CC83D1CC83AC34                       ntfs       System                        
/dev/sda2        E41C84DE1C84AD5C                       ntfs       PAUL-W7HP                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2E35-2EF9                              vfat       HP_RECOVERY                   
/dev/sdb2        00AC81F1AC81E190                       ntfs       PAUL-WXPH                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6628E4D628E4A5F1                       ntfs       PAUL-AREA2                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        b9dba18a-a184-4a50-a0f1-186e2939fd47   ext3                                     
/dev/sdd6        a7c622fa-1fb2-41b2-bcdf-84c688494d0e   swap                                     
/dev/sdd7        86B831BCB831AC15                       ntfs       PAUL-AREA3                    
/dev/sdd: PTTYPE="dos" 
/dev/sde1        7CFF-D2EA                              vfat       PAULZY-BOOK                   
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PAUL-AREA2        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd5        /media/b9dba18a-a184-4a50-a0f1-186e2939fd47 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd7        /media/PAUL-AREA3        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde1        /media/PAULZY-BOOK       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda2        /media/PAUL-W7HP         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/PAUL-WXPH         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sdb2/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=========================== sdd5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
#
#	Fri 21 Jan 2011 12:07:15 PM UTC  root  
#	UBUNTU 9.10

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
timeout		45

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color yellow/blue white/green

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
# kopt=root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,4)

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


title		Ubuntu 9.10 [Linux 2.6.31-22 KARMIC]
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Windows XP Home Edition SP3 [Area C]
root		(hd1,1)
savedefault
chainloader	+1

title		Windows 7 Home Premium [Area C]
root		(hd0,1)
savedefault
chainloader	+1

title		Ubuntu 9.10 RECOVERY MODE [Linux 2.6.31-22 KARMIC]
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		HP PC System Recovery (Normal / Destructive Modes) [Area D]
root		(hd1,0)
savedefault
chainloader	+1

title		Ubuntu 9.10 Linux Memory Test [memtest86+]
root		(hd3,4)
kernel		/boot/memtest86+.bin
quiet

## Old Linux Kernels ##

## title Ubuntu 9.10, kernel 2.6.27-17-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.27-17-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.27-17-generic
## quiet
 
## title Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.27-17-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.27-17-generic

## title Ubuntu 9.10, kernel 2.6.24-27-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-27-generic
## quiet

## title Ubuntu 9.10, kernel 2.6.24-27-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-27-generic

## title Ubuntu 9.10, kernel 2.6.24-26-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-26-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-26-generic
## quiet

## title Ubuntu 9.10, kernel 2.6.24-26-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-26-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-26-generic

## title Ubuntu 9.10, kernel 2.6.24-25-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-25-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-25-generic
## quiet
 
## title Ubuntu 9.10, kernel 2.6.24-25-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-25-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-25-generic

## title Ubuntu 9.10, kernel 2.6.24-24-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-24-generic
## quiet
 
## title Ubuntu 9.10, kernel 2.6.24-24-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-24-generic

## title Ubuntu 9.10, kernel 2.6.24-23-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-23-generic
## quiet

## title Ubuntu 9.10, kernel 2.6.24-23-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-23-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=a7c622fa-1fb2-41b2-bcdf-84c688494d0e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 173.5GB: boot/grub/menu.lst
 173.3GB: boot/grub/stage2
 173.4GB: boot/initrd.img-2.6.24-19-generic
 173.4GB: boot/initrd.img-2.6.24-19-generic.bak
 173.4GB: boot/initrd.img-2.6.24-21-generic
 173.4GB: boot/initrd.img-2.6.24-21-generic.bak
 173.4GB: boot/initrd.img-2.6.24-22-generic
 173.4GB: boot/initrd.img-2.6.24-22-generic.bak
 173.4GB: boot/initrd.img-2.6.24-23-generic
 173.3GB: boot/initrd.img-2.6.24-23-generic.bak
 173.5GB: boot/initrd.img-2.6.24-24-generic
 173.4GB: boot/initrd.img-2.6.24-24-generic.bak
 173.3GB: boot/initrd.img-2.6.24-25-generic
 173.4GB: boot/initrd.img-2.6.24-25-generic.bak
 173.3GB: boot/initrd.img-2.6.24-26-generic
 173.4GB: boot/initrd.img-2.6.24-26-generic.bak
 173.5GB: boot/initrd.img-2.6.24-27-generic
 173.5GB: boot/initrd.img-2.6.24-27-generic.bak
 173.5GB: boot/initrd.img-2.6.27-17-generic
 173.3GB: boot/initrd.img-2.6.28-19-generic
 173.5GB: boot/initrd.img-2.6.31-22-generic
 173.4GB: boot/vmlinuz-2.6.24-19-generic
 173.4GB: boot/vmlinuz-2.6.24-21-generic
 173.4GB: boot/vmlinuz-2.6.24-22-generic
 173.4GB: boot/vmlinuz-2.6.24-23-generic
 173.4GB: boot/vmlinuz-2.6.24-24-generic
 173.4GB: boot/vmlinuz-2.6.24-25-generic
 173.3GB: boot/vmlinuz-2.6.24-26-generic
 173.5GB: boot/vmlinuz-2.6.24-27-generic
 173.5GB: boot/vmlinuz-2.6.27-17-generic
 173.5GB: boot/vmlinuz-2.6.28-19-generic
 173.5GB: boot/vmlinuz-2.6.31-22-generic
 173.5GB: initrd.img
 173.3GB: initrd.img.old
 173.5GB: vmlinuz
 173.5GB: vmlinuz.old

```

---

### Post by Paulzy on 2011-02-09
Since I don't have GRUB multi booting either 7 or XP, and I use manual boot via F12 when the drive starts it does so as the FIRST drive, so it must be specified as such:

```
root (hd0,4)
```

---

### Post by kansasnoob on 2011-02-09
> **Paulzy said:**
> Since I don't have GRUB multi booting either 7 or XP, and I use manual boot via F12 when the drive starts it does so as the FIRST drive, so it must be specified as such:

```
root (hd0,4)
```

I don't think so. I have a real dumb question :???: Are you not able to boot even Ubuntu ATM? Or is it only XP that you can't boot?

I'm tempted to think that for your current purposes the "grub shell" method of reinstalling grub would work but I'd first want to see the output of the following before recommending any change. To use a grub shell (either from your installed Ubuntu or a **pre-9.10 Ubuntu Live CD**) just open the terminal and type:

```
sudo grub
```

Then:

```
find /boot/grub/stage1
```

And, since I don't want to make any changes just yet, just post that result here, and then exit the grub shell by typing:

```
quit
```

NOTE: I highlighted "pre-9.10 Ubuntu Live CD" because Ubuntu Live CD's from 9.10 forward have grub2 installed rather than legacy grub and therefore won't work properly for this purpose. If you have no older Ubuntu discs just say so and we'll do it a different way.

I also notice something obvious about your menu.lst. You've actually edited in the wrong place:

```
## ## End Default Options ##


title		Ubuntu 9.10 [Linux 2.6.31-22 KARMIC]
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Windows XP Home Edition SP3 [Area C]
root		(hd1,1)
savedefault
chainloader	+1

title		Windows 7 Home Premium [Area C]
root		(hd0,1)
savedefault
chainloader	+1

title		Ubuntu 9.10 RECOVERY MODE [Linux 2.6.31-22 KARMIC]
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		HP PC System Recovery (Normal / Destructive Modes) [Area D]
root		(hd1,0)
savedefault
chainloader	+1

title		Ubuntu 9.10 Linux Memory Test [memtest86+]
root		(hd3,4)
kernel		/boot/memtest86+.bin
quiet

## Old Linux Kernels ##

## title Ubuntu 9.10, kernel 2.6.27-17-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.27-17-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.27-17-generic
## quiet
 
## title Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.27-17-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.27-17-generic

## title Ubuntu 9.10, kernel 2.6.24-27-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-27-generic
## quiet

## title Ubuntu 9.10, kernel 2.6.24-27-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-27-generic

## title Ubuntu 9.10, kernel 2.6.24-26-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-26-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-26-generic
## quiet

## title Ubuntu 9.10, kernel 2.6.24-26-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-26-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-26-generic

## title Ubuntu 9.10, kernel 2.6.24-25-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-25-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-25-generic
## quiet
 
## title Ubuntu 9.10, kernel 2.6.24-25-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-25-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-25-generic

## title Ubuntu 9.10, kernel 2.6.24-24-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-24-generic
## quiet
 
## title Ubuntu 9.10, kernel 2.6.24-24-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-24-generic

## title Ubuntu 9.10, kernel 2.6.24-23-generic
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro quiet splash 
## initrd /boot/initrd.img-2.6.24-23-generic
## quiet

## title Ubuntu 9.10, kernel 2.6.24-23-generic (recovery mode)
## root (hd3,4)
## kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=b9dba18a-a184-4a50-a0f1-186e2939fd47 ro single
## initrd /boot/initrd.img-2.6.24-23-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Typically all user created entries should be done below the line:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

But we'll worry about that once I know you can boot into Ubuntu.

---

### Post by Paulzy on 2011-02-09
> **kansasnoob said:**
> I don't think so. I have a real dumb question :???: Are you not able to boot even Ubuntu ATM? Or is it only XP that you can't boot?


Actually, I can boot XP, 7, & Ubuntu 9.10 (I'm using it now) I used the **root (hd0,4)** method in the previous post.

> 
```
sudo grub
```

```
find /boot/grub/stage1
```

```
quit
```

NOTE: I highlighted "pre-9.10 Ubuntu Live CD" because Ubuntu Live CD's from 9.10 forward have grub2 installed rather than legacy grub and therefore won't work properly for this purpose. If you have no older Ubuntu discs just say so and we'll do it a different way.


I've done the code work already to update GRUB. But as you mentioned, and it did not occur to me, the reason the GRUB updates never worked was because I used the 9.10 and 10.1 Live CDs. I ditched my 8.04 Live Cd when I successfully updated to 9.10.

> 
I also notice something obvious about your menu.lst. You've actually edited in the wrong place:
..snip..

### END DEBIAN AUTOMAGIC KERNELS LIST[/CODE]
Typically all user created entries should be done below the line:
But we'll worry about that once I know you can boot into Ubuntu.

This has never been an issue with booting Ubuntu when I had it in my old box. I'll investigate for this box, *and report back _before_ I tagged this as solved.*

Thanks guys.):P

---

### Post by Paulzy on 2011-02-09
Replacing the root (hd3,4) with root (hd0,4) worked as
GRUB enumerates the USB drive as hd0. I'll have to test to see
what it enums 7 and XP as, but for this issue we can marked this as [SOLVED], please.

Thank guys.

---

### Post by oldfred on 2011-02-09
It can change depending on which drive you boot from, if you are using f12 to choose where to boot.

I have 3 drives and have added 2 USB flash drives, one for installing and another to install to. I have had to use e on the grub menu and edit hard drive number several times.

I have also chainbooted from one drive to another and normally boot sdc. But sdc then was hd0, sda was hd1 & sdb was hd2. But if I boot sda, then it is hd0, or if I boot sdb, it is hd0. So I could not copy my chainboot entries from one grub to another.

---

