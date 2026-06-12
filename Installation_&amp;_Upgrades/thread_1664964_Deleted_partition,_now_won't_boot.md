---
title: "Deleted partition, now won't boot"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Chazz44able on 2011-01-11
Hi, I have been dual-booting Windows XP and Ubuntu 10.04. Ubuntu wasn't working properly and so I wanted to re-install it, so I backed up my data and took screen shots of my settings. Under some very poor advice I deleted the Ubuntu partition in Windows XP strait out. When I re-booted, nothing booted at all - as grub is still there. However I booted from a Live CD and went into Gparted and it showed a blank hard drive, ( it also does this if I attempt to install Ubuntu again when I get to the options on instillation it says that no other OSs or partitions are present). After a few attempts I was able to mount the drive from the live CD. This means that the partitions for Windows are still there (I checked in Disk Utility and XP it is set as being bootable). I then booted an XP recovery disk and after many, many, many, many attempts, it always said that there was no hard drive present at all. The only thing I can think of is creating a very small partition for another Ubuntu install and seeing if I can boot windows from that using another GRUB, but I'm not h installing hopeful for that.

I don't mind that much, however it does have the Adobe Master Suite on it that I want to continue to use (I don't have the install disk - it was installed when I bought it). If it wasn't for that then I'd just wipe the disk and install Ubuntu on it's own. Please can you help.

---

### Post by Chazz44able on 2011-01-11
Here's my boot info (using the boot info script):
```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   173,777,139   173,777,077   7 HPFS/NTFS
/dev/sda2         173,778,942   214,515,711    40,736,770   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5     ? 2,704,244,936 3,328,156,127   623,911,192  81 Minix / old Linux
/dev/sda3         214,515,945   234,436,544    19,920,600   7 HPFS/NTFS

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0867C593114B5705                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        FAFC5F30FC5EE703                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda3/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  44 9c d1 c8 16 59 8a 1c  11 6d c1 81 02 a8 cd 98  |D....Y...m......|
00000010  09 df a1 09 e8 f0 40 f5  04 51 e0 13 9c 86 af 67  |......@..Q.....g|
00000020  4d da c7 c1 4f 0d db 16  82 f4 c7 c2 3d e3 00 0a  |M...O.......=...|
00000030  10 74 8a 38 f7 e9 68 52  f3 22 29 07 e7 99 dc 05  |.t.8..hR.").....|
00000040  54 5f 72 2e 75 bf aa 71  b4 df 0c 3e fa 44 cd d8  |T_r.u..q...>.D..|
00000050  d5 fa a5 47 6e da 1a 72  e1 44 b3 9b 7c c0 c5 80  |...Gn..r.D..|...|
00000060  f7 64 5c 9a 0e 18 56 fe  a6 c0 71 0b 48 6a cb 0b  |.d\...V...q.Hj..|
00000070  8e 9b a6 36 73 36 78 11  11 15 b8 8b ac 56 ec 09  |...6s6x......V..|
00000080  9d 08 01 f9 4b e2 6e 73  7f bf 35 fd c0 b2 9b b1  |....K.ns..5.....|
00000090  1e f5 3b 34 74 77 49 0e  28 6e 0d d4 64 12 98 00  |..;4twI.(n..d...|
000000a0  8f e2 22 7f ab 07 69 f5  14 2f 79 d5 fc 7d 5d 74  |.."...i../y..}]t|
000000b0  58 bd 9b fe d1 de b9 57  c3 76 e6 e9 3a f6 70 ff  |X......W.v..:.p.|
000000c0  39 81 72 36 0a 47 81 04  32 a7 f7 53 30 fe 6a ad  |9.r6.G..2..S0.j.|
000000d0  6e 98 3b 37 a9 83 5c 9c  3e c8 34 ca 3e 95 57 cb  |n.;7..\.>.4.>.W.|
000000e0  4f f8 d9 96 b6 a6 2a a4  b6 b5 d0 2f 2f 25 fd 5c  |O.....*....//%.\|
000000f0  a5 3a e5 b1 5b b6 b5 7c  c4 1e c6 49 d0 99 b7 8b  |.:..[..|...I....|
00000100  d3 ae 22 84 dc 82 ad a6  7f 9e 92 0a ec 8a 4a 28  |.."...........J(|
00000110  df 0f a8 0c f8 bc 33 fe  87 6e 76 bb 7f 5d af fc  |......3..nv..]..|
00000120  f7 b6 55 8d ed de b8 8d  1c ee 12 5e 44 d7 35 b4  |..U........^D.5.|
00000130  40 d4 17 06 a9 dc 62 22  df d0 67 2c b2 4d 15 62  |@.....b"..g,.M.b|
00000140  a3 0a f5 b1 5e 16 03 e2  2b 80 69 f8 08 64 5c d4  |....^...+.i..d\.|
00000150  c6 dd 27 8e ea 4c 6a 15  a5 e1 3e 78 cc ad 3d cb  |..'..Lj...>x..=.|
00000160  82 ee 0d 6c 6e bd 20 50  18 81 c2 06 44 f9 d3 a8  |...ln. P....D...|
00000170  72 ac 68 ec 62 09 95 ed  58 64 6e de f9 83 e1 7e  |r.h.b...Xdn....~|
00000180  6c af 08 c9 a9 f1 d9 d2  46 a6 20 69 d8 24 d0 b1  |l.......F. i.$..|
00000190  b8 7f b3 0e c8 d7 c9 00  42 18 e5 9e c6 48 89 88  |........B....H..|
000001a0  9c ff 64 26 50 af 45 3d  7c 56 4a ce 9c eb 97 e4  |..d&P.E=|VJ.....|
000001b0  47 9f 4e f9 66 46 29 2f  80 76 f9 3b 65 cf 00 fe  |G.N.fF)/.v.;e...|
000001c0  ff ff 05 fe ff ff c3 57  52 02 3f 40 1b 00 00 00  |.......WR.?@....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory


```

