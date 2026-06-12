---
title: "Messed up partitions with Gparted and TestDisk utility"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by patelsagar on 2011-02-01
Hello guys :)
I have managed to mess up my partitions. I will post screen shots that will show how they look like. But before that, let me give some idea about what I did:

I had 3 OSs on my hard disk, windows xp, windows 7 and Ubuntu 10.10. As the time went, I needed more space for Ubuntu, and hence decided to increase ext4 file system from around 7 GB to 15 GB. For that I did make enough space by deleting files. Then for a valid reason, I wanted to format whole ext4 partition. I did it, but Grub also got deleted :(

So, it started showing "Grub rescue>" on the screen, nothing more.

I tried to understand how to recover it, but wasn't able to do that. Then I inserted MBR into C drive using TestDisk utility from Gparted. I got rid of broken grub, but then windows also wasn't booting up, saying I need to repair it using windows disk. Also, in process I messed up partitions by writing new partition table (this is the main reason my partitions are messed up I believe).

I don't have a disk though, only ISO images. I think I can make my USB bootable and install Windows 7 using the iso file. 

Now my question is: Will windows 7 setup repair my partitions? Will it do so at the expense of my data? (yes I can see all my data using Ubuntu on USB). Please guide. See the attachments for some insight (and for some laughs too lol).

[http://www.flickr.com/photos/24730323@N07/5407494387/](http://www.flickr.com/photos/24730323@N07/5407494387/)
[http://www.flickr.com/photos/24730323@N07/5407494391/](http://www.flickr.com/photos/24730323@N07/5407494391/)
[http://www.flickr.com/photos/24730323@N07/5407494393/](http://www.flickr.com/photos/24730323@N07/5407494393/)
[http://www.flickr.com/photos/24730323@N07/5407494399/](http://www.flickr.com/photos/24730323@N07/5407494399/)
[http://www.flickr.com/photos/24730323@N07/5407494403/](http://www.flickr.com/photos/24730323@N07/5407494403/)
[http://www.flickr.com/photos/24730323@N07/5407494411/](http://www.flickr.com/photos/24730323@N07/5407494411/)
[http://www.flickr.com/photos/24730323@N07/5407497935/](http://www.flickr.com/photos/24730323@N07/5407497935/)
[http://www.flickr.com/photos/24730323@N07/5407497939/](http://www.flickr.com/photos/24730323@N07/5407497939/)

Thanks for reading :) Let me know if I have done something wrong while posting this.

Note: I haven't installed Ubuntu on HDD because I fear that I may lose some of the data by doing so. I am running Ubuntu on my USB. And oh, the most important thing: I am almost a noob at linux :lolflag:

---

### Post by kansasnoob on 2011-02-01
> in process I messed up partitions by writing new partition table 

Ouch! If you're real lucky you might be able to recover the previous partition table using TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by patelsagar on 2011-02-01
> **kansasnoob said:**
> Ouch! If you're real lucky you might be able to recover the previous partition table using TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Hi, thanks for the reply :)

Though, I am very scared to deal with partitions now! Let me know if using testdisk (or anything similar) is the only way to go.

I have just run boot info script and here are the results (quite funny results) :
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda7 has 66833720 sectors, but according to 
                       the info from fdisk, it has 66846401 sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,592,769   230,677,335   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372   7 HPFS/NTFS
/dev/sda6         163,830,933   245,746,304    81,915,372   7 HPFS/NTFS
/dev/sda7         245,746,368   312,592,769    66,846,402   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda7 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1017 MB, 1017117696 bytes
33 heads, 63 sectors/track, 955 cylinders, total 1986558 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     1,986,557     1,986,526   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4023 MB, 4023385600 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7858175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76440CA1440C65E9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        CE585B43585B298B                       ntfs       Local Disk                    
/dev/sda6        78C8963DC895F998                       ntfs                                     
/dev/sda7        7030538B305356E6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1072-EAF7                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        04B8-C5D4                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/78C8963DC895F998  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/76440CA1440C65E9  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  de 4f 1e 00 91 07 00 00  00 00 00 00 02 00 00 00  |.O..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 f7 ea 72 10 4e  4f 20 4e 41 4d 45 20 20  |..)..r.NO NAME  |
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
00000100  7d 00 66 b8 50 0f 00 00  66 ba 00 00 00 00 bb 00  |}.f.P...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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



---

### Post by patelsagar on 2011-02-01
Just an update: 

I had recovered partitions already, but may be I didn't write the partition table then after. I have attached screenshots of my recovered partitions. There are 3 extended partitions, so I haven't decided to write partitions yet, I am not sure if 3 extended partitions are normal or not for 4 original partitions (originally there were C,D,E and F partitions).

Going to sleep now, it's late here.

Have a wonderful day!

Edit: Attached 3rd image, which shows that my partitions can be recovered as they were! Yay! Though I will wait for a green signal from you guys ):P

---

### Post by amarendra on 2011-02-10
You can, I guess, recover your partition using "Deeper Search". I recovered mine after windows 7 had unallocated it. However, I am now, struggling with no grub installed and a "BOOTMGR missing" error.

---

### Post by patelsagar on 2011-02-14
> **amarendra said:**
> You can, I guess, recover your partition using "Deeper Search". I recovered mine after windows 7 had unallocated it. However, I am now, struggling with no grub installed and a "BOOTMGR missing" error.

My problem is solved already. Just got partitions back and reinstalled Windows 7 and then the Ubuntu.

---

