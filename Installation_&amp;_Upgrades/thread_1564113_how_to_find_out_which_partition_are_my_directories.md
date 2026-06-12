---
title: "how to find out which partition are my directories"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2010-08-30
```


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        5099    20474842+   7  HPFS/NTFS
/dev/sda3            5100       38913   271610955    f  W95 Ext'd (LBA)
/dev/sda5            5100       15298    81923436    7  HPFS/NTFS
/dev/sda6           15299       15541     1951866   83  Linux
/dev/sda7           15542       15784     1951866   82  Linux swap / Solaris
/dev/sda8           15785       21256    43953808+  83  Linux
/dev/sda9           21583       26771    41680611   83  Linux
/dev/sda10          26772       31370    36933435    7  HPFS/NTFS
/dev/sda11          31632       34242    20972826    b  W95 FAT32
/dev/sda12          34243       34836     4763272    b  W95 FAT32
/dev/sda13          34837       38739    31350816   83  Linux
/dev/sda14          38740       38913     1397623+  82  Linux swap / Solaris

```
I  want to install Ubuntu 64 bit on one of the partitions above but at the same time I want to keep the existing files of existing 32 bit Ubuntu  installation intact.
How do I find out on which partition is holds which directory.
In past I had used OpenSuse had deleted then installed Ubuntu  ,Windows then Debian then formatted some unclean unformatted partitions are there. 


My problem is my partition table.

