---
title: "error: no such partition  grub rescue&gt;"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by fieldway on 2011-01-07
Hhi 

I'm trying install ubuntu 10.10 server but once install  (no error messages appear during this period) and rebooted it come back with

error: no such partition
grub rescue


I burn the ISO to both a rewritable CD and DVD and error message appear on both


Thanks

---

### Post by dino99 on 2011-01-07
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sikander3786 on 2011-01-07
If your hardware is capable of booting an Ubuntu Live CD (Desktop Edition), it would be really helpful to see the output of bootinfoscript.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Then we can diagnose and solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

I can guess that during installation, you install Grub to the wrong place.

---

### Post by presence1960 on 2011-01-07
> **sikander3786 said:**
> If your hardware is capable of booting an Ubuntu Live CD (Desktop Edition), it would be really helpful to see the output of bootinfoscript.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Then we can diagnose and solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

I can guess that during installation, you install Grub to the wrong place.

+1 

The output of the boot info script will display your setup & boot process info. Without that info anyone is just blindly guessing as to what the issue may be.

---

### Post by offbeat404 on 2011-03-10
> **sikander3786 said:**
> If your hardware is capable of booting an Ubuntu Live CD (Desktop Edition), it would be really helpful to see the output of bootinfoscript.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Then we can diagnose and solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated ```
 tags.

I can guess that during installation, you install Grub to the wrong place.

Hello good folks of Ubuntu Forums,
I'm having the same 'error: no such partition. grub rescue>' after trying & failing to remove Kubuntu KDE and restoring back to default Gnome. I was running 10.10 dual-boot with xp but everything started going south after trying to delete an 'unknown' partition via My Computer>Manage. Long story short, i'm stuck on the grub error screen and your help would be highly appreciated. I booted through Ubuntu live and ran the bootinfo script as requested. 

Thanks in advance.


[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   218,192,564   218,192,502   7 HPFS/NTFS
/dev/sda2         218,193,918   488,396,799   270,202,882   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5         257,168,583   448,435,599   191,267,017   7 HPFS/NTFS
Invalid MBR Signature found
/dev/sda6     ?   707,937,913   707,937,912                   Unknown
/dev/sda7     ?   707,937,913   707,937,912                   Unknown

/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2
/dev/sda7 ends after the last sector of /dev/sda
the logical partition /dev/sda7 is not contained in the extended partition /dev/sda2

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2062 MB, 2062548992 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b2267437-9df4-4d54-a75a-4da0298bcb83   ext3                                     
/dev/sda1        ECA0B8F1A0B8C2FE                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        52ECD2B6ECD29417                       ntfs       dev                           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        89CD-833C                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sda6: No such file or directory
error: /dev/sda7: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ECA0B8F1A0B8C2FE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/loop1       /media/b2267437-9df4-4d54-a75a-4da0298bcb83 ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows Server 2003, Enterprise" /noexecute=optout /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6


Unknown BootLoader  on sda7


Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....|
00000020  42 74 3d 00 58 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.X...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 3c 83 cd 89 20  20 20 20 20 20 20 20 20  |..)<...         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 b0 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
```

---