---

### Post by shinigami82654 on 2011-01-11
Hey I don't know how much help this is but after I deleted Ubuntu (I'm running Win 7 and Ubuntu 8.04) the fact that grub was still supposed to be there but wasn't made it so my computer wouldn't start at all. I didn't have trouble reinstalling from the live disc and made a new partition and it works just fine again.

Hope this helps!

---

### Post by oldfred on 2011-01-11
You have major partition problems and as long as you have those many things will not work as they have to read the partition table to work.
[PHP]
/dev/sda2         173,778,942   214,515,711    40,736,770   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5     ? 2,704,244,936 3,328,156,127   623,911,192  81 Minix / old Linux

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
[/PHP]If in gparted you can delete them that may be the easiest, but it may not let you do anything. 

to make sure you have info on the good parts of your partition table I would do this first and save to another device:
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

It depends on what the errors are in the partition table and I do not know all details, but one user was just able to reread the PT.txt back into the table with sfdisk and it fixed his problem.

I would see if testdisk sees partitions and lets you update:


enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by anupal.bora on 2011-01-11
i have a booting problem i have windows xp sp 2 in c: in which i repartitioned by shrinking and installed ubuntu10.04 after this my laptop booted only ubuntu and in ubuntu i could access the ntfs drive c : and see the windows files and all as u see normally
but the ubuntu didn't show the rest of partitioned drive after this i inserted xp installation disc to see partition table and just formatted the blank i: drive and rebooted after which now only xp runs and when i press f8 os choice only shows xp now the status is 

c: was 40 gb capacity 
now after shrinking its at 15 gb
rest 25 is the ubuntu which i cannot find nor can i boot but it is there.


 i am unable to live boot as it ask username and password which i don't know
and if i go to install menu custom live says no os found and no partition-use entire disk can u give me an understanding solution[EMAIL="anupal.bora@gmail.com"]anupal.bora@gmail.com[/EMAIL]

