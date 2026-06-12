---
title: "Dual boot with upgrade of Windows to version 10"
date: 2019-10-16
forum: Installation &amp; Upgrades
---

### Post by Olivares on 2019-10-16
I have dual boot Ubuntu 18.04 and Windows. I have this week done the free upgrade of Windows to version 10. On first attempt, I got the message "we're having trouble determining if your PC can run Windows 10." Advice I found on the internet was to mark the Windows partition as the active partition. I did this, and the upgrade went smoothly. This action had the result that the PC now boots directly into Windows, I have no Ubuntu. I am assuming the thing to do to restore dual boot and the GRUB menu is to make the Ubuntu partition the active partition?

In view of the dire warnings about making sure the partition you have chosen has a boot sector, I want to run this action past wiser heads than me before I go ahead. I attach screenshot of Windows Disk Management GUI, and also Boot Info Summary.

 [ATTACH=CONFIG]284189[/ATTACH]

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda5 
                       and looks at sector 1739221968 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        718,848 1,032,774,772 1,032,055,925   7 NTFS / exFAT / HPFS
/dev/sda3       1,032,775,680 1,033,924,607     1,148,928  27 Hidden NTFS (Recovery Environment)
/dev/sda4       1,033,926,654 1,953,523,711   919,597,058   5 Extended
/dev/sda5       1,033,926,656 1,953,523,711   919,597,056  83 Linux


