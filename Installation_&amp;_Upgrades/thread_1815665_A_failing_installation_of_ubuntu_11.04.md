---
title: "A failing installation of ubuntu 11.04"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by hagai on 2011-07-31
Hello, I'm runing ubuntu 11.04 from the LIVECD in order to write this lines.

      I had a previous version (9.04) of ubuntu aside with Windows7 installed.
      Yesterday I downloaded 11.04 and ran the installation. I chose to  install ubuntu on the same partition where the 9.04 was installed.
      I marked to format this partition and create an ext3 file system on it.
      The installation then failed with the error: "The ext3 file system creation in partition #6 of SCSI(0,0,0) (sda) failed.
      Then I had to restart, but GRUB menu disappeared showing only ERROR 17.
      I tried to run the installation again but keep getting this error. I  tried several guides on the internet to restore GRUB with no success.
      Now when I try to run the installation again, I can't continue as it  claims I dont have 4.4GB drive space available. ofcourse this is not  true,
      as I have an empty partition of 40GB and another 8GM swap space.
      Be happy to get any help here.
      Thanks.

---

### Post by YesWeCan on 2011-07-31
Hi there. It would help if you would download and run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.txt here, inside code tags (highlight text and click the #)

---

### Post by hagai on 2011-07-31
Hi, here is content of RESULTS.txt :

```
                                    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: __________________________________________________________________________

    File system:
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdb1: __________________________________________________________________________
   File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 8224 of /dev/sdb1 for its
                       second stage. SYSLINUX is installed in the  directory.
                       The integrity check of the ADV area failed. No errors
                       found in the Boot Parameter Block.
    Operating System:
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    20,561,919    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     20,561,920   388,148,079   367,586,160   7 NTFS / exFAT / HPFS
/dev/sda4         388,149,246   488,394,751   100,245,506   f W95 Extended (LBA)
/dev/sda5         483,155,968   488,394,751     5,238,784  dd Dell Media Direct
/dev/sda6         388,149,248   466,272,255    78,123,008  83 Linux
/dev/sda7         466,274,304   483,153,919    16,879,616  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        07D7-0615                              vfat       DellUtility
/dev/sda2        AAB6D921B6D8EEB7                       ntfs       RECOVERY
/dev/sda3        2C6EDB496EDB0B0A                       ntfs       OS
/dev/sda5        4A0D-C5F3                              vfat       MEDIADIRECT
/dev/sda7        e50ab387-deef-4a8c-84ab-e341d3d748cb   swap
/dev/sdb1        F83A-5F17                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line w$
# ui gfxboot bootlogo
--------------------------------------------------------------------------------
================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 26 18  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 60 cc 1c  |........?....`..|
00000020  00 f0 4f 00 ed 13 00 00  00 00 00 00 02 00 00 00  |..O.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f3 c5 0d 4a 44  65 6c 6c 4d 44 33 70 6c  |..)...JDellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
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


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected




```

Thing is anytime I try to create ext(2/3) file system on sda6, it fails. I tried to do this using the ubuntu installer and Gparted with no success.
I still didnt manage to load GRUB, and having only this LIVECD internet access. still cant access Windows7.

---

### Post by YesWeCan on 2011-07-31
Ok. It looks to me like your attempt to install 11.04 caused your 9.04 partition (sda6) to be trashed. This is why Grub no longer works because it relied on files in your 9.04 partition.

Others may have other approaches but I would boot live CD and run GParted and delete sda6 and recreate it. To make sure that it exists with a proper format and no errors. Look at GParted for any warning icons and right click them to read what the warning is.

Why did you choose ext3 for it? Ext4 is normal.

Once you have a valid partition for sda6, then try installing 11.04 there. Make sure that you install a new Grub to the MBR (/dev/sda) because your existing Grub will not work with the new Grub files in your 11.04 /boot/grub directory.

---

### Post by hagai on 2011-08-01
Hi,
I managed to create ext3 file system on dev/sda6.
I also created a 8GB swap space.
I mistakenly told the installer to import files from Windows.
Now I have all my data duplicated.
- Is there a way to remove this?
- Should I remove ubuntu and install again in an ext4 file system, this time without importing anything?

Note that I now have a new GRUB which looks nicer than the old one,
Anyway GRUB is back!

Thank you very much for your help!

---

### Post by YesWeCan on 2011-08-03
Hi, sorry for my slow reply.
Glad you got it working.
ext3 is fine. ext4 has some speed improvements if you have lots of large files and some other improvements. I wouldn't reinstall just for ext4.

Don't forget to mark this as solved in [COLOR="Red"]thread tools[/COLOR].

---

