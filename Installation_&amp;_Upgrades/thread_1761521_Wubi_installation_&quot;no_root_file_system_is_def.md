---
title: "Wubi installation &quot;no root file system is defined&quot;"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by esigma on 2011-05-18
Hi
   Iam a newbie and I have installed ubuntu 11.04 inside Windows(Wubi).But when I boot into ubuntu I get an error message "[B]no root file system is defined".[SIZE=1]
    [/SIZE][/B]I have gone through this forum and found a similar thread at 
[http://ubuntuforums.org/showthread.php?t=1743189&highlight=no+root+filesystem+specified](http://ubuntuforums.org/showthread.php?t=1743189&highlight=no+root+filesystem+specified)
   I understand that different problem may have same symptoms and so Im not trying the fix given there.But I have run boot info script as per the suggestion of srs5694 and here is the result text file

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 52098858.
    Operating System:  
    Boot files:        /menu.lst /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 4 sectors/track, 2442210 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    52,097,023    52,094,976   7 NTFS / exFAT / HPFS
/dev/sda2          52,098,858   110,077,379    57,978,522   7 NTFS / exFAT / HPFS
/dev/sda3          63,215,775   109,431,514    46,215,740   5 Extended
Empty Partition.
/dev/sda4    *    110,077,952   156,299,263    46,221,312   7 NTFS / exFAT / HPFS

/dev/sda2 overlaps with /dev/sda3

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8906-6DB8                              vfat       Ubuntu
/dev/sda2        3830E1DA30E19EDE                       ntfs       
/dev/sda4        3210CAFD10CAC6D7                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/3210CAFD10CAC6D7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/menu.lst: ================================

--------------------------------------------------------------------------------
default 0
hiddenmenu
map --mem /WOW7.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       0

========================== sda4/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sda3

00000000  54 d3 b1 7a d4 44 1b 47  65 d6 5b cd ba 53 19 6d  |T..z.D.Ge.[..S.m|
00000010  60 d6 40 d4 97 96 c0 f2  1a 61 99 1d 85 e1 c9 76  |`.@......a.....v|
00000020  7b f8 e4 4b 15 ae 0e 11  8a f2 91 a6 b7 d2 b4 2b  |{..K...........+|
00000030  79 ac d2 2f 67 79 79 20  97 1f d3 b9 a5 32 29 50  |y../gyy .....2)P|
00000040  90 22 d9 03 80 32 59 bd  fb 1a ea ac b3 c3 80 fe  |."...2Y.........|
00000050  54 7f b7 2e 1d 32 7a 5c  94 fb bb 5d 91 c3 8c 5f  |T....2z\...]..._|
00000060  92 a1 21 9e 4e 2c 8f 6b  43 90 98 6c 3d 06 cf 9d  |..!.N,.kC..l=...|
00000070  be 4c e7 3a 79 3d 3a 90  53 27 95 ec 1d 28 fc 9a  |.L.:y=:.S'...(..|
00000080  e4 97 34 78 19 68 90 a1  06 b9 54 20 be 9a 06 8d  |..4x.h....T ....|
00000090  26 dc 6a 80 12 14 a8 9a  38 73 ed 6a 0e 14 ae e5  |&.j.....8s.j....|
000000a0  c0 49 5a 32 4e ad bd 27  35 f3 7e d0 48 3a 67 1a  |.IZ2N..'5.~.H:g.|
000000b0  c5 90 6c 3d 76 f3 72 ef  6b f0 0a e8 f5 34 b6 f6  |..l=v.r.k....4..|
000000c0  01 dd ee 8a 72 55 6c 97  37 14 11 05 d2 1b c7 ea  |....rUl.7.......|
000000d0  68 cc b9 a4 02 65 32 47  f5 19 c1 5b d6 48 f8 1f  |h....e2G...[.H..|
000000e0  9b 7b ae d8 ff 2b f9 5d  bd 73 6e ea b0 bc 59 56  |.{...+.].sn...YV|
000000f0  3e f1 43 5f 39 95 5a aa  9e 19 ae 2b f5 cb 43 71  |>.C_9.Z....+..Cq|
00000100  bb 2c f7 43 97 05 d5 cc  a8 07 b3 ce 1d f2 ac 14  |.,.C............|
00000110  63 31 7d d2 03 92 1b 46  a5 6f 81 8e 68 e5 09 1f  |c1}....F.o..h...|
00000120  9d cf 36 59 17 0f 64 3d  f3 bd bd 59 d2 66 9d 77  |..6Y..d=...Y.f.w|
00000130  ee f5 b2 6e 3d 1f 83 c6  df 2d 0f fb a9 ab 48 aa  |...n=....-....H.|
00000140  52 7c 92 ac b8 fc 7c 77  b7 ba f3 84 ee 92 2b 94  |R|....|w......+.|
00000150  cc 28 bc 72 04 d4 e3 3e  73 66 a5 ec f9 2c e1 83  |.(.r...>sf...,..|
00000160  62 ce 77 df 89 cf 72 d0  ed 1b 11 32 f2 5e 0a 17  |b.w...r....2.^..|
00000170  9a 7e df fb 70 f2 a8 0c  51 13 36 73 0f 66 ff fd  |.~..p...Q.6s.f..|
00000180  a1 fa 90 7a ef 0e 9f ff  41 56 39 f9 70 f0 4d 1e  |...z....AV9.p.M.|
00000190  0e 27 07 ff 51 01 e0 68  ac 75 db 44 4f d1 52 5a  |.'..Q..h.u.DO.RZ|
000001a0  0f 00 d0 88 1a d5 06 cd  98 bf f2 bb 2e f7 fb bc  |................|
000001b0  b8 2e 0b 54 f8 cd e7 62  f5 af 32 1f 63 c9 00 00  |...T...b..2.c...|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

loop: can't delete device /dev/loop1: Device or resource busy
umount: /media/3830E1DA30E19EDE: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")
```Please help me.

---

### Post by Rubi1200 on 2011-05-18
Hi and welcome to the forums :-)

You have a few issues going on here, but I want to deal with them one at a time and also call in bcbc, the Wubi expert, and srs5694, the partition expert, for their opinions.

Patience is important and please do not try anything until we confirm with you what we think are the best options.

Problem # 1; your Wubi install is failing to mount. There could be a number of reason for that and we can fix it, hopefully, with a file-system check utility called fsck.

Problem # 2; you appear to have overlapping partitions on sda2/3. This may or may not be related to problem # 1. The solution may also need to be done before the solution for # 1 and that is why you need to wait.

Problem # 3; the boot flag is set on sda4 but I don't see any of the Windows boot files there or on any of the other partitions. Are you sure you copied and pasted the _entire_ script results? It is also a bit unusual to find the boot flag on sda4 and not, for example, on sda1 or 2 (where one might normally expect it). Have you moved/deleted partitions recently? Which partitioning tools, if any, have you used recently?

As I said, I am going to ask for more opinions so please hang in there for the moment.

---

### Post by esigma on 2011-05-18
Thank You Rubi
> Problem # 3; the boot flag is set on sda4 but I don't see any of the  Windows boot files there or on any of the other partitions. Are you sure  you copied and pasted the _entire_ script results? It is also a  bit unusual to find the boot flag on sda4 and not, for example, on sda1  or 2 (where one might normally expect it). Have you moved/deleted  partitions recently? Which partitioning tools, if any, have you used  recently?
Well I think the problem 3 is because I once installed windows xp in a partition along with windows 7.And due to some reasons the xp didnt start.So I deleted all xp related files by logging into windows 7.Could that be a reason?
And yes Im sure that I copied the entire script here, I just checked again.
I have not used any other tool for partition other than the one that comes by default in windows xp and windows 7.

---

### Post by srs5694 on 2011-05-18
It looks to me as if /dev/sda3 (your extended partition) is useless, and since it overlaps with /dev/sda2 it should be deleted. Use fdisk for this task.

I wouldn't worry too much about the boot flag on /dev/sda4. Contrary to popular belief, modern versions of Windows don't actually require it if booted via GRUB or some other non-Windows tool, although the standard Windows boot loader does use it to determine which partition to boot. In fact, given that Windows XP was once installed there, it's conceivable that Windows 7 placed some of its boot files there and so moving the boot flag elsewhere could render the computer unbootable. Linux doesn't use the boot flag at all. Thus, I don't think this is related to your Linux boot problems, and given that Windows boots on this computer, I'd be very reluctant to move the boot flag. If you do move it and find that it causes problems, it can be easily moved back.

I'm far from a WUBI expert, so I can't help with your WUBI issues, unless perhaps the presence of the illegal /dev/sda3 is causing your WUBI install to flake out.

---

### Post by esigma on 2011-05-18
Thank you srs 5694

> It looks to me as if /dev/sda3 (your extended partition) is useless, and  since it overlaps with /dev/sda2 it should be deleted. Use fdisk for  this task.

Could you please tell me how to delete that extended partition using fdisk.Should I boot into ubuntu using live cd for this?

---

### Post by esigma on 2011-05-18
Thanks to srs 5694 and Rubi 1200.The problem was solved.Deleted the extended partition and then started ubuntu now ubuntu is working fine.

---

### Post by Rubi1200 on 2011-05-18
> **esigma said:**
> Thanks to srs 5694 and Rubi 1200.The problem was solved.Deleted the extended partition and then started ubuntu now ubuntu is working fine.
This is great news :-)