Drive: sdb _____________________________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 2000.4 GB, 2000398929920 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378645 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   488,378,644   488,376,597   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8AB0215FB021534D                       ntfs       System Reserved
/dev/sda2        C60423FE0423EFDB                       ntfs       
/dev/sda3        BA465CDC465C9AC9                       ntfs       
/dev/sda5        68341cbb-f7b1-4938-a482-e0226c65af12   ext4       
/dev/sdb1        7A5E8C785E8C2F47                       ntfs       Seagate Backup Plus Drive
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       fcce03d2-af3e-403c-83bd-0ec5f234ac46   swap       
/dev/zram1       a5e0d3fc-14c3-43f4-870e-ca23906ec6c1   swap       
/dev/zram2       887850e0-9cfb-47c1-b4de-0abcc1e14e66   swap       
/dev/zram3       79fd4776-c10c-4272-a70f-d1c9d8358351   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 16  2019 ata-HL-DT-ST_DVDRAM_GH24NSB0_K26DBSI3927 -> ../../sr0
lrwxrwxrwx 1 root root  9 Oct 16 03:43 ata-ST1000DM003-1CH162_Z1DA0AHT -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 16 03:44 ata-ST1000DM003-1CH162_Z1DA0AHT-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 16 03:44 ata-ST1000DM003-1CH162_Z1DA0AHT-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 16 03:44 ata-ST1000DM003-1CH162_Z1DA0AHT-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 16  2019 ata-ST1000DM003-1CH162_Z1DA0AHT-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Oct 16  2019 ata-ST1000DM003-1CH162_Z1DA0AHT-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Oct 16 03:43 ata-ST2000DM001-1E6164_Z1E7MY1X -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 16 03:44 ata-ST2000DM001-1E6164_Z1E7MY1X-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 16 03:43 wwn-0x5000c500662d1e72 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 16 03:44 wwn-0x5000c500662d1e72-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 16 03:44 wwn-0x5000c500662d1e72-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 16 03:44 wwn-0x5000c500662d1e72-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 16  2019 wwn-0x5000c500662d1e72-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Oct 16  2019 wwn-0x5000c500662d1e72-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Oct 16 03:43 wwn-0x5000c500667bf901 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 16 03:44 wwn-0x5000c500667bf901-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 16  2019 wwn-0x5001480000000000 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  fb 60 02 eb f0 27 71 e4  40 07 64 4c 16 2f db 7b  |.`...'q.@.dL./.{|
00000010  7a 53 13 83 5d 4f a1 8d  f2 90 02 10 04 80 0c 48  |zS..]O.........H|
00000020  df 5f 7f 82 20 90 07 c0  07 e2 ba 17 d5 ce f1 36  |._.. ..........6|
00000030  d5 ca 85 37 ea 20 40 fa  b7 00 2e f6 04 3f fa af  |...7. @......?..|
00000040  fe e0 ae 39 de 9f 1c a6  81 8f 38 73 7c a4 10 3e  |...9......8s|..>|
00000050  e4 00 c3 7d b9 ef a7 0a  00 77 f4 c1 6f e2 f3 77  |...}.....w..o..w|
00000060  8e ec b9 c3 d3 47 53 b2  b7 92 47 86 37 b2 44 d3  |.....GS...G.7.D.|
00000070  71 bf e7 2f ef 4f e3 de  b8 57 b9 18 4f 5b ae ec  |q../.O...W..O[..|
00000080  43 b5 f0 6e 56 e5 77 a2  b2 01 9c d5 90 3c a1 88  |C..nV.w......<..|
00000090  df 63 04 0f cb 00 30 00  52 e0 0a c4 48 00 fb 6e  |.c....0.R...H..n|
000000a0  4e 78 ef ce cb 0a b9 6c  2e 37 ca 88 f5 fe c2 71  |Nx.....l.7.....q|
000000b0  fd 09 f8 ed d6 b9 fd 6e  2a ac 43 2b 70 f3 96 37  |.......n*.C+p..7|
000000c0  ac ed 97 0b 8d fc de fc  2a 6c a9 a1 a3 43 5b 53  |........*l...C[S|
000000d0  c5 48 ec a7 d0 b1 ad ce  e5 c2 03 ad 9b 94 f5 08  |.H..............|
000000e0  0a 6e 88 bc cc 45 92 16  5c 56 e3 a5 37 4d 6e b3  |.n...E..\V..7Mn.|
000000f0  84 d9 50 26 12 db 3f 22  8a 40 e8 1a 8d a1 fc 3b  |..P&..?".@.....;|
00000100  2c 36 61 49 0f a3 46 b5  02 dd 24 49 eb 07 b4 d6  |,6aI..F...$I....|
00000110  6d 92 53 6d 32 ec 38 b6  a6 d8 61 63 48 6d e8 08  |m.Sm2.8...acHm..|
00000120  fc cb 21 55 47 17 4e 6e  77 65 72 87 06 86 32 ac  |..!UG.Nnwer...2.|
00000130  2b 6c 3c fe 1f 7d 52 c2  87 33 98 ab 0a 1e 12 73  |+l<..}R..3.....s|
00000140  19 7f 05 58 72 9c 51 cd  65 c0 e5 9e 91 6d 52 da  |...Xr.Q.e....mR.|
00000150  99 37 ca ae f3 b3 0f 87  a2 22 c0 86 b3 89 3c ad  |.7......."....<.|
00000160  29 06 20 48 14 c8 f2 df  4c 40 11 48 50 4a b3 79  |). H....L@.HPJ.y|
00000170  6a 69 79 4e 49 61 61 a4  a6 a6 4d f6 14 a1 d1 86  |jiyNIaa...M.....|
00000180  4b b0 9a f0 8b 03 40 e6  ad c6 57 93 02 c3 51 ad  |K.....@...W...Q.|
00000190  e9 d9 b1 56 e9 56 2e c2  8a 3d 9b 53 7d b2 25 a6  |...V.V...=.S}.%.|
000001a0  4d 40 d8 7a 85 b2 3b 77  76 d5 09 0c 53 99 a4 ca  |M@.z..;wv...S...|
000001b0  a5 2d 1e 55 2d 95 d9 f9  2a 5a 4a 6c 98 6e 00 fe  |.-.U-...*ZJl.n..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 cf 36 00 00  |.............6..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

MFT Sector of sdb1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ed ea e1 ff  |................|
00000010  9c 8c 6a ff 7e 6b 3f ff  6a 57 2d ff 59 48 20 ff  |..j.~k?.jW-.YH .|
00000020  4f 3d 16 ff 4a 39 13 ff  4a 38 12 ff 4b 39 14 ff  |O=..J9..J8..K9..|
00000030  50 3e 19 ff 58 45 1f ff  5f 4c 26 ff 63 50 2a ff  |P>..XE.._L&.cP*.|
00000040  64 51 2b ff 64 51 2b ff  61 4e 28 ff 61 4e 29 ff  |dQ+.dQ+.aN(.aN).|
00000050  60 4e 29 ff 60 4e 29 ff  77 67 46 ff a2 93 74 ff  |`N).`N).wgF...t.|
00000060  87 78 52 ff 65 54 2c ff  4d 3d 18 ff 3e 2f 10 ff  |.xR.eT,.M=..>/..|
00000070  37 2a 0f ff 31 26 0e ff  30 24 0d ff 32 26 0f ff  |7*..1&..0$..2&..|
00000080  32 2b 1c ff 20 2d 3a ff  1a 2d 40 ff 28 37 4e ff  |2+.. -:..-@.(7N.|
00000090  4e 63 84 ff 7b 94 c2 ff  8e a7 dc ff 94 ac e0 ff  |Nc..{...........|
000000a0  91 aa dc ff 8e aa de ff  82 a0 d7 ff 74 93 cf ff  |............t...|
000000b0  76 97 d2 ff 79 9b d2 ff  77 98 cd ff 76 95 ca ff  |v...y...w...v...|
000000c0  7c 99 cf ff 84 a0 d5 ff  89 a4 d9 ff 8d aa e0 ff  ||...............|
000000d0  93 b0 e7 ff a3 c1 f8 ff  a9 c6 fb ff ac c7 fc ff  |................|
000000e0  a6 c5 fb ff a5 c4 f9 ff  9f bc f4 ff 9e bb f3 ff  |................|
000000f0  97 b4 eb ff 8e ab e2 ff  8e aa e1 ff 92 af e5 ff  |................|
00000100  8d ac e3 ff 84 a4 de ff  7b 9a d6 ff 7a 98 d1 ff  |........{...z...|
00000110  87 a5 db ff 8c a8 dc ff  8b a8 e0 ff 7a 99 d0 ff  |............z...|
00000120  4b 64 8e ff 20 33 4e ff  1a 2d 43 ff 1e 25 30 ff  |Kd.. 3N..-C..%0.|
00000130  50 46 34 ff 69 58 34 ff  7a 6a 49 ff 9e 90 72 ff  |PF4.iX4.zjI...r.|
00000140  a6 99 7e ff a3 97 7e ff  b0 a4 89 ff a2 94 72 ff  |..~...~.......r.|
00000150  7c 6b 42 ff 5a 4a 22 ff  45 36 16 ff 47 3a 21 ff  ||kB.ZJ".E6..G:!.|
00000160  65 56 38 ff 72 60 40 ff  72 61 40 ff 76 65 44 ff  |eV8.r`@.ra@.veD.|
00000170  80 71 50 ff 9e 92 74 ff  ae a1 88 ff a6 98 7a ff  |.qP...t.......z.|
00000180  7f 6e 48 ff 5f 4e 24 ff  70 66 4d ff ce cf cb ff  |.nH._N$.pfM.....|
00000190  d6 da d9 ff cb cf cf ff  ba c0 c0 ff 9b a1 a2 ff  |................|
000001a0  61 63 6b ff 2d 2f 3b ff  1e 25 3b ff 26 33 51 ff  |ack.-/;..%;.&3Q.|
000001b0  27 36 59 ff 29 3d 66 ff  28 3e 70 ff 43 61 9b ff  |'6Y.)=f.(>p.Ca..|
000001c0  5c 7c b7 ff 57 70 ae ff  70 8e cd ff 71 90 d0 ff  |\|..Wp..p...q...|
000001d0  72 8f cf ff 67 83 c4 ff  68 86 c8 ff 5d 7d c1 ff  |r...g...h...]}..|
000001e0  4b 6c b2 ff 4e 71 b7 ff  50 72 b7 ff 47 64 9d ff  |Kl..Nq..Pr..Gd..|
000001f0  2e 46 74 ff 3b 4f 81 ff  2d 3e 6b ff 1a 26 44 ff  |.Ft.;O..->k..&D.|
00000200

