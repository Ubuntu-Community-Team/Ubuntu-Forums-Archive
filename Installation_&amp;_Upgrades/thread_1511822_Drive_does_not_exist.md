---
title: "Drive does not exist"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by dsmithnc on 2010-06-17
Yesterday, I tried to boot my desktop into Lucid and received this:

Gave up waiting for root device. Common Problems: e52f5315c2f
    -- Boot Args (cat/proc/cmdline)
       -- Check rootdelay=(did the system wait long enought?)
       -- Check root= (did the system wait for the right device?)
    -- Missing modules (cat/proc/modules; ls /dev)

ALERT! /dev/disk/by - uuid/56f07de1-e97f-471f-aa12-8e52f5315c2f does not 			exist. Dropping to shell!


BusyBox v1.13.3 (Ubunt 1:1.13.3 -1ubuntu11) built in shell (ash)
Enter 'help' for a list of commands.

(initramfs)  _

Everything worked fine the day before.

I booted from a live cd and was able to access the boot drive but somehow the grub loader isn't seeing it.

At leas the data is safe...

Any suggestions?

****

---

### Post by maferrer on 2010-06-18
Yes. I have found this bug. Can't boot by-uuid or by-label.
During boot does not exists /dev/disk/by-uuid
Only exists by-id and by-path
The udevd can't load blkid because it's not in $PATH.
The bug is from initramfs-tools (0.92j)
at end of /usr/share/initramfs-tools/hooks/udev it does:
```
copy_exec /sbin/blkid /lib/modules
```
and it should do:
```
copy_exec /sbin/blkid /sbin
```
Once it's corrected remember to:
```
update-initramfs -u
```

Good luck
__________
M.Á.Ferrer

---

### Post by dsmithnc on 2010-06-19
> **maferrer said:**
> Yes. I have found this bug. Can't boot by-uuid or by-label.
During boot does not exists /dev/disk/by-uuid
Only exists by-id and by-path
The udevd can't load blkid because it's not in $PATH.
The bug is from initramfs-tools (0.92j)
at end of /usr/share/initramfs-tools/hooks/udev it does:
```
copy_exec /sbin/blkid /lib/modules
```
and it should do:
```
copy_exec /sbin/blkid /sbin
```
Once it's corrected remember to:
```
update-initramfs -u
```

Good luck
__________
M.Á.Ferrer


Thanks for that.  I'll give it a try as soon as I can.

****

---

### Post by dsmithnc on 2010-06-19
Previous suggestion did not work.  At best, I'll simply reinstall 10.04 to a new disk.  I can still access the data.

I started the pc with the Lucid disk and then mounted sda1 and made the changes suggested to no avail.

Thanks for trying.

****

---

### Post by presence1960 on 2010-06-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by dsmithnc on 2010-06-22
> **presence1960 said:**
> Let's get a better look at your setup & boot process. 

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 


Sorry for the delay,  here is the results.txt contents:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   482,383,754   482,383,692  83 Linux
/dev/sda2         482,383,755   488,392,064     6,008,310   5 Extended
/dev/sda5         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   196,635,599   196,635,537   7 HPFS/NTFS
/dev/sdb2         196,635,600   625,137,344   428,501,745   f W95 Ext d (LBA)
/dev/sdb5         196,635,663   625,137,344   428,501,682   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240119808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   234,436,544   234,436,482   c W95 FAT32 (LBA)
/dev/sdc2         234,436,545   240,107,489     5,670,945   5 Extended
/dev/sdc5         234,436,608   237,440,699     3,004,092  83 Linux
/dev/sdc6         237,440,763   238,051,169       610,407  82 Linux swap / Solaris
/dev/sdc7         238,051,233   240,107,489     2,056,257  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        56f07de1-e97f-471f-aa12-8e52f5315c2f   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        19ec00d0-cb06-45c9-be9d-6272a60bbfcc   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8E481BEA481BCFB7                       ntfs       DRV2_VOL1                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9C041DA5041D8404                       ntfs       DRV2_VOL2                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        17EA-3758                              vfat       ONETOUCH                      
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        e2641210-baf2-4435-9954-519183a51d1c   ext3                                     
/dev/sdc6        c8673cae-2f6e-4097-84d6-32ce236e2e5e   swap                                     
/dev/sdc7        3466c584-77a7-4437-9505-571e40f5f693   ext3                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc7        /media/3466c584-77a7-4437-9505-571e40f5f693 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/ONETOUCH          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc5        /media/e2641210-baf2-4435-9954-519183a51d1c ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/DRV2_VOL1         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/DRV2_VOL2         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/menu.lst: ===========================

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
hiddenmenu

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
# kopt=root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=56f07de1-e97f-471f-aa12-8e52f5315c2f

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=19ec00d0-cb06-45c9-be9d-6272a60bbfcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   9.6GB: boot/grub/menu.lst
   9.5GB: boot/grub/stage2
   9.5GB: boot/initrd.img-2.6.28-11-generic
   9.5GB: boot/initrd.img-2.6.31-21-generic
   9.5GB: boot/initrd.img-2.6.31-22-generic
   9.5GB: boot/initrd.img-2.6.32-22-generic
   9.5GB: boot/vmlinuz-2.6.28-11-generic
   9.5GB: boot/vmlinuz-2.6.31-21-generic
   9.6GB: boot/vmlinuz-2.6.31-22-generic
   9.6GB: boot/vmlinuz-2.6.32-22-generic
   9.5GB: initrd.img
   9.5GB: initrd.img.old
   9.6GB: vmlinuz
   9.6GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


================================ sdb5/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  e9 46 44 02 00 00 80 01  |.........FD.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 91 6b b8 0b 00 00  |......?....k....|
000001d0  c1 ff 0f fe ff ff d0 6b  b8 0b f1 6a 8a 19 00 00  |.......k...j....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by presence1960 on 2010-06-26
Looks like a dist-upgrade gone awry. You should have chosen to use GRUB 2 if given the choice during the upgrade process. your menu.lst looks like a strange mix of legacy GRUB and GRUB 2. Legacy GRUB uses menu. lst and USUALLY uses this designation to refer to partitions: (hdx,y) instead of UUID. I would back up any data on Ubuntu's partition that you don't want to lose and do a clean install of Lucid.

---

