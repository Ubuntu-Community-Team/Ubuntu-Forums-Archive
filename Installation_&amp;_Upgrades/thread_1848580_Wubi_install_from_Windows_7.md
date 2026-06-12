---
title: "Wubi install from Windows 7"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by cocytus04 on 2011-09-22
Hi all, I've been trying to install Ubuntu 11.04 via Wubi from inside Windows 7 (I'd rather get a taste of it and see how things go before I completely wipe out the drive I'm putting it on, as it's the one with all my games on it).  I get through the installation process inside Windows just fine and reboot.  Then when I boot into Ubuntu and it is checking the configuration, it comes up with the eternal "no root file system defined" defined error.  Any help on what I need to do to fix things so I can get it to work would be greatly appreciated.  Thank you very much in advance for any help given!

Here is the log from the boot info script:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 has 
                       932337663 sectors, but according to the info from 
                       fdisk, it has 932340364 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 has 
                       43812863 sectors, but according to the info from 
                       fdisk, it has 43828020 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       210992 sectors.. But according to the info from the 
                       partition table, it has 224001 sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb1 has 
                       976769023 sectors, but according to the info from 
                       fdisk, it has 976782081 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   932,749,964   932,340,365   7 NTFS / exFAT / HPFS
/dev/sda3         932,747,264   976,575,284    43,828,021   7 NTFS / exFAT / HPFS
/dev/sda4         976,560,128   976,784,129       224,002   c W95 FAT32 (LBA)

/dev/sda2 overlaps with /dev/sda3
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   976,784,129   976,782,082   7 NTFS / exFAT / HPFS

/dev/sdb1 ends after the last sector of /dev/sdb

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E406FC1A06FBEC04                       ntfs       SYSTEM
/dev/sda2        F4CA5D7CCA5D3C54                       ntfs       OS
/dev/sda3        FE8831FE8831B64D                       ntfs       RECOVERY
/dev/sda4        22D2-D89E                              vfat       HP_TOOLS
/dev/sdb1        C88A68CF8A68BC16                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ce 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 35 3a  |........?.... 5:|
00000020  30 38 03 00 19 03 00 00  00 00 00 00 02 00 00 00  |08..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 9e d8 d2 22 4e  4f 20 4e 41 4d 45 20 20  |..)..."NO NAME  |
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

---

### Post by Rubi1200 on 2011-09-22
Hi and welcome to the forums :-)

This may be part of the problem:
```
/dev/sda2 overlaps with /dev/sda3 /dev/sda3 overlaps with /dev/sda4 /dev/sda4 ends after the last sector of /dev/sda
```

However, I would prefer that someone with more experience with such situations takes a look and offers advice.

I will send a message to srs5694, who really knows his stuff, asking him to take a look.

Meantime, please be patient and wait for one of us to respond.

---

### Post by srs5694 on 2011-09-23
Rubi1200 is quite correct that you do have partition table problems, but I have no idea if they'd produce the symptoms that you've described. Overlapping partitions are potentially quite serious. The good news, however, is that, if the Boot Info Script output is accurate, the filesystems contained in those partitions do *not* overlap. Thus, it should be safe to resize /dev/sda2, /dev/sda3, and /dev/sda4 so that they're all properly sized.

Unfortunately, I don't know of any tool that will do this completely automatically and safely. There are several ways you can approach solving the problem:


[list]
[*]You can use Linux's fdisk to delete and then re-create each partition individually and manually. This should work, but you've got to be very careful about specifying the start and end points of the partitions. The start point is particularly critical; if it's off by just one sector, the re-created partition will not align with the filesystem it's supposed to contain, which will make it impossible to access the filesystem until the error is corrected.
[*]You can use Linux's sfdisk ("sudo sfdisk -d /dev/sda > parts.txt") to save a file with a text-mode description of your partitions, edit the file to shrink the partitions to the sizes specified at the start of the Boot Info Script output, and then use sfdisk to write the changed file back again ("sudo sfdisk -f /dev/sda < parts.txt"). This has the advantage that you can safe the original file to an external medium and use it to restore the disk should something go wrong. I wrote [a Web page](http://www.rodsbooks.com/missing-parts/index.html) that describes a similar (but not quite identical) repair; check the "Fixing the Problem the Hard Way" section.
[*]You can use just about anything to delete all the partitions and then run TestDisk to try to recover them automatically. This is likely to work with little effort; however, TestDisk isn't 100% reliable, so there's a small chance that you'd end up creating a bigger problem by going this route. You could minimize the risk by using sfdisk to make a partition table backup first.
[*]You could try to find a Windows tool that will resize the partitions to match the filesystems they contain in an automatic way. There's a good chance that such a tool exists, but if so I don't know what it is, so I can't make a specific recommendation.
[*]You can back up all your partitions, wipe them all, create new partitions, and restore your data. This is tedious but it's probably the safest way to proceed.
[/list]


I recommend backing up as much of your data as possible before you proceed with any of these options, just in case you run into further problems that make matters worse.

Personally, I'd probably go with sfdisk to fix this problem, but it can be intimidating to less experienced users. Whatever you decide to do, good luck!

---

### Post by cocytus04 on 2011-09-24
Sorry, between school and work I haven't had time to do more than skim through what was said up until now. Thanks for the replies, you two. In my searches for the fix before I actually posted, I quickly saw that if I posted, I hoped that you two specifically would answer. You seem to be quite knowledgeable and very willing to assist (qualities that seem to exist together with increasing rarity on the internet these days). srs, would it be possible to explain a little more exactly what I need to do with the sfdisk option?  That seems the best one to me.  Unfortunately, my Linux/Unix experience is quite limited, and this is part of the plethora of things I have absolutely no idea what to do with. Unlike with other things, when my computer is involved, I don't like tinkering around until I have at least a basic idea of what I'm doing. :)

Do I just need to redirect the sfdisk command to the parts.txt file, go into the file, make sure each partition ends before the next, then redirect that file back to the command? I think that's what you're saying but want to confirm before I do anything.  The main thing I am wanting to confirm is the part about how exactly I need to manipulate the data in the file.

---

### Post by srs5694 on 2011-09-24
> **cocytus04 said:**
> Do I just need to redirect the sfdisk command to the parts.txt file, go into the file, make sure each partition ends before the next, then redirect that file back to the command? I think that's what you're saying but want to confirm before I do anything.  The main thing I am wanting to confirm is the part about how exactly I need to manipulate the data in the file.

Yes, you've got the gist of it. You'll need to do some math, though, since sfdisk describes partitions in terms of start points and lengths, rather than start points and end points. To save some effort and minimize the risk of errors, you can use the lengths reported early in the Boot Info Script output, as in:

```

    Boot sector info:   According to the info in the boot sector, sda2 has 
                       932337663 sectors, but according to the info from 
                       fdisk, it has 932340364 sectors.

```

This indicates that /dev/sda2's filesystem is 932337663 sectors long, so you can use that value in sfdisk's length field. It won't hurt to double-check the arithmetic, though. (A hint: Use a calculator applet, so you can cut-and-paste these long values. That'll minimize the risk of a typo causing confusion or a mistake.)

---

### Post by cocytus04 on 2011-09-24
Thank you so much for the assistance. The sfdisk solution worked perfectly. As of this moment, ubuntu is working on the rest of the installation (three cheers for smart phones... don't even have to wait to thank you). I really can't thank you enough. If I could buy you a pizza I would! :D

---

