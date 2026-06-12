---
title: "Lost dual boot on 10.04"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by frugal007 on 2010-08-17
One of the updates for 10.04 has done in my ability to dual boot.
The XP option in grub has disappeared.
Grub seems to be saving a large number of older kernels.
This happened to me with 9.10, but the problem disappeared after upgrading to 10.04.
As I expect to stay with 10.04 for awhile, how do I go about recovering?

---

### Post by Rubi1200 on 2010-08-17
> **frugal007 said:**
> One of the updates for 10.04 has done in my ability to dual boot.
The XP option in grub has disappeared.
Grub seems to be saving a large number of older kernels.
This happened to me with 9.10, but the problem disappeared after upgrading to 10.04.
As I expect to stay with 10.04 for awhile, how do I go about recovering?
If you have an Ubuntu CD, please boot the computer with it, choosing the option to try rather than install.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here so we can take a look at your setup and offer solutions.

Thanks.

---

### Post by frugal007 on 2010-08-20
> **Rubi1200 said:**
> If you have an Ubuntu CD, please boot the computer with it, choosing the option to try rather than install.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here so we can take a look at your setup and offer solutions.

Thanks.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    72,469,214    72,469,152   7 HPFS/NTFS
/dev/sda2          72,469,215   156,296,384    83,827,170   5 Extended
/dev/sda5          72,469,278   152,762,084    80,292,807  83 Linux
/dev/sda6         152,762,148   156,296,384     3,534,237  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    22,539,194    22,539,132   7 HPFS/NTFS
/dev/sdb2          22,539,195   120,085,874    97,546,680   f W95 Ext d (LBA)
/dev/sdb5          22,539,258    45,062,324    22,523,067   b W95 FAT32
/dev/sdb6          45,062,388    67,585,454    22,523,067   b W95 FAT32
/dev/sdb7          67,585,518    90,108,584    22,523,067   7 HPFS/NTFS
/dev/sdb8          90,108,648   120,085,874    29,977,227   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7ACCF63CCCF5F1ED                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3e7b2575-a3fb-4423-97d4-98c09e7de814   ext3                                     
/dev/sda6        bb4e0498-7343-4a93-9947-f680804a55dd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        40B4D6D3B4D6CA94                       ntfs       Old Man                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        A0A0-207A                              vfat       MATT DRIVE                    
/dev/sdb6        B422-75BC                              vfat       JEN'S DRIVE                   
/dev/sdb7        42CC2653CC264211                       ntfs       Carolyn                       
/dev/sdb8        DE1843241842FAD3                       ntfs       Chris                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C0409CE1409CDF88                       ntfs       My Book                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
# kopt=root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3e7b2575-a3fb-4423-97d4-98c09e7de814

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-17-generic
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-17-generic (recovery mode)
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        3e7b2575-a3fb-4423-97d4-98c09e7de814
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
UUID=3e7b2575-a3fb-4423-97d4-98c09e7de814 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bb4e0498-7343-4a93-9947-f680804a55dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  59.8GB: boot/grub/menu.lst
  59.8GB: boot/grub/stage2
  59.8GB: boot/initrd.img-2.6.28-17-generic
  59.8GB: boot/initrd.img-2.6.31-21-generic
  59.8GB: boot/initrd.img-2.6.32-22-generic
  59.9GB: boot/initrd.img-2.6.32-23-generic
  59.9GB: boot/initrd.img-2.6.32-24-generic
  59.8GB: boot/vmlinuz-2.6.28-17-generic
  59.8GB: boot/vmlinuz-2.6.31-21-generic
  59.8GB: boot/vmlinuz-2.6.32-22-generic
  59.7GB: boot/vmlinuz-2.6.32-23-generic
  59.8GB: boot/vmlinuz-2.6.32-24-generic
  59.9GB: initrd.img
  59.9GB: initrd.img.old
  59.8GB: vmlinuz
  59.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  08 8c 03 9a 5f 78 76 94  8f 45 bf 49 e3 96 00 c0  |...._xv..E.I....|