I am really pleased you managed to get this sorted out.

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

### Post by hamid_big on 2011-08-09
Hi, I have a same problem.....PLZ HELP
```
 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/nvidia_dhiaeffd.

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvidia_dhiaeffd1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

nvidia_dhiaeffd1/Wubi: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

nvidia_dhiaeffd2: ______________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

nvidia_dhiaeffd5: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, 
                       nvidia_dhiaeffd5 starts at sector 63.
    Operating System:  
    Boot files:        

nvidia_dhiaeffd6: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, 
                       nvidia_dhiaeffd6 starts at sector 63.
    Mounting failed:   mount: unknown filesystem type ''
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
1 heads, 63 sectors/track, 31008335 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,127 1,953,520,065   7 NTFS / exFAT / HPFS


Drive: nvidia_dhiaeffd _____________________________________________________________________

Disk /dev/mapper/nvidia_dhiaeffd: 122.9 GB, 122941210624 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240119552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_dhiaeffd1   *             63    42,845,354    42,845,292   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_dhiaeffd2         42,845,355   240,107,489   197,262,135   f W95 Extended (LBA)
/dev/mapper/nvidia_dhiaeffd5         42,845,418   129,034,079    86,188,662   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_dhiaeffd6        129,034,143   240,107,489   111,073,347   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/nvidia_dhiaeffd1 5EFC0382FC035425                       ntfs       
/dev/mapper/nvidia_dhiaeffd5 64582061582033E8                       ntfs       
/dev/mapper/nvidia_dhiaeffd6 105C53D95C53B7E4                       ntfs       
/dev/sda                                                nvidia_raid_member 
/dev/sdb1        80944B43944B3B44                       ntfs       FreeAgent GoFlex Drive

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
nvidia_dhiaeffd
nvidia_dhiaeffd1
nvidia_dhiaeffd5
nvidia_dhiaeffd6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/dm-3        /media/105C53D95C53B7E4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


========================== nvidia_dhiaeffd1/boot.ini: ==========================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on nvidia_dhiaeffd1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on nvidia_dhiaeffd2



========= Devices which don't seem to have a corresponding hard drive: =========

sda: "pdc" and "nvidia" formats discovered (using nvidia)! 

=============================== StdErr Messages: ===============================

ERROR: only one argument allowed for this option
hexdump: /dev/mapper/nvidia_dhiaeffd2: No such file or directory
hexdump: /dev/mapper/nvidia_dhiaeffd2: No such file or directory
ERROR: only one argument allowed for this option



```