---

### Post by oldfred on 2011-01-11
anupal.bora Welcome to forum, but please do not hijact another's thread. If your issues are not identical (yours are not) or if you are not contributing to solutions, please start a new thread.

Windows does not 'see' Linux partitions, do not use windows tools to edit or attempt to modify Linux partitions.

As part of your new thread run this so we can see your current configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Chazz44able on 2011-01-12
```

> **oldfred said:**
> You have major partition problems and as long as you have those many things will not work as they have to read the partition table to work.
[PHP]
/dev/sda2         173,778,942   214,515,711    40,736,770   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5     ? 2,704,244,936 3,328,156,127   623,911,192  81 Minix / old Linux

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
[/PHP]If in gparted you can delete them that may be the easiest, but it may not let you do anything. 

to make sure you have info on the good parts of your partition table I would do this first and save to another device:
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

It depends on what the errors are in the partition table and I do not know all details, but one user was just able to reread the PT.txt back into the table with sfdisk and it fixed his problem.

I would see if testdisk sees partitions and lets you update:


enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

```
Thanks for the quick replies, as I said though, I can't see anything in Gparted, it shows the HDD as being completely empty, but with only 111GB, not the full 121GB, which is strange... the only explanation I can think of is that the other 10GB that is not shown up is the "HP Back up" one.

---

### Post by Chazz44able on 2011-01-12
> **shinigami82654 said:**
> Hey I don't know how much help this is but after I deleted Ubuntu (I'm running Win 7 and Ubuntu 8.04) the fact that grub was still supposed to be there but wasn't made it so my computer wouldn't start at all. I didn't have trouble reinstalling from the live disc and made a new partition and it works just fine again.

Hope this helps!

That's exactly what  I wanted to, however I can't create another partition to put Lucid in, as the install disk wont recognise any of the partitions, neither will Gparted. Can you get the Adobe suite for Linux? (I know obviously about GIMP, would you be able to get Dreamweaver for Linux, for example.

---

### Post by Chazz44able on 2011-01-13
I have installed Ubuntu again on the other end of the HDD. I can't even see the XP file system in  it though, which I can do if I boot from a Live CD. I installed BURG also in order to check the OSs that are available in the hope that that would find XP... but it didn't work.

---

### Post by shinigami82654 on 2011-01-13
I ended up making a new partition on the hdd and then going back into windows and keeping the newest one, deleting the old partitions that *had* linux on it. I'm sure with free and untouched partition space you could go back into linux and add partition space onto it. I'm not sure though...

---

### Post by Chazz44able on 2011-01-14
> **shinigami82654 said:**
> I ended up making a new partition on the hdd and then going back into windows and keeping the newest one, deleting the old partitions that *had* linux on it. I'm sure with free and untouched partition space you could go back into linux and add partition space onto it. I'm not sure though...
Well my problem is that I can't access windows at all. So I can't go back into it.

---

### Post by dino99 on 2011-01-14
boot on partedmagic, or windows cd

with windows cd: run chkdsk /f on the windows drive (might be "c:")

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Chazz44able on 2011-01-14
> **dino99 said:**
> boot on partedmagic, or windows cd

with windows cd: run chkdsk /f on the windows drive (might be "c:")

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

what's partedmagic - does that boot you into like an XP Live CD? I can't see the partitions in G-parted :(

---

### Post by oldfred on 2011-01-14
I think you only get chkdsk from the windows CD. You can run ntfsfix from Ubuntu.
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".


chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Chazz44able on 2011-01-14
The drive is flagged as being clean ATM, but I'll try that when I get home.

---

### Post by Chazz44able on 2011-01-14
The drive is flagged as being clean ATM, but I'll try that when I get home.

---

### Post by Chazz44able on 2011-01-18
I've just re-installed it on the other side of the HDD and I really CBA to recover windows, it was a pain in the **** anyways, so I'll just re-format the disk and then leave it.

---

