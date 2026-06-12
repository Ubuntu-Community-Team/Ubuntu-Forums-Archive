---
title: "Ubuntu 10.04 / Windows XP dual boot (using Grub2) Issue"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by dbeloved on 2011-10-11
Compliments.

I had Windows XP on my Hp Compaq Mini and I tried to install Ubuntu 10.04 LTS on it.

During the installation, I shrunk the Hard Drive from the normal 160gb to 130 and I used the 30gb shrunk to make the swap and boot for Ubuntu.

First thing I saw after reboot was the boot loader did not show and it only led me to Ubuntu 10.04 CLI intro which I entered.

I have tried to check through but the Windows XP is not there in the boot order again.

When I used Ubuntu 7.10 LiveCD on it and checked for the partitions using sudo fdisk -l, it read the following:
/dev/sda1 * .... HPFS/NTFS
/dev/sda2 ..... Extended
/dev/sda3 ...... Linux
/dev/sda5 ...... Linux swap / Solaris

Can my Windows XP still be retrieved? How do I go about it.

---

### Post by An Sanct on 2011-10-11
Welcome to the forums!

If you installed on the 30Gb partition, then Windows is still there.

Boot from the installation media again and select "Try Ubuntu (without changes to the system)", from there, you can confirm if Windows is still there.

If you can still see it, then proceed with GRUB reinstall ([more info in this thread]("http://ubuntuforums.org/showthread.php?p=10440484")). If you have any problems or questions, please let us know.

---

### Post by Rubi1200 on 2011-10-11
Hi and welcome to the forums dbeloved :)

I highly recommend you post the results of the boot info script before making any more changes to the system.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by dbeloved on 2011-10-12
I must confess, Ubuntu is rich! With the prompt response I am receiving on my enquiries since it was posted, I am definitely bought over now.

I will post the  boot info script shortly in giving you the breakdown. Seems I can boot in with a 7.10 LiveCD to do that. Thanks Rubi1200

I appreciate An Sanct too for the comment. Save for Rubi1200, I wanted to proceed with recommendations on this thread: 
[http://ubuntuforums.org/showthread.php?t=1669478](http://ubuntuforums.org/showthread.php?t=1669478) 
Seems it is a similar problem and what [Quackers]("http://ubuntuforums.org/member.php?u=369240") recommended with testdisk [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) should work I suppose.

But first I will try to get the boot info script out now.

Merci.

---

### Post by An Sanct on 2011-10-12
Thank you dbeloved ;)

Please post the output of the *boot info script* Rubi1200 proposed (it saved mi behind a few times...). After doing so, it will be clear in what state your system is and a solution will be simpler.

---

