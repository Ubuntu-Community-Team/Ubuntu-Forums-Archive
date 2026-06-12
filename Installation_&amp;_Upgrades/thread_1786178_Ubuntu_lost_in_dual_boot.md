---
title: "Ubuntu lost in dual boot"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by zanuxzan on 2011-06-19
Sometime ago I installed (from memory...) Ubuntu 9.10 using wubi, as dual boot with Windows 7 onto a friends laptop, which is used in an art gallery to display a piece using openframeworks.

Unfortunately someone at the gallery or more than likely something has corrupted/removed the dual boot.

When the system boots it comes up with the Windows boot load which gives the option of Windows or Ubuntu. When Ubuntu is chosen it drops to the grub prompt. From here I mostly get errors saying 'No kernel found'.

I've tried various things, such as [replacing wubildr]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210") and also attempted to follow the guide [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). Each time I get stuck tho, as there doesn't appear to be a valid Ubuntu install (unless I'm missing something???). Is it possible that Windows or AVG or something like that has completely removed the Ubuntu install?

Below is the output of boot_info_script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    16,386,047    16,384,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     16,386,048   260,583,423   244,197,376   7 NTFS / exFAT / HPFS
/dev/sda3         260,583,424   488,396,799   227,813,376   f W95 Extended (LBA)
/dev/sda5         260,585,472   488,396,799   227,811,328   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        800E-1B1C                              vfat       RECOVERY
/dev/sda2        168850BF88509ED5                       ntfs       
/dev/sda5        B29814CD981491C9                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 26 00  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 fa 00 61 3e 00 00  00 00 00 00 02 00 00 00  |....a>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1c 1b 0e 80 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

```

Any ideas?

---

### Post by TheDoctorX on 2011-06-19
> **zanuxzan said:**
> Sometime ago I installed (from memory...) Ubuntu 9.10 using wubi, as dual boot with Windows 7 onto a friends laptop, which is used in an art gallery to display a piece using openframeworks.

Unfortunately someone at the gallery or more than likely something has corrupted/removed the dual boot.

When the system boots it comes up with the Windows boot load which gives the option of Windows or Ubuntu. When Ubuntu is chosen it drops to the grub prompt. From here I mostly get errors saying 'No kernel found'.

I've tried various things, such as [replacing wubildr]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210") and also attempted to follow the guide [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). Each time I get stuck tho, as there doesn't appear to be a valid Ubuntu install (unless I'm missing something???). Is it possible that Windows or AVG or something like that has completely removed the Ubuntu install?

Below is the output of boot_info_script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    16,386,047    16,384,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     16,386,048   260,583,423   244,197,376   7 NTFS / exFAT / HPFS
/dev/sda3         260,583,424   488,396,799   227,813,376   f W95 Extended (LBA)
/dev/sda5         260,585,472   488,396,799   227,811,328   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        800E-1B1C                              vfat       RECOVERY
/dev/sda2        168850BF88509ED5                       ntfs       
/dev/sda5        B29814CD981491C9                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 26 00  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 fa 00 61 3e 00 00  00 00 00 00 02 00 00 00  |....a>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1c 1b 0e 80 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

```

Any ideas?

in which partition did u install ubuntu?? if u installed ubuntu with wubi it must be the same partition of win7 ... for your problem i don't see real solutions :( ... but if u want u can recover your ubuntu files ... just go on the partition u installed ubuntu and search for a folder called found.0000 ... or something like that ... the there is another folder dir0000.chk i think ... what u need is a file called root.disk ... to open it u must install on win7 this program "ext2toexplore" i'll gave u the link at the end ... with this program u can copy to win your ubuntu files ... after it you can unistall ubuntu and then reinstall it ... this is the best and simple way ...:)

---

### Post by TheDoctorX on 2011-06-19
here is the ext2explore link [http://www.softpedia.com/dyn-postdownload.php?p=136458&t=0&i=1]("http://www.softpedia.com/dyn-postdownload.php?p=136458&t=0&i=1")

---

### Post by zanuxzan on 2011-06-19
> **TheDoctorX said:**
> in which partition did u install ubuntu?? if u installed ubuntu with wubi it must be the same partition of win7 ... for your problem i don't see real solutions :( ... but if u want u can recover your ubuntu files ... just go on the partition u installed ubuntu and search for a folder called found.0000 ... or something like that ... the there is another folder dir0000.chk i think ... what u need is a file called root.disk ... to open it u must install on win7 this program "ext2toexplore" i'll gave u the link at the end ... with this program u can copy to win your ubuntu files ... after it you can unistall ubuntu and then reinstall it ... this is the best and simple way ...:)

Thanks for the quick response. I have booted up on a live cd (Ubuntu 11.04) and I do indeed have a found.000 folder, however its total size is only about 10M.

Do you think perhaps the Ubuntu "partition" (is it actually referred to as a partition when its installed with wubi?) was deleted in a Windows update or virus checker? Is there any other possible suggestion?

I don't really care too much about the data as I have it all backed up but its quite a long and tedious process to reinstall Ubuntu, openframeworks, all the libraries that I require and tune the machine again.

---

### Post by TheDoctorX on 2011-06-19
> **zanuxzan said:**
> Thanks for the quick response. I have booted up on a live cd (Ubuntu 11.04) and I do indeed have a found.000 folder, however its total size is only about 10M.

Do you think perhaps the Ubuntu "partition" (is it actually referred to as a partition when its installed with wubi?) was deleted in a Windows update or virus checker? Is there any other possible suggestion?

I don't really care too much about the data as I have it all backed up but its quite a long and tedious process to reinstall Ubuntu, openframeworks, all the libraries that I require and tune the machine again.

sometimes windows can move ubuntu files ... it's very rare, but could happen ... i still don't understand if u installed ubuntu natty with wubi or with a live cd ... probably because i'm italian :p ... do u have only the dual boot with win7 ? or u have also something else ??

---

### Post by TheDoctorX on 2011-06-19
> **TheDoctorX said:**
> sometimes windows can move ubuntu files ... it's very rare, but could happen ... i still don't understand if u installed ubuntu natty with wubi or with a live cd ... probably because i'm italian :p ... do u have only the dual boot with win7 ? or u have also something else ??

there are no real solutions with the wubi install ... i had the same problem a few time ago ... some people say that the mbr file is corrupted but when u restore it the problem persists ... the only way is reistall it ... wubi is do damn triky and difficult to control ...

---

