---
title: "Ubuntu Partition Table Inconsistent With Windows table"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by LukeLinux on 2011-12-16
Boy, this one really has me stumped.

So I've installed various flavors of linux dozens of times, but I've never seen the likes of this before. Earlier in the year, I had Ubuntu installed on my Asus 1201N netbook and running great, but I decided to be adventurous and try a hackintosh for a while. It didn't take long for me to figure out that I hated OSX, so I formatted the whole drive and reinstalled my copy of Windows 7 and a bit later, added the Windows 8 developer preview to the mix. Now I want to install Ubuntu again as well. So I boot into Windows and shrink Windows 7's disk to create 1GB for swap space and 20GB for Ubuntu. All appears well as seen in the screenshot below.

[[IMG]http://i.imgur.com/EQdtOm.jpg[/IMG]]("http://i.imgur.com/EQdtO.jpg")
*(Click screenshots for full resolution image)*

But then I reboot and start the Ubuntu installation off of my USB drive, begin the installation, and the partition table is way out of date! What the heck?

[[IMG]http://i.imgur.com/wJ0Y8m.png[/IMG]]("http://i.imgur.com/wJ0Y8.png")

I _***completely***_ formatted the drive to get rid of OSX, yet somehow there it is, and the darned hfs+ drive actually mounts and still has all my files on it--and they're readable! :confused: The Win7 partition listed there is not readable at all, however, and Windows 8 is nowhere to be found, nor is my newly created free space, nor...well *anything* that is supposed to show up there! So now I can't install Ubuntu to my netbook because it can't see the partition table in its current state.

Like I said...what the heck?!

Any idea how to correct this problem so Ubuntu can read my disk properly?

---

### Post by fantab on 2011-12-16
Was your netbook primarily a mac system? Did it have BIOS or EFI? If it was BIOS, I am afraid that Hackintosh messed with your BIOS firmware.

Your problem has everything to do with Gparted view /dev/sda1, EFI. **[See here]("https://help.ubuntu.com/community/UEFIBooting")** for more info.

**Edit**: I think you may have to revert back to BIOS, **[see here]("http://support.asus.com/Download.aspx?SLanguage=en&m=Eee+PC+1201N&p=20&s=1")**. Before that you have to delete all partitions and recreate partition table and partitions using **[Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php")**.

*Before you jump into troubleshooting I suggest you wait for someone to address this here more authoritatively.*

---

### Post by oldfred on 2011-12-17
We need to know if you are gpt or part gpt & part MBR.

This does not parse efi partitions, but will document most of your system.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"


Your partition table maybe gpt. You can revert back to MBR(msdos), but it looks like your Windows install saw gpt, and if you have UEFI, it will install in UEFI mode. The first partition is then the efi partition. Or Windows saw BIOS &  ignored the gpt and installed to MBR partitions and created a hybrid.

Macs do install a hybrid MBR/gpt system that then can cause major issues if they get out of sync. Windows is in the MBR part, the Mac is in the gpt part and only the first three gpt partitions are also MBR, if that even makes sense.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx)

If you are going to erase the gpt info you have to use gdisk. 

Info on converting:
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

Before erasing anything also post these which is a bit more info that boot script will not show. You will have to install gdisk from synaptic or download it from rodbooks site.
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sda

---

### Post by LukeLinux on 2011-12-17
This is some good info! Thanks for the reply. :)

Here's my Results file:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 has 
                       339085311 sectors, but according to the info from 
                       fdisk, it has 332146687 sectors.
    Mounting failed:   Failed to read last sector (339085311): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (339085311): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sda3: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        /etc/fstab

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 15420 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        411,648   339,496,959   339,085,312   7 NTFS / exFAT / HPFS
/dev/sda3         339,496,960   383,537,151    44,040,192   f W95 Extended (LBA)
Empty Partition.
/dev/sda4         383,537,152   488,394,751   104,857,600   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         411,648   332,558,335   332,146,688 Data partition (Windows/Linux)
/dev/sda3     332,558,336   488,134,983   155,576,648 Hierarchical File System Plus (HFS+) partition (Mac OS X)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        70D6-1701                              vfat       EFI
/dev/sda2        F004CB3904CB0218                       ntfs       Win7
/dev/sda3        7c3a4a01-cec2-3f91-b867-3f0cf1214a3a   hfsplus    OSX
/dev/sdb         1716-472E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
UUID=858E85DE-CB4E-4F33-9025-980CF2D927CD none ntfs rw
--------------------------------------------------------------------------------

=========================== sdb/boot/grub/grub.cfg: ============================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================== sdb/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

==================== sdb: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 01 17 d6 70 45  46 49 20 20 20 20 20 20  |..)...pEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda3

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf ed  e1 e8 6a 00 8a 16 04 e6  |.|h.N.....j.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5b 00 f4 eb fd 66 60  |.... ....[....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 52 31 d2 66 c1 ea 04  |.fa.f`...R1.f...|
000000f0  8e c2 5b 1e 1e 66 03 0e  00 e6 66 51 06 53 30 e4  |..[..f....fQ.S0.|
00000100  50 68 10 00 8a 16 04 e6  89 e6 b4 42 cd 13 72 a5  |Ph.........B..r.|
00000110  89 ec 07 66 61 c3 66 60  57 be dd e3 e8 07 00 5e  |...fa.f`W......^|
00000120  e8 03 00 66 61 c3 bb 01  00 ac 3c 00 74 06 b4 0e  |...fa.....<.t...|
00000130  cd 10 eb f5 c3 66 60 ad  86 e0 ab 3c 00 74 23 89  |.....f`....<.t#.|
00000140  c1 ad 86 e0 80 3e 01 e4  58 74 14 09 c0 75 01 48  |.....>..Xt...u.H|
00000150  80 fc 00 77 0a 3c 41 72  06 3c 5a 77 02 04 20 ab  |...w.<Ar.<Zw.. .|
00000160  e2 df 66 61 c3 66 60 b2  00 66 8b 44 02 66 3b 45  |..fa.f`..f.D.f;E|
00000170  02 75 0f 80 3c 00 75 0a  66 8b 44 06 66 3b 45 06  |.u..<.u.f.D.f;E.|
00000180  74 48 77 44 72 3d 66 60  31 d2 87 f7 66 ad 66 89  |tHwDr=f`1...f.f.|
00000190  c1 87 f7 66 ad 66 39 c8  77 2e 72 27 87 f7 ad 89  |...f.f9.w.r'....|
000001a0  c1 87 f7 ad 80 f9 00 74  1f 39 c8 74 0b 77 07 fe  |.......t.9.t.w..|
000001b0  ce 89 c1 e9 02 00 fe c6  f3 a7 77 0c 72 05 88 f2  |..........w.r...|
000001c0  e9 07 00 fe ca e9 02 00  fe c2 88 96 14 00 80 fa  |................|
000001d0  00 66 61 c3 50 57 8b 3e  0a e6 57 47 47 49 49 b0  |.fa.PW.>..WGGII.|
000001e0  00 f3 aa 89 3e 0a e6 5d  89 2d 5f 58 c3 2f 62 6f  |....>..].-_X./bo|
000001f0  6f 74 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |ot............U.|
00000200



```

to my surprise, dmesg | grep EFI returned:

```
[        9.717166] EFI Variables Facility v0.08 2004-May-17
```

but then find /boot/efi -name "*efi" returned:

```
find: '/boot/efi': No such file or directory
```

So...it's installed, but it's not installed. Terrific.

Of course since Mac OSX won't boot off of a BIOS, I had to format my disk and set it up as GPT with EFI (though I don't believe this was a 'true' EFI...more like an EFI that sat on top of the BIOS, but I could be way off on that), but when I was done with OSX I formatted all that and I'm inclined to believe Windows is really booting off of the BIOS, because it no longer displays the "booting off GPT" message it did while running from the EFI/GPT setup, not to mention that just now I also had to set up an extended partition to make room for Ubuntu, which would only be necessary with an MBR/BIOS setup.