### Post by dbeloved on 2011-10-12
Thanks a big deal, I have my RESULTS.TXT and it is posted below:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b88a7

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   263,739,104   263,739,042   7 NTFS / exFAT / HPFS
/dev/sda2         263,753,726   267,659,263     3,905,538   5 Extended
/dev/sda5         263,753,728   267,659,263     3,905,536  82 Linux swap / Solaris
/dev/sda3         267,659,264   312,580,095    44,920,832  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3820 MB, 3820486656 bytes
214 heads, 62 sectors/track, 562 cylinders, total 7461888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     7,461,887     7,461,824   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda3        fa216e63-354a-45cd-83a5-09435d7104a7   ext3       
/dev/sda5        5de07369-f7ac-48d3-9606-26bd7b164caa   swap       
/dev/sdb1        FCB5-74B3                              vfat       MICKEN

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/scd1        /media/nProtectScanner   iso9660    (ro,nosuid,nodev,uid=999,utf8)
/dev/sdb1        /media/MICKEN            vfat       (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  85 96 7c 27 0c 80 12 e0  1e 15 4f 90 17 58 c9 64  |..|'......O..X.d|
00000010  bd 50 2b b0 34 56 0b e8  fe 6a 9e 08 b2 c5 03 64  |.P+.4V...j.....d|
00000020  ea d6 5c 6c 0f 83 af 0e  d3 9b 5b 8a c1 7b 35 de  |..\l......[..{5.|
00000030  f6 12 37 a2 b6 de 9f 39  13 8d 89 79 18 fa 16 83  |..7....9...y....|
00000040  cd 1c 12 00 82 43 e0 76  e9 9d b6 46 94 f2 7a c8  |.....C.v...F..z.|
00000050  66 71 9e 72 21 bd 3d 6d  8d cb dc f0 4a 08 ac fd  |fq.r!.=m....J...|
00000060  13 d4 e9 85 bd f9 97 99  ce c8 57 5a d1 c0 e0 16  |..........WZ....|
00000070  1f 49 71 1e 85 1a 8a ab  f3 13 e8 c1 99 c3 82 04  |.Iq.............|
00000080  30 b4 02 38 90 0c 47 4c  1e 3f 5a 09 50 31 2e bd  |0..8..GL.?Z.P1..|
00000090  fb e4 99 45 f9 0f 27 6c  04 6a 50 e3 1a 8b 7e b5  |...E..'l.jP...~.|
000000a0  07 cd 25 00 00 82 00 00  08 5d 02 ba 25 00 00 74  |..%......]..%..t|
000000b0  01 01 1b 00 00 00 00 08  9d 0b 00 00 af 2e 00 00  |................|
000000c0  a8 00 36 13 f6 bf a4 e3  5c 68 e3 42 55 7c fe 93  |..6.....\h.BU|..|
000000d0  8d 71 a3 8d 09 55 f3 fb  fe 4e c1 b1 d0 1d 2d 82  |.q...U...N....-.|
000000e0  6d c7 c7 5c 0f a8 4d 14  94 05 ba b5 28 9a 56 d1  |m..\..M.....(.V.|
000000f0  2d 46 ea 5b ed 91 61 94  a6 96 1c a4 92 d0 35 26  |-F.[..a.......5&|
00000100  30 90 c3 23 fc 89 c1 4d  01 d6 00 5e 5d 96 e4 05  |0..#...M...^]...|
00000110  c8 ea fd 6b 45 9b 90 22  34 ab 36 6e 9b bb 05 97  |...kE.."4.6n....|
00000120  99 1a 7b c8 cd 28 8c de  ef 62 44 d2 07 80 f7 d6  |..{..(...bD.....|
00000130  05 c9 7b e9 9d 05 8b 38  a0 a4 c2 41 0d a9 04 16  |..{....8...A....|
00000140  4a 4a cb 1b c9 21 a8 9f  1f 49 03 7a d5 05 a5 34  |JJ...!...I.z...4|
00000150  4b f6 ab dd 01 0d 64 69  b1 0b 8a 05 0a 19 09 0d  |K.....di........|
00000160  21 89 d2 42 15 21 bc 0c  18 dc f6 19 41 fc dd 3f  |!..B.!......A..?|
00000170  7e 54 3f 14 be aa 87 e9  6c a5 04 3f 08 7c 98 62  |~T?.....l..?.|.b|
00000180  58 25 d6 65 f6 1d e8 43  57 b0 48 c7 78 90 17 4e  |X%.e...CW.H.x..N|
00000190  74 f0 58 16 c4 9e 77 4f  a0 f3 82 87 0d f2 78 38  |t.X...wO......x8|
000001a0  89 62 26 97 45 c1 88 6d  38 89 35 04 13 35 a1 28  |.b&.E..m8.5..5.(|
000001b0  e6 82 b9 ea 9c 43 d2 84  ac 6a 61 17 ef 84 00 fe  |.....C...ja.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 3b 00 00 00  |............;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I hope this would unearth the issue on the system.

Thanks.

---

### Post by oldfred on 2011-10-12
Did you run boot script from your 7.10 liveCD? That may have have had the NTFS drivers to 'see' sda1. It says sda3 is ext3 but if you installed ext4 then the 7.10 would not have drivers for that either.

But script is saying it cannot mount the NTFS & your main Linux partitions. That could be the missing drivers or you need chkdsk on the NTFS partition, and fsck on the Linux partition, or  a failing hard drive.

First try using your XP install disk and run chkdsk on the c: partition.
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

chkdsk c: /r

You really should have a current liveCD of the same verison of Ubuntu has you have installed.

#From liveCD so everything is unmounted,swap off if necessary, change sda3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda3
#if errors:
sudo e2fsck -f -y -v /dev/sda3

---

### Post by dbeloved on 2011-10-12
> **oldfred said:**
> Did you run boot script from your 7.10 liveCD? That may have have had the NTFS drivers to 'see' sda1. It says sda3 is ext3 but if you installed ext4 then the 7.10 would not have drivers for that either.

But script is saying it cannot mount the NTFS & your main Linux partitions. That could be the missing drivers or you need chkdsk on the NTFS partition, and fsck on the Linux partition, or  a failing hard drive.

First try using your XP install disk and run chkdsk on the c: partition.
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

chkdsk c: /r

You really should have a current liveCD of the same verison of Ubuntu has you have installed.

#From liveCD so everything is unmounted,swap off if necessary, change sda3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda3
#if errors:
sudo e2fsck -f -y -v /dev/sda3

I am looking at your post, thanks.

But I have an issue, the Windows XP installation disk I have is not giving an option of repair. It just saw the Windows XP partition as unallocated.

Yes I used the Ubuntu 7.10 Live CD. I think I will look through my archive to use Ubuntu 10 for the next line of action. 
Hope Ubuntu 10 Desktop Edition would be ok since I installed Server Edition initially i.e. 10.04

I am thinking I should use the Testdisk! What do you think. I already have it downloaded on my flash drive.

Thanks and great work helping out.

---

### Post by oldfred on 2011-10-12
I like testdisk for recovering partitions. Yours look ok, but need repair. Teskdisk also has a function to restore backup partition boot sector - PBR or create a new boot sector. If Windows disk is not seeing the c: drive then that may be a problem.

This was for those who installed grub to the PBR but you can use it to check if the PBR or backup PBR are valid.  If backup is valid you then can restore it. 

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