---

### Post by saidii89 on 2012-05-15
a lot of users faced such problem and the solution to it is pretty simple
 
make sure that the partition file system [you wish to install linux, ubunto or backrack on it] is ext4, ext3 or ext2 [not fat32 or ntfs]
 
then mount "/" on it, how? easy: 
1- on the installation process press [change] on the partition you wish to use
 
2- make sure [do not use this partition] scroll is not chosen, scroll to ext4, ext3 or ext2
 
3- and on "mount" field write "/"
 
4- when clicking ok then next a message will appear saying something like [swap area was not defined, do you wish to continue or choose a swap area? because bla bla bla..], click "ok" and continue or click "go back" and choose another partition and click change, on the file system scroll choose [swap] and click ok and next
 
this will solve both "no root file system is defined" and the "swap area" message, if you still get the swap area message then on step 4 mount "/swap" to the partition
 
**AND THIS SOLVES IT!**
 
every time anyone need solutions don't hesitate to search for help
 
ask me if you need something and I can help I will do it, I don't log to forums a lot, I found this thread while searching on google and I copied this answer to all the threads with the same problem, so If you need contact here it goes ->
 
[http://www.twitter.com/saidii89](http://www.twitter.com/saidii89)
[http://www.facebook.com/saidii89](http://www.facebook.com/saidii89)
[http://www.formsrping.me/saidii89](http://www.formsrping.me/saidii89)
[http://www.saidi-theory.blogspot.com]("http://www.saidi-theory.blogspot.com/")
 
brought to you by Sa'eed Awad
[Saidi Theory Solutions] by Sa'eed Awad

---

### Post by oldos2er on 2012-05-15
Old thread closed.

---

