---
title: "burg/grub doesnt find Win7"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by CBenni on 2012-03-01
Hy,

EDIT: I had a copy of the old bootloader (thankfully ^.^) I copied that into /dev/sdb2 and now burg found everything. now ill try if it boots correctly

I know a ton of People have similar problems, but every problem is just a bit different;

I had Windows 7 installed (on /dev/sdb2 for some strange reason) and /dev/sdb1 contained a windows 7 bootloader.
I decided to install Xubuntu 11.10 to /dev/sdc. After rebooting, it directly started xubuntu. 
I installed the BURG bootloader, however it doesnt find my Win7 partition... I cant mount /dev/sdb/ manually aswell, it throws the error
```
This seems not to be a root file system (no fstab found)
```when trying to mount it inside the grub customizer.

The boot info script finds Win7 with some (strange) errors:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /burg.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 35778 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800  83 Linux
/dev/sdb2             206,848   156,299,263   156,092,416   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   781,250,559   781,248,512  83 Linux
/dev/sdc2         781,252,606   781,422,591       169,986   5 Extended
/dev/sdc5         781,252,608   781,422,591       169,984  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        125210B95210A40F                       ntfs       Daten
/dev/sdb1        f8670ba8-7104-46a5-a521-68716a792abd   ext4       
/dev/sdb2        2E7486B8748681F7                       ntfs       Win7
/dev/sdc1        e1fb67d7-d9f3-4e3e-89d5-22af0dd086ee   ext4       
/dev/sdc5        dfecb00f-4af8-4cb6-95ca-47b6c4822c80   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /media/grub-customizer_recovery_root_mountpoint/dev none       (rw,bind)
/dev/sdb1        /boot                    ext4       (rw,commit=0)
/dev/sdb1        /media/grub-customizer_recovery_root_mountpoint/boot ext4       (rw)
/dev/sdc1        /media/grub-customizer_recovery_root_mountpoint ext4       (rw)
/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  f4 70 ef b5 d2 99 8d b6  ce fd da f4 65 fd e7 20  |.p..........e.. |
00000010  3e 5e 4a 10 c8 e3 0b 1c  a7 3f 0a 13 57 73 67 a6  |>^J......?..Wsg.|
00000020  49 33 33 fa 29 c2 4f f7  be ed 9f 7f 74 f8 68 35  |I33.).O.....t.h5|
00000030  1f 16 1f 35 ff 6f 11 ce  db 68 c9 a2 ff 04 92 ee  |...5.o...h......|
00000040  67 80 88 1f 54 20 e9 de  3a 6c 76 7e 23 e7 de d2  |g...T ..:lv~#...|
00000050  57 87 fd ea d5 6b 29 cc  aa c6 71 ff 4d e2 53 eb  |W....k)...q.M.S.|
00000060  17 a5 3c 7c 13 37 5c ea  5d 8f 5a 9e ab e2 f9 f9  |..<|.7\.].Z.....|
00000070  37 70 5a a5 56 c6 5f 17  12 82 f7 9c b8 d5 ba df  |7pZ.V._.........|
00000080  56 05 0d f5 bb 0d 7c b5  f9 9f f2 05 9b 45 21 0c  |V.....|......E!.|
00000090  00 00 5a 80 80 52 00 00  95 c2 00 5a b2 24 47 db  |..Z..R.....Z.$G.|
000000a0  1d db 46 db 77 e0 d2 f8  81 d0 51 77 41 10 c8 80  |..F.w.....QwA...|
000000b0  41 6e 00 fa ac 2d b0 95  b6 32 e5 b6 68 99 01 c6  |An...-...2..h...|
000000c0  f7 c2 2d 53 52 80 02 1f  f0 56 44 e6 1e fe 5e f1  |..-SR....VD...^.|
000000d0  a6 bf bf 26 f8 ee 87 2d  e3 bf b2 2b 06 e1 70 4e  |...&...-...+..pN|
000000e0  d6 fe 27 fe 6b 1a 25 9e  6b ad 42 43 20 7c fe 00  |..'.k.%.k.BC |..|
000000f0  f9 b7 86 6f 25 b8 e0 e1  4b 79 7e 6d 1e ee dc 99  |...o%...Ky~m....|
00000100  d1 72 e9 54 61 1c ac b5  ae f3 1c 9d a6 d8 57 1f  |.r.Ta.........W.|
00000110  99 87 f4 d4 e3 de 3d 40  f7 57 ae d7 37 7e fe 39  |......=@.W..7~.9|
00000120  f4 28 0c 11 f6 e3 c6 89  5f 79 78 22 c5 f5 fe d8  |.(......_yx"....|
00000130  f5 f8 5a ea 3d ff c8 4f  80 e3 a3 89 d0 7b c4 4c  |..Z.=..O.....{.L|
00000140  19 cc dd 06 96 d0 46 3b  22 da b9 bd c8 d8 cc 43  |......F;"......C|
00000150  3f cf 59 52 9c 38 5e 3a  97 66 4d 7d e7 5c 15 e7  |?.YR.8^:.fM}.\..|
00000160  f3 f4 a2 9a ee f3 b5 78  5e 7f 71 9c d7 cf b4 2c  |.......x^.q....,|
00000170  a6 e9 83 42 81 8e bf bf  5c fb 19 9f 15 3b 82 af  |...B....\....;..|
00000180  f8 d8 ad 45 fc c4 eb 37  38 4f 84 a4 f4 ff 5d 83  |...E...78O....].|
00000190  33 94 24 a9 d3 b2 5f f0  d3 9e 1e 7d 8d 1b 9f 5f  |3.$..._....}..._|
000001a0  4a d0 4a 52 db ca 4b 68  48 73 ef 66 3a c8 c5 a4  |J.JR..KhHs.f:...|
000001b0  f6 7f 20 6b 65 20 7c 2e  78 fa 47 22 ef 7d 00 fe  |.. ke |.x.G".}..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 02 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 2457: cd: /boot
/media/grub-customizer_recovery_root_mountpoint/boot/: No such file or directory
boot_info_script.sh: line 2457: cd: /
/media/grub-customizer_recovery_root_mountpoint/: No such file or directory

