---
title: "Lost Windows boot option"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by mike1122 on 2011-12-03
Hi, new user here.. I have just installed v9.04 ubuntu from the alternate cd, and was aiming to have the dual boot option, but when I boot up, I only see ubuntu related options.  I have a fakeraid setup.  Maybe someone can take a shot at deciphering my bootscript results, or point me in the right direction?  All I can tell from the script is that there is no mount point for windows.  Thanks!!

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Grub Legacy (v0.97) is installed in the MBR of 
    /dev/mapper/isw_beecfgafad_RAID0 and looks on the same drive in partition 
    #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_beecfgafad_RAID01: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

isw_beecfgafad_RAID02: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

isw_beecfgafad_RAID03: _________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_beecfgafad_RAID05: _________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

isw_beecfgafad_RAID06: _________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,188,253,470 1,188,253,408   7 NTFS / exFAT / HPFS
/dev/sda2       1,229,213,475 1,250,274,689    21,061,215   7 NTFS / exFAT / HPFS
/dev/sda3       1,188,263,790 1,229,213,474    40,949,685   5 Extended
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00310030

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sdb1     ?     4,391,004    11,534,538     7,143,535  62 Unknown
/dev/sdb2     ?     7,602,286    13,959,347     6,357,062  6e Unknown
/dev/sdb3     ?     7,536,741    15,401,152     7,864,412  6c Unknown
/dev/sdb4     ?     6,488,169    13,762,778     7,274,610  5f Unknown

/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb1 overlaps with /dev/sdb4
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 overlaps with /dev/sdb4

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,751,999   976,751,937   c W95 FAT32 (LBA)


Drive: isw_beecfgafad_RAID0 _____________________________________________________________________

Disk /dev/mapper/isw_beecfgafad_RAID0: 640.1 GB, 640141230080 bytes
255 heads, 63 sectors/track, 77826 cylinders, total 1250275840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_beecfgafad_RAID01                 63 1,188,253,470 1,188,253,408   7 NTFS / exFAT / HPFS
/dev/mapper/isw_beecfgafad_RAID02      1,229,213,475 1,250,274,689    21,061,215   7 NTFS / exFAT / HPFS
/dev/mapper/isw_beecfgafad_RAID03      1,188,263,790 1,229,213,474    40,949,685   5 Extended
/dev/mapper/isw_beecfgafad_RAID05      1,188,263,853 1,227,414,194    39,150,342  83 Linux
/dev/mapper/isw_beecfgafad_RAID06      1,227,414,258 1,229,213,474     1,799,217  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_beecfgafad_RAID01 CECCB449CCB42E19                       ntfs       HP
/dev/mapper/isw_beecfgafad_RAID02 949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/mapper/isw_beecfgafad_RAID05 cf622aec-64f7-4684-ba39-107425a6f2c3   ext3       
/dev/mapper/isw_beecfgafad_RAID06 d3c38cad-d180-4140-bbea-ce2011ea94cc   swap       
/dev/sdc1        843E-AA9E                              vfat       My Book

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_beecfgafad_RAID0
isw_beecfgafad_RAID01
isw_beecfgafad_RAID02
isw_beecfgafad_RAID05
isw_beecfgafad_RAID06

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/isw_beecfgafad_RAID05 /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdc1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================== isw_beecfgafad_RAID05/boot/grub/menu.lst: ===================

--------------------------------------------------------------------------------
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
# kopt=root=/dev/mapper/isw_beecfgafad_RAID05 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_beecfgafad_RAID05 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_beecfgafad_RAID05 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

