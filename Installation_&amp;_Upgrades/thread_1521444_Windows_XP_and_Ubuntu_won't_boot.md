---
title: "Windows XP and Ubuntu won't boot"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by HDSaint on 2010-06-30
Hello, I'm hoping someone here can help me with a problem that I'm having. I downloaded Ubuntu 10.04 and installed it to a USB drive to try it out. I liked the way that it worked and noticed that it could be dual installed with Windows. I decided to install it. I ran the install from the USB and when it got to the part about partitioning I had the Ubuntu installer create a separate partition of 50GB on my main drive which had Windows XP installed on already. 

It finished installing and went to restart and what I thought was suppose to happen was that I would get a screen to choose what OS to boot to. This didn't happen it went to boot Windows and then did a CHKDSK on the main drive then Windows booted up.  I tried restarting and it booted to Windows. I checked the disk and it did show the drive had a separate partition of 50GB.  

I booted Ubuntu from my USB and was going to try to see if I could figure anything out but then had to reboot into Windows since I had some stuff to work on. Unfortunately when I restarted the windows screen would show and then would ask if I wanted to boot into safe mode(s) or start normally. I tried the normal, but it just restarted. I then tried safe mode and it would restart and so now I can't boot to Windows either. 

I tried looking at previous posts but couldn't find anything similar, if there is please point me in that direction. I did read lots of posts though that recommended to post the boot info script so have posted that below.

Sorry for the long post, I'm a noob at this stuff so wanted to make sure I gave as much information as I could. Please let me know if there is more info needed and thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   781,417,664   781,417,602  42 SFS


Drive: sdd ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   293,025,615   293,025,553   7 HPFS/NTFS
/dev/sdd2         293,025,790   390,721,535    97,695,746   5 Extended
Extended  partition  linking to another extended partition
Extended  partition  linking to another extended partition
Invalid MBR Signature found
/dev/sdd5     ? 2,358,139,710 2,358,139,709                   Unknown
/dev/sdd6     ? 2,358,139,710 2,358,139,709                   Unknown

/dev/sdd5 ends after the last sector of /dev/sdd
the logical partition /dev/sdd5 is not contained in the extended partition /dev/sdd2
/dev/sdd6 ends after the last sector of /dev/sdd
the logical partition /dev/sdd6 is not contained in the extended partition /dev/sdd2

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62     3,945,059     3,944,998   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       5dba9e60-993d-4743-ab12-9caa3203ca9a   ext3                                     
/dev/sda1        36F04F78F04F3D7D                       ntfs       SATA_DRIVE                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C22042A82042A371                       ntfs       USB_BACKUP                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        04D06F15D06F0C6C                       ntfs       BACKUP                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        A6B8BC44B8BC1531                       ntfs                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd: PTTYPE="dos" 
/dev/sde1        26BB-55EC                              vfat                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd5: No such file or directory
error: /dev/sdd6: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/A6B8BC44B8BC1531  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/SATA_DRIVE        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/loop1       /media/5dba9e60-993d-4743-ab12-9caa3203ca9a ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/VX2PFPP_EN        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sdd1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd2