```I have no idea what happened here... the last time installing BURG (on my old machine) worked without problems :/

thankful for any advice (linking me to a thread that resolves may be enough, i searched for quite a long time though),
CBenni

PS: Mods, feel free to relocate this Thread :D, thx

---

### Post by oldfred on 2012-03-02
You are showing a wubi install inside your Windows in sdb2, but you have formated the sdb1 100MB partition to Linux. Windows 7 normal install is to a 100MB boot partition (active partition in Windows speak) and the main install or c:. The separate boot partition is to let you encrypt your main install as the boot files cannot be encrypted.

Windows boot partition has nothing to do with grub booting. You also installed the grub2 boot loader to the sdb1 partition. It almost always should be installed to the MBR of a drive and normally best to install to the same drive as the Ubuntu install or sdc in your case.

If you have not written anything other than the grub boot loader to the sdb1 partition in may be possible to repair with testdisk. You may be able to change back to NTFS and NTFS partitions keep a backup of the partition boot sector and can be restored. I would try that first.

You need to change sdb1 to type 07 first. See if Disk Utility will let you do that, otherwise we may need to use sdfdisk.

Then follow this to repair the PBR or partition boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

I would also install grub2 to sdc. And boot sdc drive first from BIOS. Burg is not maintained anymore and I do not know it so if you want Burg you will have to experiment yourself. 
[COLOR=DarkRed]Edit:[/COLOR]
On further review this probably will not work. You show no grub files or fstab in sdc1. At this point it may just be easier to reinstall.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc1 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc1 if not correct:
sudo fdisk -l
#confirm that linux is sdc1
sudo mount /dev/sdc1 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdc

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