======================= isw_beecfgafad_RAID05/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/isw_beecfgafad_RAID05 during installation
UUID=cf622aec-64f7-4684-ba39-107425a6f2c3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/isw_beecfgafad_RAID06 during installation
UUID=d3c38cad-d180-4140-bbea-ce2011ea94cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========== isw_beecfgafad_RAID05: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.28-11-generic
            ?? = ??             boot/vmlinuz-2.6.28-11-generic
            ?? = ??             initrd.img
            ?? = ??             vmlinuz

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  30 42 3b 00 30 42 3b 00  00 00 00 00 00 00 00 00  |0B;.0B;.........|
00000010  40 42 3b 00 40 42 3b 00  00 00 00 00 00 00 00 00  |@B;.@B;.........|
00000020  6c 00 69 00 08 21 70 01  00 00 00 00 00 00 00 00  |l.i..!p.........|
00000030  00 00 00 00 6e 00 3d 00  00 00 00 00 00 00 00 00  |....n.=.........|
00000040  00 00 00 00 05 00 00 00  23 00 00 00 7c 42 3b 00  |........#...|B;.|
00000050  7c 42 3b 00 00 00 00 00  00 00 00 00 8c 42 3b 00  ||B;..........B;.|
00000060  8c 42 3b 00 00 00 00 00  00 00 00 00 9c 42 3b 00  |.B;..........B;.|
00000070  9c 42 3b 00 00 00 00 00  00 00 00 00 ac 42 3b 00  |.B;..........B;.|
00000080  ac 42 3b 00 00 00 00 00  00 00 00 00 bc 42 3b 00  |.B;..........B;.|
00000090  bc 42 3b 00 00 00 00 00  00 00 00 00 cc 42 3b 00  |.B;..........B;.|
000000a0  cc 42 3b 00 00 00 00 00  00 00 00 00 dc 42 3b 00  |.B;..........B;.|
000000b0  dc 42 3b 00 00 00 00 00  00 00 00 00 aa 12 00 00  |.B;.............|
000000c0  01 06 00 00 00 00 00 05  50 00 00 00 b5 89 fb 38  |........P......8|
000000d0  19 84 c2 cb 5c 6c 23 6d  57 00 77 6e c0 02 64 87  |....\l#mW.wn..d.|
000000e0  01 06 00 00 00 00 00 05  50 00 00 00 b5 89 fb 38  |........P......8|
000000f0  19 84 c2 cb 5c 6c 23 6d  57 00 77 6e c0 02 64 87  |....\l#mW.wn..d.|
00000100  d8 46 7a 3a 99 02 00 00  00 63 01 00 00 00 00 00  |.Fz:.....c......|
00000110  b0 01 00 00 01 00 04 94  5c 01 00 00 7c 01 00 00  |........\...|...|
00000120  00 00 00 00 14 00 00 00  02 00 48 01 04 00 00 00  |..........H.....|
00000130  00 00 28 00 ff 01 1f 00  01 06 00 00 00 00 00 05  |..(.............|
00000140  50 00 00 00 b5 89 fb 38  19 84 c2 cb 5c 6c 23 6d  |P......8....\l#m|
00000150  57 00 77 6e c0 02 64 87  00 00 14 00 a9 00 12 00  |W.wn..d.........|
00000160  01 01 00 00 00 00 00 05  12 00 00 00 00 00 18 00  |................|
00000170  a9 00 12 00 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000180  20 02 00 00 00 00 18 00  a9 00 12 00 01 02 00 00  | ...............|
00000190  00 00 00 05 20 00 00 00  21 02 00 00 30 00 2e 00  |.... ...!...0...|
000001a0  36 00 30 00 30 00 31 00  2e 00 31 00 38 00 30 00  |6.0.0.1...1.8.0.|
000001b0  30 00 30 00 5f 00 30 00  30 00 31 00 63 00 35 00  |0.0._.0.0.1.c.5.|
000001c0  30 00 62 00 35 00 5c 00  43 00 6f 00 6d 00 70 00  |0.b.5.\.C.o.m.p.|
000001d0  6f 00 6e 00 65 00 6e 00  74 00 46 00 61 00 6d 00  |o.n.e.n.t.F.a.m.|
000001e0  69 00 6c 00 69 00 65 00  73 00 5c 00 78 00 38 00  |i.l.i.e.s.\.x.8.|
000001f0  36 00 5f 00 6d 00 69 00  63 00 72 00 6f 00 73 00  |6._.m.i.c.r.o.s.|
00000200

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on sdb3


Unknown BootLoader on sdb4


Unknown BootLoader on sdc1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.Z.MSWIN4.1..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  41 0d 38 3a b2 d1 01 00  00 00 00 00 02 00 00 00  |A.8:............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9e aa 3e 84 4d  79 20 42 6f 6f 6b 20 20  |..)..>.My Book  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown BootLoader on isw_beecfgafad_RAID03



========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/mapper/isw_beecfgafad_RAID03: No such file or directory
hexdump: /dev/mapper/isw_beecfgafad_RAID03: No such file or directory
```

---

### Post by bluexrider on 2011-12-03
there are cautions about Fakeraid here [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

dual boot windows 7 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by darkod on 2011-12-03
Did you use any of the auto methods to install or you partitioned yourself manually during the install?
Or maybe in advance from windows?

Anyway, the disks are a mess. Look at the invalid MBR messages for both sda and sdb.

---

### Post by mike1122 on 2011-12-03
Oh man, does this mean my windows is toast?  Ok, first I set aside a 20gb partition using vista disk mgmt tool, and then while installing ubuntu, I chose automatic configuring/partitioning of that same 20gb piece, and I believe it created an ext4 and a swap.  At least I have things backed up.  thanks

---

### Post by darkod on 2011-12-03
It doesn't have to mean that it's toast. Partition table/MBR errors can be repaired. But that's beyond my expertise especially not even looking at the computer so I can't give you any solid advice. On top of that running a RAID0 might make it more complicated than without it.

---

### Post by mike1122 on 2011-12-05
Ok, good news, all appears to be working now.  The partition issue is probably still present but it doesn't seem to be limiting the OSs.  Upgraded to v10.04 (alternate of course), received an option to repair windows, did fixboot & fixmbr cmds, installed easybcd.  Now have a fine working dual boot installed on a RAID0 fakeraid, did not lose any files except for the windows mbr as mentioned, which I probably could've avoided to begin with by not overwriting it with grub during the initial 9.04 installation.  Only took me 2 weeks! Thanks for all the help.

---