=============================== StdErr Messages: ===============================

ERROR: unsupported sector size 4096 on /dev/sdb.
ERROR: unsupported sector size 4096 on /dev/sdb.
hexdump: u: bad byte count
/usr/share/boot-sav/bis.sh: line 1746: [: -eq: unary operator expected
cat: write error: Broken pipe
File descriptor 9 (/proc/3117/mounts) leaked on lvs invocation. Parent PID 11189: bash
File descriptor 63 (pipe:[27440]) leaked on lvs invocation. Parent PID 11189: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2019-10-16__03h43 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
ERROR: unsupported sector size 4096 on /dev/sdb.
ERROR: unsupported sector size 4096 on /dev/sdb.
ERROR: unsupported sector size 4096 on /dev/sdb.
ERROR: unsupported sector size 4096 on /dev/sdb.
ERROR: unsupported sector size 4096 on /dev/sdb.
ERROR: unsupported sector size 4096 on /dev/sdb.
File descriptor 9 (/proc/3117/mounts) leaked on lvs invocation. Parent PID 4786: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount -r /dev/sda5 : Error code 32
Unmount sdb1 from /media/lubuntu/Seagate Backup Plus Drive to avoid space incompatibilities

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda1:Windows 8 (loader):Windows:chain
/dev/sda2:Windows 8 (loader):Windows1:chain
/dev/sda5:Ubuntu 18.04.3 LTS (18.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="8AB0215FB021534D" TYPE="ntfs"
/dev/sda2: UUID="C60423FE0423EFDB" TYPE="ntfs"
/dev/sda3: UUID="BA465CDC465C9AC9" TYPE="ntfs"
/dev/sda5: UUID="68341cbb-f7b1-4938-a482-e0226c65af12" TYPE="ext4"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sdb1: LABEL="Seagate Backup Plus Drive" UUID="7A5E8C785E8C2F47" TYPE="ntfs"
/dev/zram0: UUID="fcce03d2-af3e-403c-83bd-0ec5f234ac46" TYPE="swap"
/dev/zram1: UUID="a5e0d3fc-14c3-43f4-870e-ca23906ec6c1" TYPE="swap"
/dev/zram2: UUID="887850e0-9cfb-47c1-b4de-0abcc1e14e66" TYPE="swap"
/dev/zram3: UUID="79fd4776-c10c-4272-a70f-d1c9d8358351" TYPE="swap"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

mount -r /dev/sda5 : Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size   Type      File system  Flags
1      1049kB  368MB   367MB  primary   ntfs
2      368MB   529GB   528GB  primary   ntfs         boot
3      529GB   529GB   588MB  primary   ntfs         diag
4      529GB   1000GB  471GB  extended
5      529GB   1000GB  471GB  logical   ext4


Model: Seagate Backup+ Desk (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      8389kB  2000GB  2000GB  primary               boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA ST1000DM003-1CH1;
1:1049kB:368MB:367MB:ntfs::;
2:368MB:529GB:528GB:ntfs::boot;
3:529GB:529GB:588MB:ntfs::diag;
4:529GB:1000GB:471GB:::;
5:529GB:1000GB:471GB:ext4::;

BYT;
/dev/sdb:2000GB:scsi:4096:4096:msdos:Seagate Backup+ Desk;
1:8389kB:2000GB:2000GB:::boot;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  4d 53 21 b0 5f 21 b0 8a  |........MS!._!..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f8 0a 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  74 ec 83 3d 00 00 00 00  |........t..=....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  db ef 23 04 fe 23 04 c6  |..........#..#..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 e8 8e 3d  |........?......=|
00000020  00 00 00 00 80 00 80 00  ff 87 11 00 00 00 00 00  |................|
00000030  00 bb 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c9 9a 5c 46 dc 5c 46 ba  |..........F.F.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 10 01 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  14 09 1c 1d 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  01 00 00 00 01 00 00 00  47 2f 8c 5e 78 8c 5e 7a  |........G/.^x.^z|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.4G  7.2M  3.4G   1% /
udev           devtmpfs   3.4G   12K  3.4G   1% /dev
tmpfs          tmpfs      684M  1.3M  683M   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.4G  8.0K  3.4G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.4G     0  3.4G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    350M  258M   93M  74% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    493G  205G  288G  42% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    561M  475M   87M  85% /mnt/boot-sav/sda3
/dev/sdb1      fuseblk    1.9T  759G  1.1T  41% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1f9c02ef

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2   *      718848  1032774772   516027962+   7  HPFS/NTFS/exFAT
/dev/sda3      1032775680  1033924607      574464   27  Hidden NTFS WinRE
/dev/sda4      1033926654  1953523711   459798529    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1033926656  1953523711   459798528   83  Linux
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 2000.4 GB, 2000398929920 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9a8aa40c

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   488378644  1953506388    7  HPFS/NTFS/exFAT




=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2019-10-16
Please use code tags on longer terminal output.
With Boot-Repair better to just post link it provides to pastebin site.

Windows always requires boot flag on the primary NTFS partition with its boot files when in BIOS boot mode.
But it looks like you had installed grub to a PBR partition boot record, and used the Windows boot loader to chain to the partition (sda5) with grub. Grub2 does not recommend installing to a PBR, just to MBR in BIOS boot mode.

Report says you have gpt data on drive. I thought Ubuntu would not install in first place with mixed MBR & gpt as Linux tools see both MBR and backup gpt and do not know which you really have.
If you install Windows in BIOS boot mode to a gpt drive it incorrectly converts to MBR, by leaving backup gpt partition at end of drive. 
To fully convert to MBR:

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

You may also need to run fsck on the Linux partition.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

With Windows 10 you must make sure fast start up is off. Grub only boots working Windows and if hibernation flag is set grub will not boot it.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Then you can use Boot-Repair to install grub to MBR.

Windows 10 is not particularly easy to dual boot in BIOS mode. It turns fast start up back on and then grub will not boot it. You have to temporarily restore Windows boot loader, fix Windows, & then restore grub. With UEFI, you can always directly boot Windows from UEFI boot menu to make repairs.

So always have a Windows repair flash drive & your Ubuntu live installer. If upgrades upgrade your repair flash drives also.
Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by Olivares on 2019-10-17
I ran fixparts and e2fsck commands as recommended, and ensured fast start up in Windows is turned off, but still no GRUB menu. Here is a screenshot from live DVD:
[ATTACH=CONFIG]284197[/ATTACH]

Here is latest boot info summary: [http://paste.ubuntu.com/p/DD2Yfkrc55/](http://paste.ubuntu.com/p/DD2Yfkrc55/) 

Where did I go wrong?

---

### Post by oldfred on 2019-10-17
Pastebin not working.

Is this a Mac? It says partition table is a Mac.
Do not know difference with Mac and gpt.

---

### Post by Olivares on 2019-10-17
Please ignore my previous message. My issue is now resolved. When I ran boot repair before, I failed to set partition booted by MBR to the Ubuntu partition.

---