00000010  88 9d dd c0 6d 36 60 df  48 5d ad f7 46 d1 32 24  |....m6`.H]..F.2$|
00000020  38 29 95 cd ad 28 d2 a2  dc 89 f3 57 d9 21 cf de  |8)...(.....W.!..|
00000030  df 8e 1f d3 30 3e 86 19  64 1e 9c 2f 95 b4 d8 36  |....0>..d../...6|
00000040  55 df 4b 4d cd 24 fb 31  e8 b8 e3 bf 0d ff 6d 43  |U.KM.$.1......mC|
00000050  32 02 64 43 b4 69 12 a7  f4 53 cc da 02 eb 60 f7  |2.dC.i...S....`.|
00000060  63 dd d0 68 1b 97 b8 2a  3b 7c c9 14 04 ef d7 44  |c..h...*;|.....D|
00000070  cd 62 b3 34 da 54 73 82  3f 5d 58 dd 14 2c ec 47  |.b.4.Ts.?]X..,.G|
00000080  ef c1 8f 10 00 8d 18 a0  e5 ed a5 98 43 9a 4b 5a  |............C.KZ|
00000090  7d 7b e1 6c 8a 84 5b cf  1a 03 26 cb 54 17 de 3a  |}{.l..[...&.T..:|
000000a0  09 8c c1 e4 ea 00 76 c9  7a 86 40 2e 59 96 56 28  |......v.z.@.Y.V(|
000000b0  9c 84 86 5a b7 62 c8 db  e2 7a e5 dc 56 31 e5 06  |...Z.b...z..V1..|
000000c0  53 ab 63 21 48 cf 70 04  18 2d 2c 64 df 5a c9 7a  |S.c!H.p..-,d.Z.z|
000000d0  09 1c 07 14 58 44 fb 19  73 57 04 f4 b6 ea f8 08  |....XD..sW......|
000000e0  f1 f0 3e ba 9e c4 ef df  69 30 c2 6f 70 49 bc 3f  |..>.....i0.opI.?|
000000f0  2f 4c 90 5d 71 67 7f 28  3b 9d c7 9a 14 94 53 ca  |/L.]qg.(;.....S.|
00000100  8a 95 e1 3c 6d 8c 1f 03  97 43 20 2e b8 af 91 95  |...<m....C .....|
00000110  fd 81 10 9b 09 ee 2a cd  2d b5 2c 01 1f 6f 7e f6  |......*.-.,..o~.|
00000120  57 3f a0 e8 44 c3 7d 50  5a 84 31 25 63 bb f5 bd  |W?..D.}PZ.1%c...|
00000130  ea 93 46 dd 34 e4 18 f3  c3 6f 04 03 8a a2 45 63  |..F.4....o....Ec|
00000140  13 fa 9c 9e b9 e7 c6 c4  f2 77 a7 83 2a 87 d6 21  |.........w..*..!|
00000150  f7 c2 b3 da 0a 3d ae ad  fe 05 e5 22 0d 3a bf 12  |.....=.....".:..|
00000160  03 34 bb eb 67 5e 01 85  21 09 f9 1c ce 17 6f 55  |.4..g^..!.....oU|
00000170  ab b2 a1 f4 ac d9 95 38  67 18 26 86 70 2d 49 29  |.......8g.&.p-I)|
00000180  f4 cf ad 00 f7 7c 80 e7  3a 90 65 6f 11 56 43 12  |.....|..:.eo.VC.|
00000190  19 75 22 2e 43 77 c2 fd  13 b3 f3 00 7c 5a 89 f8  |.u".Cw......|Z..|
000001a0  36 07 e7 be 11 77 db 5f  11 c9 fb a1 c9 13 1a 3d  |6....w._.......=|
000001b0  da 81 14 3d 00 c7 70 83  9d 42 33 0c 02 87 00 01  |...=..p..B3.....|
000001c0  c1 ff 0b fe ff ff 3f 00  00 00 bb ac 57 01 00 00  |......?.....W...|
000001d0  c1 ff 05 fe ff ff fa ac  57 01 fa ac 57 01 00 00  |........W...W...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

```

---

### Post by frugal007 on 2010-08-20
Since using the "Try it" mode from CD, The system will no longer boot into 10.04.
It get as far as "UBUNTU" with 5 red dot below it and then freezes.
Twenty minute wait produces nothing.
Only responds to Ctrl-Alt-Del.

What's my next move?
Thanks.

---

### Post by oldfred on 2010-08-20
I have seen where the "box" that grub presents does not show all the entries but your have to scroll down to see them as they really are still there.

With old grub you can limit the number of kernels shown, change the [COLOR=Red]all[/COLOR] to 2. The entry with only one # will be used on the next update of grub.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]all[/COLOR]

Then run 
sudo update-grub

You can also set many of the parameters with 
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by oldfred on 2010-08-20
Have you tried booting with recovery mode?
or
At grub menu use e for edit and remove splash quiet and you will see all the detail of the boot process. Do the last entries give an clues to something wrong.

---

### Post by kansasnoob on 2010-08-20
[B][COLOR="Red"]Oops, never mind. I wasn't paying attention.
[/COLOR][/B]
> **frugal007 said:**
> One of the updates for 10.04 has done in my ability to dual boot.
The XP option in grub has disappeared.
Grub seems to be saving a large number of older kernels.
This happened to me with 9.10, but the problem disappeared after upgrading to 10.04.
As I expect to stay with 10.04 for awhile, how do I go about recovering?

The long list of kernels may have simply "pushed" XP out of the visible range of the boot menu ;)

Try using the "down" arrow button and see if it's still not there. If so we need to know what version of grub you have to tell you how to clean up some of the old kernels, to see grub version run:

```
grub-install -v
```

---