00000000  4b d0 f1 71 33 4a ac 5b  37 2c b5 15 96 47 94 94  |K..q3J.[7,...G..|
00000010  55 f2 df 03 f0 e3 f5 ac  2f 0b cf 24 7a 9b 40 41  |U......./..$z.@A|
00000020  66 9f 3b 31 dd bd 33 d3  9a de a4 ad 16 bd 0c 69  |f.;1..3........i|
00000030  5e 52 8f cc fa df 04 00  00 cf 15 18 c6 7d eb e0  |^R...........}..|
00000040  75 4c fa c7 b8 99 19 e2  9a d9 07 a7 07 34 49 58  |uL...........4IX|
00000050  16 e0 0e 4e 3a 0a 72 81  9f a5 4a b3 d4 7b 0e ef  |...N:.r...J..{..|
00000060  df 9a 5d c3 b9 ef de aa  c2 23 de 37 1a 01 24 f5  |..]......#.7..$.|
00000070  e4 9e e6 8b f4 63 b0 b9  20 f1 eb d6 82 78 c7 04  |.....c.. ....x..|
00000080  77 a7 e4 2b 0d 18 e8 3a  52 16 1d 38 e7 a5 4b 63  |w..+...:R..8..Kc|
00000090  23 62 6a b5 cc 6b 24 12  c6 79 0f 13 a9 c7 b8 34  |#bj..k$..y.....4|
000000a0  43 75 de e8 25 b1 f9 2d  7f 61 24 13 cd 03 ae 0a  |Cu..%..-.a$.....|
000000b0  48 d8 1e d9 35 9e cb b1  94 8e 4e e2 0d 7d 35 3d  |H...5.....N..}5=|
000000c0  62 ad d8 e3 e6 b3 3b 9f  0f 78 c6 5b 08 bc 99 37  |b.....;..x.[...7|
000000d0  18 b7 12 08 ea 33 da bd  47 40 f1 14 7a 9c 8b 05  |.....3..G@..z...|
000000e0  bb 29 66 04 90 7b 56 33  a2 db d1 2b 1b 29 a7 ea  |.)f..{V3...+.)..|
000000f0  7a ce 9f 60 96 e9 8e 0b  31 e4 d6 89 62 0e 39 e4  |z..`....1...b.9.|
00000100  56 2e 3c b6 ec 45 ee d9  13 39 2b eb 9a 60 39 e0  |V.<..E...9+..`9.|
00000110  9e b4 d4 9e a2 1f 9e 73  90 05 46 ae 3a 83 90 46  |.......s..F.:..F|
00000120  68 5b 7c c3 72 55 c1 e9  ce 05 22 31 0d 81 eb f9  |h[|.rU...."1....|
00000130  56 f1 92 42 b1 71 0e 32  78 c7 4c 8a 90 30 23 9e  |V..B.q.2x.L..0#.|
00000140  07 b5 74 ed a9 9b 25 e7  1c 7a 54 4d d3 9e bc f4  |..t...%..zTM....|
00000150  ad 14 6e 66 ec 55 53 86  60 58 f2 46 0e 3d ab 85  |..nf.US.`X.F.=..|
00000160  f8 8a ab fd 94 ad 8c 95  b8 42 4e 3a 70 45 6c 95  |.........BN:pEl.|
00000170  8c 67 b9 e1 cc 0e 77 75  00 d3 09 eb d4 66 9a 8d  |.g....wu.....f..|
00000180  ef a9 0d 8d 3f 2e 70 00  c9 c8 fc aa 95 c9 2b 19  |....?.p.......+.|
00000190  72 71 f2 91 d6 b2 a8 b4  35 8b 47 97 1c 31 f7 27  |rq......5.G..1.'|
000001a0  9a 40 87 18 23 ad 66 6e  7a ba 7c 34 97 cc f2 5a  |.@..#.fnz.|4...Z|
000001b0  44 59 4d 90 b9 23 70 c8  5f 2f 76 4f a7 15 00 fe  |DYM..#p._/vO....|
000001c0  ff ff 05 fe ff ff c3 5f  94 05 3f 58 3e 00 00 00  |......._..?X>...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd5


Unknown BootLoader  on sdd6



=============================== StdErr Messages: ===============================

hexdump: /dev/sdd5: No such file or directory
hexdump: /dev/sdd5: No such file or directory
hexdump: /dev/sdd6: No such file or directory
hexdump: /dev/sdd6: No such file or directory
```

---

### Post by darkod on 2010-07-01
Drive: sdd ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   293,025,615   293,025,553   7 HPFS/NTFS
/dev/sdd2         293,025,790   390,721,535    97,695,746   5 Extended
Extended  partition  linking to another extended partition
Extended  partition  linking to another extended partition
Invalid MBR Signature found
/dev/sdd5     ? 2,358,139,710 2,358,139,709                   Unknown
/dev/sdd6     ? 2,358,139,710 2,358,139,709                   Unknown

/dev/sdd5 ends after the last sector of /dev/sdd
[COLOR=Red]the logical partition /dev/sdd5 is not contained in the extended partition /dev/sdd2[/COLOR]
/dev/sdd6 ends after the last sector of /dev/sdd
[COLOR=Red]the logical partition /dev/sdd6 is not contained in the extended partition /dev/sdd2
[/COLOR]
I don't know how it happened but the ubuntu partitions are all messed up. Since this was a new install it might be easier just to open Gparted from live mode and delete the sdd5, sdd6 and sdd2 partitions (if it allows you to do that). Hit the green button in Gparted to execute the changes.

After that it should leave the 50GB space as unallocated. Just install again using the Use Largest Available Free space or manual partitioning.

With so many disks you also need to be careful where you put the bootloader and which disk you are booting from. Look at the top of the results, grub2 went to sda and it's best to be on the same disk as ubuntu, in other words sdd. You control this with the Advanced button in the last screen of the installer.

---