>  Or Windows saw BIOS &  ignored the gpt and installed to MBR partitions and created a hybrid.

You know what...I think that may be exactly what happened :shock:

> Macs do install a hybrid MBR/gpt system that then can cause major issues if they get out of sync. Windows is in the MBR part, the Mac is in the gpt part and only the first three gpt partitions are also MBR, if that even makes sense.

Yes, it makes sense, but _none_ of my partitions are in sync between MBR/GPT. The table looks just like it did six months ago or so from Ubuntu's perspective.

> 
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx)

Thank you for those links; very helpful for understanding what's going on.

> Before erasing anything also post these which is a bit more info that boot script will not show.

sudo parted /dev/sda unit s print
```
Model: ATA WDC WD2500BEVT-8 (scsi)
Disk /dev/sda: 488397168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start       End         Size        File system  Name                  Flags
 1      40s         409639s     409600s     fat32        EFI System Partition  boot
 2      411648s     332558335s  332146688s  ntfs         SEVEN
 3      332558336s  488134983s  155576648s  hfs+         OSX
```

sudo sfdisk -l -uS
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             1    409639     409639  ee  GPT
        start: (c,h,s) expected (0,0,2) found (1023,254,63)
        end: (c,h,s) expected (25,127,14) found (1023,254,63)