How do I identify which folder is from a previous linux installation is there some way I can merge the 
unused space into one and then install 64 bit Ubuntu so that I have a triple boot system.
I had checked this link [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

I want to also have windows drive as in above partition table.
Since I have got all my data and I do not want to mess up with that.
I am seeing from GUI a folder lost+found worth 42.7 Gb
this much space is getting wasted I am not too sure as if this is the space getting wasted from the current running Ubuntu installation or any of the above previous Linux which I forgot to cleanly delete.
How can I proceed in a convenient way for this problem?

---

### Post by presence1960 on 2010-08-30
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by jamesbon on 2010-08-30
Here is the result you requested
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #13 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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
    Boot files/dirs:   /boot.ini

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda10 has 72135600 sectors, but according to 
                       the info from fdisk, it has 73866869 sectors.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   c W95 FAT32 (LBA)
/dev/sda2          40,965,750    81,915,434    40,949,685   7 HPFS/NTFS
/dev/sda3          81,915,435   625,137,344   543,221,910   f W95 Ext d (LBA)
/dev/sda5          81,915,498   245,762,369   163,846,872   7 HPFS/NTFS
/dev/sda6         245,762,433   249,666,164     3,903,732  83 Linux
/dev/sda7         249,666,228   253,569,959     3,903,732  82 Linux swap / Solaris
/dev/sda8         253,570,023   341,477,639    87,907,617  83 Linux
/dev/sda9         346,714,893   430,076,114    83,361,222  83 Linux
/dev/sda10        430,076,178   503,943,047    73,866,870   7 HPFS/NTFS
/dev/sda11        508,152,078   550,097,729    41,945,652   b W95 FAT32
/dev/sda12        550,097,793   559,624,336     9,526,544   b W95 FAT32
/dev/sda13        559,640,403   622,342,034    62,701,632  83 Linux
/dev/sda14        622,342,098   625,137,344     2,795,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       8E78438F784374CD                       ntfs                                     
/dev/sda11       F09C-8B5C                              vfat                                     
/dev/sda12       90A9-8462                              vfat                                     
/dev/sda13       1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1   ext3                                     
/dev/sda14       1414ee34-775a-4ca6-a196-5e23b09f07a8   swap                                     
/dev/sda1        90A8-5C76                              vfat                                     
/dev/sda2        3838B25B38B217B8                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7AC03B13C03AD4DB                       ntfs                                     
/dev/sda6        5c5c98f4-ff1d-4750-b3fb-d290bf60c48b   ext2                                     
/dev/sda7                                               swap                                     
/dev/sda8        9729e304-0db5-4915-9dc6-d9fd16ce5856   ext2                                     
/dev/sda9        a20a4466-24bc-42c5-93e2-2193e99847b5   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda11       /media/F09C-8B5C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda13       /media/1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1 ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /Execute /fastdetect 

================================ sda5/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /Execute /fastdetect 

========================== sda13/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1
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


=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda13 during installation
UUID=1c1bc84c-9ef5-4daa-a630-8fe29b5d12d1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda14 during installation
UUID=1414ee34-775a-4ca6-a196-5e23b09f07a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda13: Location of files loaded by Grub: ===================


 293.2GB: boot/grub/menu.lst
 293.2GB: boot/grub/stage2
 293.3GB: boot/initrd.img-2.6.28-11-generic
 293.3GB: boot/vmlinuz-2.6.28-11-generic
 293.3GB: initrd.img
 293.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda9

00000000  ff eb ff c9 82 bd 8f e5  ce ce 7f b0 05 37 81 cb  |.............7..|
00000010  65 df 7f f9 f7 b9 f3 b4  ef 65 1f 8f 1e 2b 7e 3d  |e........e...+~=|
00000020  91 b7 63 0c b7 7e a7 7b  d6 94 3a 97 5d 09 c4 42  |..c..~.{..:.]..B|
00000030  76 c3 b9 78 ce 63 5f 16  06 63 44 84 73 6e 9c 94  |v..x.c_..cD.sn..|
00000040  ad b3 b4 90 0f e7 bf 83  8f 8e 18 40 5c c3 b8 75  |...........@\..u|
00000050  9e 53 b3 84 d0 43 b8 2c  31 a4 f5 63 fd b9 52 ac  |.S...C.,1..c..R.|
00000060  02 c6 5e 0e 40 df 00 b5  2c fd 5f 8b b8 b0 00 00  |..^.@...,._.....|
00000070  91 b7 64 0c 37 a4 f5 bd  62 60 4f 73 72 8e 41 e8  |..d.7...b`Osr.A.|
00000080  01 c3 03 6f ec 2f f3 cf  e4 5c d2 f7 ff 94 73 4b  |...o./...\....sK|
00000090  35 ab a6 0a 54 e7 15 75  25 ee 07 18 71 0f 03 ef  |5...T..u%...q...|
000000a0  eb ef f3 4f e5 35 8f b7  fc a2 89 c8 fc af a2 5f  |...O.5........._|
000000b0  b0 2f e4 91 9f 81 fd 2e  57 d8 9a 61 52 52 ae ef  |./......W..aRR..|
000000c0  91 b7 65 0c 45 21 92 e7  04 e9 58 a8 01 22 06 01  |..e.E!....X.."..|
000000d0  c5 fe 44 a1 93 68 24 5d  92 c4 52 1c 35 91 c5 d8  |..D..h$]..R.5...|
000000e0  39 28 7f 23 7f 42 4c 02  7f aa c5 86 18 4a 3e af  |9(.#.BL......J>.|
000000f0  5f b1 ed 77 35 e1 ed 7f  1c f5 7f 8d fc a4 aa b6  |_..w5...........|
00000100  13 07 54 38 e0 d3 f2 2d  7d 3e 33 06 ff 1c 5f 02  |..T8...-}>3..._.|
00000110  91 b7 66 0c 26 a8 c6 00  bc d8 b3 80 2f 01 22 41  |..f.&......./."A|
00000120  7e 91 29 28 c3 64 a3 90  bc 91 aa 6b e0 d2 41 3e  |~.)(.d.....k..A>|
00000130  22 2e b8 5d 97 09 15 a9  ce 22 21 29 e1 29 29 2b  |"..]....."!).))+|
00000140  cc 0d 31 54 91 d0 79 a4  e8 e3 c0 da fa 26 bc 0c  |..1T..y......&..|
00000150  4c 00 19 b8 c3 3c f8 26  54 93 cb 04 14 75 00 b3  |L....<.&T....u..|
00000160  91 b7 67 0c 6e 23 d4 80  e4 22 7d 90 35 83 00 0f  |..g.n#..."}.5...|
00000170  7e 01 6d 28 66 a3 94 d1  32 fd 27 f1 82 da fa 07  |~.m(f...2.'.....|
00000180  6c a5 50 c4 8d 43 47 2f  92 c5 34 80 f0 1e 6d 23  |l.P..CG/..4...m#|
00000190  30 1b f4 59 47 12 91 b7  ad 74 ac ab 18 ad 79 e8  |0..YG....t....y.|
000001a0  f1 98 0f 84 e5 6a e0 26  c4 9d 25 08 c0 00 00 00  |.....j.&..%.....|
000001b0  91 b7 68 0c b6 2e bf f1  dc 48 30 a1 01 79 50 41  |..h......H0..yPA|
000001c0  a0 f0 bd af 9b 19 c5 62  8b ae 48 0f 0a 3c 5a e9  |.......b..H..<Z.|
000001d0  c7 a5 df 2a e0 4a d0 79  66 8e 03 bc 5a 0b c6 ab  |...*.J.yf...Z...|
000001e0  33 a2 2b c8 ac 3a 92 fe  36 07 71 b4 f8 a9 6e 24  |3.+..:..6.q...n$|
000001f0  9a 50 cd b4 c0 00 06 a5  cf 5b 00 00 00 00 00 09  |.P.......[......|
00000200


```An already mounted device could be mounted.
I mounted each partition on /tmp and unmounted.

Finally it appears sda13 from above list is what my current active linux is.
I am not clear as how could I mount an active Linux partition (not from Live CD)
already installed Linux (32 bit) Ubuntu 9.04.

I did 

```

ls /dev/disk/by-uuid

```but which one is which?
I mean /dev/sda1 etc type.

---

### Post by jamesbon on 2010-09-03
Ok I have got it.sda 6 sda7 and sda 8 is what I have used.
Also while installing 10.04 the grub2 took care of an existing installation and has updted the grub entries automatically.Which I used to do manually previously with other linux systems.
Thanks for the help.

---