/dev/sda2   *    411648 339496959  339085312   7  HPFS/NTFS/exFAT
/dev/sda3     339496960 383537151   44040192   f  W95 Ext'd (LBA)
/dev/sda4     383537152 488394751  104857600   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1012 cylinders, 63 heads, 62 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   ? 3224498923 3657370039  432871117   7  HPFS/NTFS/exFAT
        start: (c,h,s) expected (1023,62,62) found (187,180,14)
        end: (c,h,s) expected (1023,62,62) found (784,0,13)
/dev/sdb2   ? 3272020941 5225480974 1953460034  16  Hidden FAT16
        start: (c,h,s) expected (1023,62,62) found (906,235,61)
        end: (c,h,s) expected (1023,62,62) found (262,116,59)
/dev/sdb3   ?         0         -          0  6f  Unknown
/dev/sdb4      50200576 974536369  924335794   0  Empty
        start: (c,h,s) expected (1023,62,62) found (0,0,0)
        end: (c,h,s) expected (1023,62,62) found (0,0,0)

Disk /dev/sdc: 1021 cylinders, 8 heads, 62 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   ? 778135908 1919645538 1141509631  72  Unknown
        start: (c,h,s) expected (1023,7,62) found (357,116,40)
        end: (c,h,s) expected (1023,7,62) found (357,32,45)
/dev/sdc2   ? 168689522 2104717761 1936028240  65  Novell Netware 386
        start: (c,h,s) expected (1023,7,62) found (288,115,43)
        end: (c,h,s) expected (1023,7,62) found (367,114,50)
/dev/sdc3   ? 1869881465 3805909656 1936028192  79  Unknown
        start: (c,h,s) expected (1023,7,62) found (366,32,33)
        end: (c,h,s) expected (1023,7,62) found (357,32,43)
/dev/sdc4   ? 2885681152 2885736650      55499   d  Unknown
        start: (c,h,s) expected (1023,7,62) found (372,97,50)
        end: (c,h,s) expected (1023,7,62) found (0,10,0)
```

sudo gdisk -l /dev/sda
```
GPT fdisk (gdisk) version 0.8.1

Warning! MBR Logical partitions found on a hybrid MBR disk! This is an
EXTREMELY dangerous configuration!
Warning! MBR Logical partitions found on a hybrid MBR disk! This is an
EXTREMELY dangerous configuration!
Warning! MBR Logical partitions found on a hybrid MBR disk! This is an
EXTREMELY dangerous configuration!
Warning! MBR Logical partitions found on a hybrid MBR disk! This is an
EXTREMELY dangerous configuration!
Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): BF3F6E10-8046-4774-89E6-AAE2E7B4BE1E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 8-sector boundaries
Total free space is 264165 sectors (129.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          411648       332558335   158.4 GiB   0700  SEVEN
   3       332558336       488134983   74.2 GiB    AF00  OSX

```

Darn, it _***is***_ a hybrid! Shall I move forward with FixParts, or no? I'd really like to go back to just a normal MBR/BIOS since that's my netbook's stock configuration, but I'd also like to avoid completely formatting again, if I can.

Thanks again for all your help!

---

### Post by oldfred on 2011-12-17
I was a little surprised that boot script showed two different layouts for sda. It showed both the msdos & the gpt.

The gdisk output confirms you have the hybrid and you need to follow the steps from the rodbooks site to fix it. I never have had a hybrid and it would always be best to have good backups as who knows what will happen.  But fixparts was set up to fix partition table issues and I have not heard any issues with it.

gpt is the newer partition table structure over the 35-40 year old MBR(msdos). With gpt all partitions are primary and it has a backup of the table. That backup is what is confusing some software as it is not as gpt aware or does not delete the backup so other software then sees backup and uses it. Windows installs of BIOS versions just overwrite the first gpt info creating the issue you have. I think one or two others have posted similar issues.

I do not use Windows on most of my drives. I am keeping MBR on my old XP drive and used gpt for two Linux only drives. My large MBR drive I am debating converting to gpt. I am still BIOS but am leaving both space for efi & bios_grub partitions (only one used) on my gpt drives so when I get a new UEFI system the drives will work without major reconfiguration.

Windows does seem to install without any issues in UEFI systems with gpt, but grub has some issues that have not been resolved. Some of the issues may be UEFI/BIOS that motherboard mfg. have really only set up and tested to work with Windows. Some have reported success with grub2 but had to do some work arounds to fix it.

---

### Post by LukeLinux on 2011-12-17
Well, it looks like I got myself royally buggered on this one. FixParts couldn't do anything because it determined my disk was GPT, not an MBR with some GPT leftovers, and while GPT Fdisk was able to clear up some minor glitches, it still didn't solve the problem, and attempting to convert the disk from GPT to MBR just resulted in an unbootable netbook.

Guess I'm going to have to format after all. :(

Oh well. This has been an educational experience at least, and I'm sure I'll know how to run a cleaner system from here on out! Thanks for all your help.

---

