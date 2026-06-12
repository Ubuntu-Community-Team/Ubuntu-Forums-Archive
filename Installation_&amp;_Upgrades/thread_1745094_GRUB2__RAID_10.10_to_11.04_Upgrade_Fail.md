---
title: "GRUB2 / RAID 10.10 to 11.04 Upgrade Fail"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by sunshinelock on 2011-04-30
I previously posted this here:

[http://ubuntuforums.org/showthread.php?p=10747089#post10747089](http://ubuntuforums.org/showthread.php?p=10747089#post10747089)

I realize the title didn't reflect the true problem.  (I have since determined this is probably a GRUB2 / RAID issue.)

So, just a rundown on that previous thread:

I have an AMD64 with 4 hard drives, of which we have 2 RAID settings so it's more like 2 hard drives.

I have searched a few posts the last 3 hours or so and have not had any success.

I tried this:

```
sudo mkdir /media/fix
sudo mount /dev/sde1 /media/fix
sudo chroot /media/fix su
```And it's at that point I get an error

```
chroot: failed to run command `su': No such file or directory
ubuntu@ubuntu:~$ 
```So, I did this:

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="promise_fasttrack_raid_member" 
/dev/sdb: TYPE="promise_fasttrack_raid_member" 
/dev/sdc: TYPE="promise_fasttrack_raid_member" 
/dev/sdd: TYPE="promise_fasttrack_raid_member" 
/dev/mapper/pdc_cdajibgfhj1: LABEL="Windows 7" UUID="5A99662B8FE00B1F" TYPE="ntfs" 
/dev/mapper/pdc_cdajibgfhj2: LABEL="Double Backed Up" UUID="CE22E72322E70EF1" TYPE="ntfs" 
/dev/sde1: LABEL="PENDRIVE" UUID="604F-4A66" TYPE="vfat" 
```I'm not sure what that is supposed to get me, but I posted it for info purposes.

I have also run this:

```
ubuntu@ubuntu:~$ sudo bash Downloads/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sde...
Computing Partition Table of /dev/mapper/pdc_cdajibgfhj...
Searching sde1 for information... 
Searching pdc_cdajibgfhj1 for information... 
Searching pdc_cdajibgfhj2 for information... 
RAID set "pdc_cdgaabhbff" is not active
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Downloads
```That gave me a RESULTS.txt file like this:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/mapper/pdc_cdajibgfhj

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

pdc_cdajibgfhj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

pdc_cdajibgfhj2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32    15,625,215    15,625,184   b W95 FAT32


Drive: pdc_cdajibgfhj ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cdajibgfhj: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cdajibgfhj1   *          2,048   987,545,599   987,543,552   7 HPFS/NTFS
/dev/mapper/pdc_cdajibgfhj2        987,545,600 1,953,120,255   965,574,656   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cdajibgfhj1 5A99662B8FE00B1F                       ntfs       Windows 7                     
/dev/mapper/pdc_cdajibgfhj2 CE22E72322E70EF1                       ntfs       Double Backed Up              
/dev/mapper/pdc_cdajibgfhj: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc                                                promise_fasttrack_raid_member                               
/dev/sdd                                                promise_fasttrack_raid_member                               
/dev/sde1        604F-4A66                              vfat       PENDRIVE                      
/dev/sde: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_cdajibgfhj
pdc_cdajibgfhj1
pdc_cdajibgfhj2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde1/boot/grub/grub.cfg: ===========================


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

=================== sde1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 6b ee 00 7e 3b 00 00  00 00 00 00 02 00 00 00  |.k..~;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 66 4a 4f 60 4e  4f 20 4e 41 4d 45 20 20  |..)fJO`NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 20  77 98 00 66 ba 00 00 00  |..E}.f. w..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
```

I tried restarting in safe mode (I know it's actually called something else but can't remember what at the moment) and after a few moments it says something about an MSI quirk.  I hit enter and it eventually gets me to this prompt:

```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/d2be8a74-9bea-4bei-9915-bf98bcee5521 does not exist.

Dropping to a shell
```

The setparams I have deleted the line that has "search" on it and changed the drive to /dev/sdc1 and added a rootdelay like so:

```
recordfail
set gfxpayload_$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(hd4,msdos2)'
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdc1 ro quiet spash vt.handoff=7 rootdelay=130
initrd /boot/initrd.img-2.6.38-8-generic
```

That gets me this:

```

error: hd4 cannot get C/H/S values
error: you need to load the kernel first
```

More info:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc694342

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       61472   493771776    7  HPFS/NTFS
/dev/sdb2           61472      121577   482787328    7  HPFS/NTFS

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc694342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       61472   493771776    7  HPFS/NTFS
/dev/sda2           61472      121577   482787328    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf49d456

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2232    17920000   82  Linux swap / Solaris
/dev/sdc2            2232        3443     9728000   83  Linux
/dev/sdc3            3443      121577   948911104   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf49d456

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2232    17920000   82  Linux swap / Solaris
/dev/sdd2            2232        3443     9728000   83  Linux
/dev/sdd3            3443      121577   948911104   83  Linux

Disk /dev/dm-0: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc694342

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       61472   493771776    7  HPFS/NTFS
/dev/dm-0p2           61472      121577   482787328    7  HPFS/NTFS

Disk /dev/dm-1: 505.6 GB, 505622298624 bytes
255 heads, 63 sectors/track, 61471 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 494.4 GB, 494374223872 bytes
255 heads, 63 sectors/track, 60104 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sde: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders
Units = cylinders of 3040 * 512 = 1556480 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        5140     7812592    b  W95 FAT32
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ ls -l /dev/mapper
total 0
crw------- 1 root root 10, 236 2011-04-30 11:06 control
lrwxrwxrwx 1 root root       7 2011-04-30 15:45 pdc_cdajibgfhj -> ../dm-0
lrwxrwxrwx 1 root root       7 2011-04-30 11:06 pdc_cdajibgfhj1 -> ../dm-1
lrwxrwxrwx 1 root root       7 2011-04-30 11:06 pdc_cdajibgfhj2 -> ../dm-2
```
```
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   3963976    131568   3832408   4% /
none                   3922924       720   3922204   1% /dev
/dev/sde1              7797344    714988   7082356  10% /cdrom
/dev/loop0              680704    680704         0 100% /rofs
none                   3963976       112   3963864   1% /dev/shm
tmpfs                  3963976        28   3963948   1% /tmp
none                   3963976        92   3963884   1% /var/run
none                   3963976         4   3963972   1% /var/lock
/dev/dm-2            482787324  19632612 463154712   5% /media/Double Backed Up
/dev/dm-1            493771772  42603828 451167944   9% /media/Windows 7

```

I'm 90% certain that my home disk was in sdc2 (sdd2 -RAID).  sdc1 was my swap.

So, from this thread, [http://ubuntuforums.org/showthread.php?t=1611213](http://ubuntuforums.org/showthread.php?t=1611213) post #6 I decide to do this:

```
sudo mount /dev/sdc2 /mnt sudo grub-install --root-directory=/mnt /dev/sdc
```

(instead of the sdb1 and sdb as in the original thread)

But the first line throws an error:
```

ubuntu@ubuntu:~$ sudo mount /dev/sdc2 /mnt
mount: special device /dev/sdc2 does not exist
```

And that's where I'm at still.

Checking another thread and it suggested posting the result of dmesg:

```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- BOOT_IMAGE=/casper/vmlinuz 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000093400 (usable)
[    0.000000]  BIOS-e820: 0000000000093400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf810000 (usable)
[    0.000000]  BIOS-e820: 00000000bff70000 - 00000000bff88000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff88000 - 00000000bffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffd0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M/USB3, BIOS 0901    09/06/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000240000000 aka 9216M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf810 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf810000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00bf800000 page 2M
[    0.000000]  00bf800000 - 00bf810000 page 4k
[    0.000000] kernel direct mapping tables up to bf810000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000230000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ bf80e000-bf810000
[    0.000000] RAMDISK: 7f2bf000 - 7ffff000
[    0.000000] ACPI: RSDP 00000000000fb570 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bff70100 0005C (v01 090610 XSDT1403 20100906 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bff70290 000F4 (v03 090610 FACP1403 20100906 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bff70450 0EE8F (v01  A1642 A1642001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bff88000 00040
[    0.000000] ACPI: APIC 00000000bff70390 0007C (v01 090610 APIC1403 20100906 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bff70410 0003C (v01 090610 OEMMCFG  20100906 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bff88040 00072 (v01 090610 OEMB1403 20100906 MSFT 00000097)
[    0.000000] ACPI: SRAT 00000000bff7f8a0 00108 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000bff7f9b0 00038 (v01 090610 OEMHPET  20100906 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bff7f9f0 00DA4 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x04 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x05 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-c0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-240000000
[    0.000000] SRAT: Node 0 [0,a0000) + [100000,c0000000) -> [0,c0000000)
[    0.000000] SRAT: Node 0 [0,c0000000) + [100000000,240000000) -> [0,240000000)
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Initmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [000000022fffb000 - 000000022fffffff]
[    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880228200000-ffff88022effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000093
[    0.000000]     0: 0x00000100 -> 0x000bf810
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2029459
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3909 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 766024 pages, LIFO batch:31
[    0.000000]   Normal zone: 17024 pages used for memmap
[    0.000000]   Normal zone: 1228160 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: IOAPIC (id[0x06] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 6, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 0000000000094000
[    0.000000] PM: Registered nosave memory: 0000000000094000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf810000 - 00000000bff70000
[    0.000000] PM: Registered nosave memory: 00000000bff70000 - 00000000bff88000
[    0.000000] PM: Registered nosave memory: 00000000bff88000 - 00000000bffd0000
[    0.000000] PM: Registered nosave memory: 00000000bffd0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3fa00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800bf200000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1998093
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- BOOT_IMAGE=/casper/vmlinuz 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ b4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ b4000000
[    0.000000] PM: Registered nosave memory: 00000000b4000000 - 00000000b8000000
[    0.000000] Memory: 7845852k/9175040k available (5940k kernel code, 1057204k absent, 271984k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:728 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 81264640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3012.700 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6025.40 BogoMIPS (lpj=30127000)
[    0.000056] pid_max: default: 32768 minimum: 301
[    0.000096] Security Framework initialized
[    0.000131] AppArmor: AppArmor initialized
[    0.000157] Yama: becoming mindful.
[    0.000687] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.011391] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012333] Mount-cache hash table entries: 256
[    0.012447] Initializing cgroup subsys ns
[    0.012474] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.012504] Initializing cgroup subsys cpuacct
[    0.012532] Initializing cgroup subsys memory
[    0.012563] Initializing cgroup subsys devices
[    0.012589] Initializing cgroup subsys freezer
[    0.012616] Initializing cgroup subsys net_cls
[    0.012642] Initializing cgroup subsys blkio
[    0.012689] tseg: 0000000000
[    0.012700] CPU: Physical Processor ID: 0
[    0.012726] CPU: Processor Core ID: 0
[    0.012751] mce: CPU supports 6 MCE banks
[    0.012783] using C1E aware idle routine
[    0.013914] ACPI: Core revision 20110112
[    0.020010] ftrace: allocating 24314 entries in 96 pages
[    0.024983] Setting APIC routing to flat
[    0.025267] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.125602] CPU0: AMD Phenom(tm) II X6 1075T Processor stepping 00
[    0.130000] Performance Events: AMD PMU driver.
[    0.130000] ... version:                0
[    0.130000] ... bit width:              48
[    0.130000] ... generic registers:      4
[    0.130000] ... value mask:             0000ffffffffffff
[    0.130000] ... max period:             00007fffffffffff
[    0.130000] ... fixed-purpose events:   0
[    0.130000] ... event mask:             000000000000000f
[    0.130000] Booting Node   0, Processors  #1
[    0.290012] System has AMD C1E enabled
[    0.290047]  #2
[    0.290099] Switch to broadcast mode on CPU1
[    0.460014] Switch to broadcast mode on CPU2
[    0.460054]  #3
[    0.630029] Switch to broadcast mode on CPU3
[    0.630072]  #4
[    0.800030] Switch to broadcast mode on CPU4
[    0.800077]  #5 Ok.
[    0.970035] Brought up 6 CPUs
[    0.970031] Switch to broadcast mode on CPU5
[    0.970092] Total of 6 processors activated (36159.06 BogoMIPS).
[    0.973066] Switch to broadcast mode on CPU0
[    0.973066] devtmpfs: initialized
[    0.973066] print_constraints: dummy: 
[    0.973066] Time: 15:52:04  Date: 04/30/11
[    0.973066] NET: Registered protocol family 16
[    0.973066] node 0 link 0: io port [1000, ffffff]
[    0.973066] TOM: 00000000c0000000 aka 3072M
[    0.973066] Fam 10h mmconf [e0000000, efffffff]
[    0.973066] node 0 link 0: mmio [a0000, bffff]
[    0.973066] node 0 link 0: mmio [c0000000, cfffffff]
[    0.973066] node 0 link 0: mmio [d0000000, dfffffff]
[    0.973066] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.973066] node 0 link 0: mmio [f0000000, fe5fffff]
[    0.973066] node 0 link 0: mmio [fe600000, fe7fffff]
[    0.973066] node 0 link 0: mmio [fe800000, ffdfffff]
[    0.973066] TOM2: 0000000240000000 aka 9216M
[    0.973066] bus: [00, 07] on node 0 link 0
[    0.973066] bus: 00 index 0 [io  0x0000-0xffff]
[    0.973066] Trying to unpack rootfs image as initramfs...
[    0.973066] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.973066] bus: 00 index 2 [mem 0xc0000000-0xdfffffff]
[    0.973066] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.973066] bus: 00 index 4 [mem 0x240000000-0xfcffffffff]
[    0.973066] Extended Config Space enabled on 1 nodes
[    0.973066] ACPI: bus type pci registered
[    0.973066] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.973066] PCI: not using MMCONFIG
[    0.973066] PCI: Using configuration type 1 for base access
[    0.973066] PCI: Using configuration type 1 for extended access
[    0.973066] bio: create slab <bio-0> at 0
[    0.973066] ACPI: EC: Look up EC in DSDT
[    0.973066] ACPI: Executed 3 blocks of module-level executable AML code
[    2.740559] Freeing initrd memory: 13568k freed
[    3.140578] ACPI: Interpreter enabled
[    3.140608] ACPI: (supports S0 S1 S3 S4 S5)
[    3.140756] ACPI: Using IOAPIC for interrupt routing
[    3.140799] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    3.142062] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    3.160304] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    3.160420] ACPI: No dock devices found.
[    3.160445] HEST: Table not found.
[    3.160472] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    3.160610] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    3.160741] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    3.160769] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    3.160796] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    3.160824] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    3.160853] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    3.160881] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    3.160919] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    3.160953] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    3.160977] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    3.160998] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    3.161000] pci 0000:00:02.0: PME# disabled
[    3.161012] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    3.161031] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    3.161033] pci 0000:00:05.0: PME# disabled
[    3.161044] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
[    3.161063] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    3.161065] pci 0000:00:07.0: PME# disabled
[    3.161076] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
[    3.161096] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    3.161097] pci 0000:00:09.0: PME# disabled
[    3.161107] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    3.161128] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    3.161129] pci 0000:00:0a.0: PME# disabled
[    3.161149] pci 0000:00:11.0: [1002:4393] type 0 class 0x000104
[    3.161162] pci 0000:00:11.0: reg 10: [io  0x9000-0x9007]
[    3.161169] pci 0000:00:11.0: reg 14: [io  0x8000-0x8003]
[    3.161176] pci 0000:00:11.0: reg 18: [io  0x7000-0x7007]
[    3.161183] pci 0000:00:11.0: reg 1c: [io  0x6000-0x6003]
[    3.161189] pci 0000:00:11.0: reg 20: [io  0x5000-0x500f]
[    3.161196] pci 0000:00:11.0: reg 24: [mem 0xfe5ffc00-0xfe5fffff]
[    3.161230] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    3.161240] pci 0000:00:12.0: reg 10: [mem 0xfe5fe000-0xfe5fefff]
[    3.161289] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    3.161303] pci 0000:00:12.2: reg 10: [mem 0xfe5ff800-0xfe5ff8ff]
[    3.161352] pci 0000:00:12.2: supports D1 D2
[    3.161353] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    3.161356] pci 0000:00:12.2: PME# disabled
[    3.161370] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    3.161380] pci 0000:00:13.0: reg 10: [mem 0xfe5fd000-0xfe5fdfff]
[    3.161429] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    3.161443] pci 0000:00:13.2: reg 10: [mem 0xfe5ff400-0xfe5ff4ff]
[    3.161492] pci 0000:00:13.2: supports D1 D2
[    3.161493] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    3.161496] pci 0000:00:13.2: PME# disabled
[    3.161511] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    3.161561] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    3.161571] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    3.161577] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    3.161584] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    3.161591] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    3.161598] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    3.161623] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    3.161638] pci 0000:00:14.2: reg 10: [mem 0xfe5f4000-0xfe5f7fff 64bit]
[    3.161679] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    3.161682] pci 0000:00:14.2: PME# disabled
[    3.161691] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    3.161744] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    3.161773] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    3.161782] pci 0000:00:14.5: reg 10: [mem 0xfe5fc000-0xfe5fcfff]
[    3.161829] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    3.161838] pci 0000:00:16.0: reg 10: [mem 0xfe5f3000-0xfe5f3fff]
[    3.161887] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    3.161901] pci 0000:00:16.2: reg 10: [mem 0xfe5ff000-0xfe5ff0ff]
[    3.161950] pci 0000:00:16.2: supports D1 D2
[    3.161951] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    3.161954] pci 0000:00:16.2: PME# disabled
[    3.161967] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    3.161978] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    3.161988] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    3.161997] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    3.162009] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    3.162042] pci 0000:01:05.0: [1002:9715] type 0 class 0x000300
[    3.162049] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    3.162052] pci 0000:01:05.0: reg 14: [io  0xa000-0xa0ff]
[    3.162056] pci 0000:01:05.0: reg 18: [mem 0xfe7f0000-0xfe7fffff]
[    3.162063] pci 0000:01:05.0: reg 24: [mem 0xfe600000-0xfe6fffff]
[    3.162073] pci 0000:01:05.0: supports D1 D2
[    3.162100] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.162127] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    3.162129] pci 0000:00:01.0:   bridge window [mem 0xfe600000-0xfe7fffff]
[    3.162132] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.162158] pci 0000:02:00.0: [1002:9490] type 0 class 0x000300
[    3.162171] pci 0000:02:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.162182] pci 0000:02:00.0: reg 18: [mem 0xfe8f0000-0xfe8fffff 64bit]
[    3.162188] pci 0000:02:00.0: reg 20: [io  0xb000-0xb0ff]
[    3.162201] pci 0000:02:00.0: reg 30: [mem 0xfe8c0000-0xfe8dffff pref]
[    3.162218] pci 0000:02:00.0: supports D1 D2
[    3.162237] pci 0000:02:00.1: [1002:aa38] type 0 class 0x000403
[    3.162250] pci 0000:02:00.1: reg 10: [mem 0xfe8ec000-0xfe8effff 64bit]
[    3.162295] pci 0000:02:00.1: supports D1 D2
[    3.180017] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    3.180048] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    3.180051] pci 0000:00:02.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    3.180055] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.180089] pci 0000:03:00.0: [10ec:8172] type 0 class 0x000280
[    3.180102] pci 0000:03:00.0: reg 10: [io  0xc800-0xc8ff]
[    3.180110] pci 0000:03:00.0: reg 14: [mem 0xfe9fc000-0xfe9fffff]
[    3.180170] pci 0000:03:00.0: supports D1 D2
[    3.180171] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    3.180174] pci 0000:03:00.0: PME# disabled
[    3.200017] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    3.200048] pci 0000:00:05.0:   bridge window [io  0xc000-0xcfff]
[    3.200050] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    3.200053] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    3.200087] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
[    3.200102] pci 0000:04:00.0: reg 10: [mem 0xfeafe000-0xfeafffff 64bit]
[    3.200157] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    3.200160] pci 0000:04:00.0: PME# disabled
[    3.220017] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    3.220047] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    3.220050] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    3.220053] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    3.220098] pci 0000:05:00.0: [1106:0415] type 0 class 0x000101
[    3.220119] pci 0000:05:00.0: reg 10: [io  0xdc00-0xdc07]
[    3.220134] pci 0000:05:00.0: reg 14: [io  0xd880-0xd883]
[    3.220149] pci 0000:05:00.0: reg 18: [io  0xd800-0xd807]
[    3.220163] pci 0000:05:00.0: reg 1c: [io  0xd480-0xd483]
[    3.220178] pci 0000:05:00.0: reg 20: [io  0xd400-0xd40f]
[    3.220206] pci 0000:05:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
[    3.220252] pci 0000:05:00.0: supports D1 D2
[    3.220253] pci 0000:05:00.0: PME# supported from D1 D2 D3hot
[    3.220258] pci 0000:05:00.0: PME# disabled
[    3.240020] pci 0000:00:09.0: PCI bridge to [bus 05-05]
[    3.240051] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    3.240053] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    3.240056] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    3.240090] pci 0000:06:00.0: [10ec:8168] type 0 class 0x000200
[    3.240102] pci 0000:06:00.0: reg 10: [io  0xe800-0xe8ff]
[    3.240122] pci 0000:06:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    3.240134] pci 0000:06:00.0: reg 20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
[    3.240169] pci 0000:06:00.0: supports D1 D2
[    3.240170] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.240174] pci 0000:06:00.0: PME# disabled
[    3.260018] pci 0000:00:0a.0: PCI bridge to [bus 06-06]
[    3.260048] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    3.260051] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    3.260054] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    3.260103] pci 0000:00:14.4: PCI bridge to [bus 07-07] (subtractive decode)
[    3.260134] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    3.260137] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    3.260140] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    3.260142] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    3.260144] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    3.260146] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    3.260147] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    3.260149] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    3.260151] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    3.260167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.260276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    3.260299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    3.260318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    3.260337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    3.260355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    3.260376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    3.260402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    3.260497]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    3.260610]  pci0000:00: ACPI _OSC control (0x1d) granted
[    3.263784] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[    3.264111] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    3.264438] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    3.264764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *9 10 11 14 15)
[    3.265059] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    3.265391] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    3.265726] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    3.266058] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    3.266433] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    3.266464] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    3.266494] vgaarb: loaded
[    3.266617] SCSI subsystem initialized
[    3.266662] libata version 3.00 loaded.
[    3.266662] usbcore: registered new interface driver usbfs
[    3.266662] usbcore: registered new interface driver hub
[    3.266662] usbcore: registered new device driver usb
[    3.266662] wmi: Mapper loaded
[    3.266662] PCI: Using ACPI for IRQ routing
[    3.266662] PCI: pci_cache_line_size set to 64 bytes
[    3.266662] reserve RAM buffer: 0000000000093400 - 000000000009ffff 
[    3.266662] reserve RAM buffer: 00000000bf810000 - 00000000bfffffff 
[    3.266662] NetLabel: Initializing
[    3.266662] NetLabel:  domain hash size = 128
[    3.266662] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.266662] NetLabel:  unlabeled traffic allowed by default
[    3.266662] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    3.266662] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    3.266662] Switching to clocksource hpet
[    3.266662] Switched to NOHz mode on CPU #5
[    3.266662] Switched to NOHz mode on CPU #0
[    3.266662] Switched to NOHz mode on CPU #2
[    3.266662] Switched to NOHz mode on CPU #1
[    3.266662] Switched to NOHz mode on CPU #3
[    3.266662] Switched to NOHz mode on CPU #4
[    3.266662] AppArmor: AppArmor Filesystem Enabled
[    3.266662] pnp: PnP ACPI init
[    3.266662] ACPI: bus type pnp registered
[    3.266662] pnp 00:00: [bus 00-ff]
[    3.266662] pnp 00:00: [io  0x0cf8-0x0cff]
[    3.266662] pnp 00:00: [io  0x0000-0x0cf7 window]
[    3.266662] pnp 00:00: [io  0x0d00-0xffff window]
[    3.266662] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    3.266662] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    3.266662] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    3.266662] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    3.266662] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    3.266662] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.266662] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.266662] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.266662] pnp 00:02: [dma 4]
[    3.266662] pnp 00:02: [io  0x0000-0x000f]
[    3.266662] pnp 00:02: [io  0x0081-0x0083]
[    3.266662] pnp 00:02: [io  0x0087]
[    3.266662] pnp 00:02: [io  0x0089-0x008b]
[    3.266662] pnp 00:02: [io  0x008f]
[    3.266662] pnp 00:02: [io  0x00c0-0x00df]
[    3.266662] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    3.266662] pnp 00:03: [io  0x0070-0x0071]
[    3.266662] pnp 00:03: [irq 8]
[    3.266662] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.266662] pnp 00:04: [io  0x0061]
[    3.266662] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    3.266662] pnp 00:05: [io  0x00f0-0x00ff]
[    3.266662] pnp 00:05: [irq 13]
[    3.266662] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.266662] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    3.266662] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    3.266662] pnp 00:07: [io  0x0060]
[    3.266662] pnp 00:07: [io  0x0064]
[    3.266662] pnp 00:07: [irq 1]
[    3.266662] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    3.266662] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    3.266662] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    3.266662] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    3.266662] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    3.266662] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.266662] pnp 00:09: [io  0x0010-0x001f]
[    3.266662] pnp 00:09: [io  0x0022-0x003f]
[    3.266662] pnp 00:09: [io  0x0062-0x0063]
[    3.266662] pnp 00:09: [io  0x0065-0x006f]
[    3.266662] pnp 00:09: [io  0x0072-0x007f]
[    3.266662] pnp 00:09: [io  0x0080]
[    3.266662] pnp 00:09: [io  0x0084-0x0086]
[    3.266662] pnp 00:09: [io  0x0088]
[    3.266662] pnp 00:09: [io  0x008c-0x008e]
[    3.266662] pnp 00:09: [io  0x0090-0x009f]
[    3.266662] pnp 00:09: [io  0x00a2-0x00bf]
[    3.266662] pnp 00:09: [io  0x00b1]
[    3.266662] pnp 00:09: [io  0x00e0-0x00ef]
[    3.266662] pnp 00:09: [io  0x04d0-0x04d1]
[    3.266662] pnp 00:09: [io  0x040b]
[    3.266662] pnp 00:09: [io  0x04d6]
[    3.266662] pnp 00:09: [io  0x0c00-0x0c01]
[    3.266662] pnp 00:09: [io  0x0c14]
[    3.266662] pnp 00:09: [io  0x0c50-0x0c51]
[    3.266662] pnp 00:09: [io  0x0c52]
[    3.266662] pnp 00:09: [io  0x0c6c]
[    3.266662] pnp 00:09: [io  0x0c6f]
[    3.266662] pnp 00:09: [io  0x0cd0-0x0cd1]
[    3.266662] pnp 00:09: [io  0x0cd2-0x0cd3]
[    3.266662] pnp 00:09: [io  0x0cd4-0x0cd5]
[    3.266662] pnp 00:09: [io  0x0cd6-0x0cd7]
[    3.266662] pnp 00:09: [io  0x0cd8-0x0cdf]
[    3.266662] pnp 00:09: [io  0x0b00-0x0b3f]
[    3.266662] pnp 00:09: [io  0x0800-0x089f]
[    3.266662] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    3.266662] pnp 00:09: [io  0x0b00-0x0b1f]
[    3.266662] pnp 00:09: [io  0x0b20-0x0b3f]
[    3.266662] pnp 00:09: [io  0x0900-0x090f]
[    3.266662] pnp 00:09: [io  0x0910-0x091f]
[    3.266662] pnp 00:09: [io  0xfe00-0xfefe]
[    3.266662] pnp 00:09: [io  0x0060-0x005f disabled]
[    3.266662] pnp 00:09: [io  0x0064-0x0063 disabled]
[    3.266662] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.266662] pnp 00:09: [mem 0xffb80000-0xffbfffff]
[    3.266662] pnp 00:09: [mem 0xfec10000-0xfec1001f]
[    3.266662] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    3.266662] pnp 00:09: [mem 0xfed80000-0xfed80fff]
[    3.266662] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.266662] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    3.266662] system 00:09: [io  0x040b] has been reserved
[    3.266662] system 00:09: [io  0x04d6] has been reserved
[    3.266662] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    3.266662] system 00:09: [io  0x0c14] has been reserved
[    3.266662] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    3.266662] system 00:09: [io  0x0c52] has been reserved
[    3.266662] system 00:09: [io  0x0c6c] has been reserved
[    3.266662] system 00:09: [io  0x0c6f] has been reserved
[    3.266662] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    3.266662] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    3.266662] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    3.266662] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    3.266662] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    3.266662] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    3.266662] system 00:09: [io  0x0800-0x089f] has been reserved
[    3.266662] system 00:09: [io  0x0b00-0x0b1f] has been reserved
[    3.266662] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    3.266662] system 00:09: [io  0x0900-0x090f] has been reserved
[    3.266662] system 00:09: [io  0x0910-0x091f] has been reserved
[    3.266662] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    3.266662] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    3.266662] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    3.266662] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    3.266662] system 00:09: [mem 0xfed80000-0xfed80fff] has been reserved
[    3.266662] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.266662] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    3.266662] pnp 00:0a: [io  0x0230-0x023f]
[    3.266662] pnp 00:0a: [io  0x0290-0x029f]
[    3.266662] pnp 00:0a: [io  0x0300-0x030f]
[    3.266662] pnp 00:0a: [io  0x0a30-0x0a3f]
[    3.266662] system 00:0a: [io  0x0230-0x023f] has been reserved
[    3.266662] system 00:0a: [io  0x0290-0x029f] has been reserved
[    3.266662] system 00:0a: [io  0x0300-0x030f] has been reserved
[    3.266662] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    3.266662] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.266662] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    3.266662] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    3.266662] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.266662] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    3.266662] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    3.266662] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    3.266662] pnp 00:0c: [mem 0x00100000-0xbfffffff]
[    3.266662] pnp 00:0c: [mem 0xfec00000-0xffffffff]
[    3.266662] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    3.266662] system 00:0c: [mem 0x000c0000-0x000cffff] has been reserved
[    3.266662] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    3.266662] system 00:0c: [mem 0x00100000-0xbfffffff] could not be reserved
[    3.266662] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    3.266662] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    3.266662] pnp: PnP ACPI: found 13 devices
[    3.266662] ACPI: ACPI bus type pnp unregistered
[    3.272146] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.272174] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    3.272202] pci 0000:00:01.0:   bridge window [mem 0xfe600000-0xfe7fffff]
[    3.272230] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.272261] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    3.272287] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    3.272316] pci 0000:00:02.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    3.272344] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.272374] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    3.272400] pci 0000:00:05.0:   bridge window [io  0xc000-0xcfff]
[    3.272428] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    3.272456] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    3.272484] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    3.272510] pci 0000:00:07.0:   bridge window [io  disabled]
[    3.272538] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    3.272566] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    3.272593] pci 0000:00:09.0: PCI bridge to [bus 05-05]
[    3.272621] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    3.272648] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    3.272676] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    3.272704] pci 0000:00:0a.0: PCI bridge to [bus 06-06]
[    3.272730] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    3.272758] pci 0000:00:0a.0:   bridge window [mem disabled]
[    3.272785] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    3.272815] pci 0000:00:14.4: PCI bridge to [bus 07-07]
[    3.272841] pci 0000:00:14.4:   bridge window [io  disabled]
[    3.272870] pci 0000:00:14.4:   bridge window [mem disabled]
[    3.272899] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    3.272940] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.272968] pci 0000:00:02.0: setting latency timer to 64
[    3.272973] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.273001] pci 0000:00:05.0: setting latency timer to 64
[    3.273006] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.273034] pci 0000:00:07.0: setting latency timer to 64
[    3.273037] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.273064] pci 0000:00:09.0: setting latency timer to 64
[    3.273067] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.273094] pci 0000:00:0a.0: setting latency timer to 64
[    3.273100] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    3.273101] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    3.273102] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    3.273104] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    3.273105] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    3.273106] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    3.273108] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    3.273109] pci_bus 0000:01: resource 1 [mem 0xfe600000-0xfe7fffff]
[    3.273111] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.273112] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    3.273114] pci_bus 0000:02: resource 1 [mem 0xfe800000-0xfe8fffff]
[    3.273115] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.273117] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    3.273118] pci_bus 0000:03: resource 1 [mem 0xfe900000-0xfe9fffff]
[    3.273119] pci_bus 0000:04: resource 1 [mem 0xfea00000-0xfeafffff]
[    3.273121] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    3.273122] pci_bus 0000:05: resource 1 [mem 0xfeb00000-0xfebfffff]
[    3.273124] pci_bus 0000:06: resource 0 [io  0xe000-0xefff]
[    3.273125] pci_bus 0000:06: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    3.273127] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    3.273128] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    3.273129] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    3.273131] pci_bus 0000:07: resource 7 [mem 0x000d0000-0x000dffff]
[    3.273132] pci_bus 0000:07: resource 8 [mem 0xc0000000-0xdfffffff]
[    3.273133] pci_bus 0000:07: resource 9 [mem 0xf0000000-0xfebfffff]
[    3.273157] NET: Registered protocol family 2
[    3.273335] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    3.274378] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.276258] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.276510] TCP: Hash tables configured (established 524288 bind 65536)
[    3.276538] TCP reno registered
[    3.276572] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    3.276639] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    3.276766] NET: Registered protocol family 1
[    3.276800] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    6.960137] pci 0000:01:05.0: Boot video device
[    6.962198] pci 0000:04:00.0: xHCI HW did not halt within 2000 usec status = 0x0
[    6.962235] PCI: CLS 64 bytes, default 64
[    6.963733] PCI-DMA: Disabling AGP.
[    6.963871] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    6.963897] PCI-DMA: using GART IOMMU.
[    6.963925] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    6.967256] audit: initializing netlink socket (disabled)
[    6.967299] type=2000 audit(1304178729.960:1): initialized
[    6.975812] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    6.976976] VFS: Disk quotas dquot_6.5.2
[    6.977032] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    6.977481] fuse init (API version 7.16)
[    6.977554] msgmni has been set to 15479
[    6.977825] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    6.977880] io scheduler noop registered
[    6.977908] io scheduler deadline registered
[    6.977954] io scheduler cfq registered (default)
[    6.978196] pcieport 0000:00:02.0: setting latency timer to 64
[    6.978223] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    6.978317] pcieport 0000:00:05.0: setting latency timer to 64
[    6.978336] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    6.978414] pcieport 0000:00:07.0: setting latency timer to 64
[    6.978432] pcieport 0000:00:07.0: irq 42 for MSI/MSI-X
[    6.978513] pcieport 0000:00:09.0: setting latency timer to 64
[    6.978532] pcieport 0000:00:09.0: irq 43 for MSI/MSI-X
[    6.978613] pcieport 0000:00:0a.0: setting latency timer to 64
[    6.978631] pcieport 0000:00:0a.0: irq 44 for MSI/MSI-X
[    6.978698] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    6.978726] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    6.978753] pci 0000:02:00.1: Signaling PME through PCIe PME interrupt
[    6.978781] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    6.978791] pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
[    6.978818] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    6.978846] pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
[    6.978856] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    6.978884] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    6.978921] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    6.978929] pcieport 0000:00:09.0: Signaling PME through PCIe PME interrupt
[    6.979420] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    6.979448] pcie_pme 0000:00:09.0:pcie01: service driver pcie_pme loaded
[    6.979455] pcieport 0000:00:0a.0: Signaling PME through PCIe PME interrupt
[    6.979482] pci 0000:06:00.0: Signaling PME through PCIe PME interrupt
[    6.979509] pcie_pme 0000:00:0a.0:pcie01: service driver pcie_pme loaded
[    6.979520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    6.979559] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    6.979668] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    6.979699] ACPI: Power Button [PWRB]
[    6.979751] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    6.979780] ACPI: Power Button [PWRF]
[    6.979905] ACPI: acpi_idle registered with cpuidle
[    6.979944] ACPI: processor limited to max C-state 1
[    6.982679] ERST: Table is not found!
[    6.982744] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    7.420333] Linux agpgart interface v0.103
[    7.420975] brd: module loaded
[    7.421277] loop: module loaded
[    7.421358] i2c-core: driver [adp5520] using legacy suspend method
[    7.421384] i2c-core: driver [adp5520] using legacy resume method
[    7.421575] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.421627] pata_acpi 0000:00:14.1: setting latency timer to 64
[    7.421688] pata_acpi 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.421733] pata_acpi 0000:05:00.0: setting latency timer to 64
[    7.421743] pata_acpi 0000:05:00.0: PCI INT A disabled
[    7.422061] Fixed MDIO Bus: probed
[    7.422106] PPP generic driver version 2.4.2
[    7.422157] tun: Universal TUN/TAP device driver, 1.6
[    7.422188] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    7.422257] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    7.422359] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.422420] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    7.422490] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    7.490103] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    7.490135] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    7.490182] ehci_hcd 0000:00:12.2: debug port 1
[    7.490236] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe5ff800
[    7.510073] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    7.510196] hub 1-0:1.0: USB hub found
[    7.510224] hub 1-0:1.0: 5 ports detected
[    7.510395] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.510432] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    7.510484] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    7.510541] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    7.510571] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    7.510615] ehci_hcd 0000:00:13.2: debug port 1
[    7.510650] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe5ff400
[    7.530085] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    7.530189] hub 2-0:1.0: USB hub found
[    7.530217] hub 2-0:1.0: 5 ports detected
[    7.530376] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.530413] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    7.530467] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    7.530523] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM
[    7.530553] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    7.530596] ehci_hcd 0000:00:16.2: debug port 1
[    7.530632] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe5ff000
[    7.550071] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    7.550176] hub 3-0:1.0: USB hub found
[    7.550208] hub 3-0:1.0: 4 ports detected
[    7.550308] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    7.550425] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.550462] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    7.550519] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    7.550586] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe5fe000
[    7.614161] hub 4-0:1.0: USB hub found
[    7.614190] hub 4-0:1.0: 5 ports detected
[    7.614371] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.614408] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    7.614467] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    7.614525] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe5fd000
[    7.674142] hub 5-0:1.0: USB hub found
[    7.674172] hub 5-0:1.0: 5 ports detected
[    7.674351] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    7.674388] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    7.674439] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    7.674498] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe5fc000
[    7.734155] hub 6-0:1.0: USB hub found
[    7.734185] hub 6-0:1.0: 2 ports detected
[    7.734361] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.734398] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    7.734450] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    7.734509] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe5f3000
[    7.794166] hub 7-0:1.0: USB hub found
[    7.794196] hub 7-0:1.0: 4 ports detected
[    7.794300] uhci_hcd: USB Universal Host Controller Interface driver
[    7.890097] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    7.890126] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    7.890317] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.890407] mousedev: PS/2 mouse device common for all mice
[    7.890500] rtc_cmos 00:03: RTC can wake from S4
[    7.960149] Refined TSC clocksource calibration: 3013.355 MHz.
[    7.960178] Switching to clocksource tsc
[    7.960243] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    7.960288] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    7.960379] device-mapper: uevent: version 1.0.3
[    7.960456] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    7.960565] device-mapper: multipath: version 1.2.0 loaded
[    7.960592] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.960691] cpuidle: using governor ladder
[    7.960717] cpuidle: using governor menu
[    7.960883] TCP cubic registered
[    7.960975] NET: Registered protocol family 10
[    7.961290] NET: Registered protocol family 17
[    7.961324] Registering the dns_resolver key type
[    7.961423] powernow-k8: Found 1 AMD Phenom(tm) II X6 1075T Processor (6 cpu cores) (version 2.20.00)
[    7.961458] powernow-k8: Core Performance Boosting: on.
[    7.961509] powernow-k8:    0 : pstate 0 (3000 MHz)
[    7.961535] powernow-k8:    1 : pstate 1 (2300 MHz)
[    7.961562] powernow-k8:    2 : pstate 2 (1600 MHz)
[    7.961588] powernow-k8:    3 : pstate 3 (800 MHz)
[    7.962296] PM: Hibernation image not present or could not be loaded.
[    7.962303] registered taskstats version 1
[    7.962583]   Magic number: 7:173:893
[    7.962697] rtc_cmos 00:03: setting system clock to 2011-04-30 15:52:11 UTC (1304178731)
[    7.962728] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.962754] EDD information not available.
[    7.963895] Freeing unused kernel memory: 956k freed
[    7.964096] Write protecting the kernel read-only data: 10240k
[    7.964750] Freeing unused kernel memory: 184k freed
[    7.968031] Freeing unused kernel memory: 1444k freed
[    7.984777] <30>udev[134]: starting version 167
[    8.012432] [drm] Initialized drm 1.1.0 20060810
[    8.014903] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.014949] r8169 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.015008] r8169 0000:06:00.0: setting latency timer to 64
[    8.015012] r8169 0000:06:00.0: (unregistered net_device): unknown MAC, using family default
[    8.015080] r8169 0000:06:00.0: irq 45 for MSI/MSI-X
[    8.015397] r8169 0000:06:00.0: eth0: RTL8168b/8111b at 0xffffc90000c7e000, 20:cf:30:e1:35:0d, XID 0c200000 IRQ 45
[    8.017262] pata_via 0000:05:00.0: version 0.3.4
[    8.017273] pata_via 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.017348] pata_via 0000:05:00.0: setting latency timer to 64
[    8.017602] scsi0 : pata_via
[    8.018494] scsi1 : pata_via
[    8.018641] ata1: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    8.018670] ata2: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    8.018758] scsi2 : pata_atiixp
[    8.020034] scsi3 : pata_atiixp
[    8.020544] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    8.020573] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    8.093066] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    8.140096] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    8.360058] ahci 0000:00:11.0: version 3.0
[    8.360070] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.360196] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl RAID mode
[    8.360227] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    8.360769] scsi4 : ahci
[    8.360851] scsi5 : ahci
[    8.360924] scsi6 : ahci
[    8.360997] scsi7 : ahci
[    8.361061] ata5: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffd00 irq 19
[    8.361092] ata6: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffd80 irq 19
[    8.361123] ata7: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffe00 irq 19
[    8.361165] ata8: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffe80 irq 19
[    8.367229] [drm] radeon defaulting to kernel modesetting.
[    8.367258] [drm] radeon kernel modesetting enabled.
[    8.370064] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.370094] radeon 0000:01:05.0: setting latency timer to 64
[    8.371406] [drm] initializing kernel modesetting (RS880 0x1002:0x9715).
[    8.371451] [drm] register mmio base: 0xFE7F0000
[    8.371477] [drm] register mmio size: 65536
[    8.372536] ATOM BIOS: 113
[    8.372576] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    8.372605] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    8.375927] [drm] Detected VRAM RAM=256M, BAR=256M
[    8.375963] [drm] RAM width 32bits DDR
[    8.379950] [TTM] Zone  kernel: Available graphics memory: 3963978 kiB.
[    8.380052] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    8.380083] [TTM] Initializing pool allocator.
[    8.380123] [drm] radeon: 256M of VRAM memory ready
[    8.380150] [drm] radeon: 512M of GTT memory ready.
[    8.380187] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.380214] [drm] Driver supports precise vblank timestamp query.
[    8.380256] [drm] radeon: irq initialized.
[    8.380283] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.380839] [drm] Loading RS780 Microcode
[    8.387401] radeon 0000:01:05.0: WB enabled
[    8.419427] [drm] ring test succeeded in 1 usecs
[    8.419524] [drm] radeon: ib pool ready.
[    8.419598] [drm] ib test succeeded in 0 usecs
[    8.419632] [drm] Enabling audio support
[    8.419923] [drm] Radeon Display Connectors
[    8.419939] [drm] Connector 0:
[    8.419964] [drm]   VGA
[    8.420019] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    8.420049] [drm]   Encoders:
[    8.420074] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.420100] [drm] Connector 1:
[    8.420125] [drm]   DVI-D
[    8.420150] [drm]   HPD1
[    8.420176] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    8.420204] [drm]   Encoders:
[    8.420230] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[    8.474294] [drm] radeon: power management initialized
[    8.550446] [drm] fb mappable at 0xC0141000
[    8.550472] [drm] vram apper at 0xC0000000
[    8.550497] [drm] size 4325376
[    8.550522] [drm] fb depth is 24
[    8.550548] [drm]    pitch is 5632
[    8.579124] Console: switching to colour frame buffer device 170x48
[    8.588147] fb0: radeondrmfb frame buffer device
[    8.588209] drm: registered panic notifier
[    8.588267] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[    8.588459] radeon 0000:02:00.0: enabling device (0000 -> 0003)
[    8.588541] radeon 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.588633] radeon 0000:02:00.0: setting latency timer to 64
[    8.589821] [drm] initializing kernel modesetting (RV730 0x1002:0x9490).
[    8.589950] [drm] register mmio base: 0xFE8F0000
[    8.590027] [drm] register mmio size: 65536
[    8.680108] usb 4-5: new low speed USB device using ohci_hcd and address 3
[    8.702876] ATOM BIOS: 113
[    8.702928] [drm] GPU not posted. posting now...
[    8.704236] radeon 0000:02:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    8.704352] radeon 0000:02:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    8.713401] [drm] Detected VRAM RAM=1024M, BAR=256M
[    8.713479] [drm] RAM width 128bits DDR
[    8.713541] [drm] radeon: 1024M of VRAM memory ready
[    8.713608] [drm] radeon: 512M of GTT memory ready.
[    8.713675] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.713768] [drm] Driver supports precise vblank timestamp query.
[    8.713890] radeon 0000:02:00.0: irq 46 for MSI/MSI-X
[    8.713894] radeon 0000:02:00.0: radeon: using MSI.
[    8.713984] [drm] radeon: irq initialized.
[    8.714041] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.714663] [drm] Loading RV730 Microcode
[    8.721873] radeon 0000:02:00.0: WB enabled
[    8.770589] [drm] ring test succeeded in 1 usecs
[    8.773235] [drm] radeon: ib pool ready.
[    8.775825] [drm] ib test succeeded in 0 usecs
[    8.778410] [drm] Enabling audio support
[    8.781052] failed to evaluate ATIF got AE_BAD_PARAMETER
[    8.781277] [drm] Radeon Display Connectors
[    8.783903] [drm] Connector 0:
[    8.786453] [drm]   VGA
[    8.788933] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[    8.791597] [drm]   Encoders:
[    8.794156] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    8.796739] [drm] Connector 1:
[    8.799323] [drm]   HDMI-A
[    8.801968] [drm]   HPD2
[    8.804509] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    8.807094] [drm]   Encoders:
[    8.809665] [drm]     DFP2: INTERNAL_UNIPHY1
[    8.812292] [drm] Connector 2:
[    8.814852] [drm]   DVI-I
[    8.817375] [drm]   HPD1
[    8.819879] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    8.822529] [drm]   Encoders:
[    8.825128] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.827767] [drm]     DFP1: INTERNAL_UNIPHY
[    8.887477] [drm] Internal thermal controller with fan control
[    8.890167] [drm] radeon: power management initialized
[    8.920081] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.922895] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.925667] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.928595] ata6.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    8.931303] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    8.933995] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.936755] ata7.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    8.939492] ata7.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    8.942264] ata5.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    8.944980] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    8.947842] ata6.00: configured for UDMA/133
[    8.950548] ata8.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    8.953243] ata8.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    8.953414] ata7.00: configured for UDMA/133
[    8.953435] ata5.00: configured for UDMA/133
[    8.953550] scsi 4:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    8.953687] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    8.953782] sd 4:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    8.953800] scsi 5:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    8.953876] sd 4:0:0:0: [sda] Write Protect is off
[    8.953878] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.953912] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.953947] sd 5:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    8.953949] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    8.954052] sd 5:0:0:0: [sdb] Write Protect is off
[    8.954054] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.954085] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.954154] scsi 6:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    8.954270] sd 6:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    8.954285] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    8.954364] sd 6:0:0:0: [sdc] Write Protect is off
[    8.954366] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    8.954393] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.954448] ata8.00: configured for UDMA/133
[    8.954520] scsi 7:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    8.954612] sd 7:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    8.954624] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    8.954675] sd 7:0:0:0: [sdd] Write Protect is off
[    8.954677] sd 7:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    8.954703] sd 7:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.962265] generic-usb 0003:0764:0501.0001: hiddev0,hidraw0: USB HID v1.10 Device [CPS  CP 1500C] on usb-0000:00:12.0-2/input0
[    8.968328] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input3
[    8.968408] generic-usb 0003:1BCF:0007.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:12.0-5/input0
[    8.968417] usbcore: registered new interface driver usbhid
[    8.968418] usbhid: USB HID core driver
[    8.973080]  sdb: sdb1 sdb2
[    8.973416]  sdc: sdc1 sdc2 sdc3
[    8.974797]  sda: sda1 sda2
[    8.977511]  sdd: sdd1 sdd2 sdd3
[    9.010026] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    9.019250] sd 5:0:0:0: [sdb] Attached SCSI disk
[    9.019269] sd 7:0:0:0: [sdd] Attached SCSI disk
[    9.019295] sd 4:0:0:0: [sda] Attached SCSI disk
[    9.019277] sd 6:0:0:0: [sdc] Attached SCSI disk
[    9.067671] [drm] fb mappable at 0xD0142000
[    9.071087] [drm] vram apper at 0xD0000000
[    9.074425] [drm] size 4325376
[    9.077605] [drm] fb depth is 24
[    9.080806] [drm]    pitch is 5632
[    9.083967] fb1: radeondrmfb frame buffer device
[    9.087121] [drm] Initialized radeon 2.8.0 20080528 for 0000:02:00.0 on minor 1
[    9.174338] usbcore: registered new interface driver uas
[    9.180374] Initializing USB Mass Storage driver...
[    9.183639] scsi8 : usb-storage 2-2:1.0
[    9.186938] usbcore: registered new interface driver usb-storage
[    9.190153] USB Mass Storage support registered.
[    9.303324] device-mapper: table: 252:0: sdc too small for target: start=0, len=6248092288, dev_size=1953525168
[    9.931172] Btrfs loaded
[    9.934747] xor: automatically using best checksumming function: generic_sse
[    9.980051]    generic_sse: 14340.000 MB/sec
[    9.980056] xor: using function: generic_sse (14340.000 MB/sec)
[    9.981990] device-mapper: dm-raid45: initialized v0.2594b
[   10.180675] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 2
[   10.181052] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   10.181659] sd 8:0:0:0: [sde] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
[   10.182795] sd 8:0:0:0: [sde] Write Protect is off
[   10.182798] sd 8:0:0:0: [sde] Mode Sense: 03 00 00 00
[   10.183539] sd 8:0:0:0: [sde] No Caching mode page present
[   10.183542] sd 8:0:0:0: [sde] Assuming drive cache: write through
[   10.186414] sd 8:0:0:0: [sde] No Caching mode page present
[   10.186416] sd 8:0:0:0: [sde] Assuming drive cache: write through
[   10.187172]  sde: sde1
[   10.189653] sd 8:0:0:0: [sde] No Caching mode page present
[   10.189656] sd 8:0:0:0: [sde] Assuming drive cache: write through
[   10.189658] sd 8:0:0:0: [sde] Attached SCSI removable disk
[   30.238585] aufs 2.1-standalone.tree-38-rcN-20110207
[   30.249536] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   38.721409] <30>udev[2891]: starting version 167
[   39.005288] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   39.005311] xhci_hcd 0000:04:00.0: setting latency timer to 64
[   39.005314] xhci_hcd 0000:04:00.0: xHCI Host Controller
[   39.005384] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
[   39.036517] cfg80211: Calling CRDA to update world regulatory domain
[   39.040245] xhci_hcd 0000:04:00.0: irq 19, io mem 0xfeafe000
[   39.040299] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[   39.040303] xhci_hcd 0000:04:00.0: irq 48 for MSI/MSI-X
[   39.040307] xhci_hcd 0000:04:00.0: irq 49 for MSI/MSI-X
[   39.040310] xhci_hcd 0000:04:00.0: irq 50 for MSI/MSI-X
[   39.040314] xhci_hcd 0000:04:00.0: irq 51 for MSI/MSI-X
[   39.040317] xhci_hcd 0000:04:00.0: irq 52 for MSI/MSI-X
[   39.040321] xhci_hcd 0000:04:00.0: irq 53 for MSI/MSI-X
[   39.043595] usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   39.043700] xHCI xhci_add_endpoint called for root hub
[   39.043702] xHCI xhci_check_bandwidth called for root hub
[   39.043723] hub 8-0:1.0: USB hub found
[   39.043727] hub 8-0:1.0: 4 ports detected
[   39.043888] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.051830] MCE: In-kernel MCE decoding enabled.
[   39.057641] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
[   39.057643] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   39.099908] EDAC MC: Ver: 2.1.0 Apr 11 2011
[   39.111617] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   39.111716] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   39.120688] rtllib_crypt: registered algorithm 'NULL'
[   39.120690] rtllib_crypt: registered algorithm 'TKIP'
[   39.120692] rtllib_crypt: registered algorithm 'CCMP'
[   39.120693] rtllib_crypt: registered algorithm 'WEP'
[   39.120694] 
[   39.120695] Linux kernel driver for RTL8192 based WLAN cards
[   39.120696] Copyright (c) 2007-2008, Realsil Wlan Driver
[   39.120769] EDAC amd64_edac: v3.3.0
[   39.120823] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   39.120828] rtl819xSE 0000:03:00.0: setting latency timer to 64
[   39.120904] EDAC amd64: DRAM ECC disabled.
[   39.120910] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   39.120911]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   39.120912]  (Note that use of the override may cause unknown side effects.)
[   39.120937] Memory mapped space start: 0xfe9fc000 
[   39.120961] Adapter(8192SE) is found - DeviceID=8172
[   39.121568] GetPciBusInfo(): Find Device(10EC:8172)  bus=3 dev=0, func=0
[   39.121628] GetPciBridegInfo : Find Device(1022:9605)  bus=0 dev=5, func=0
[   39.121629] Pci Bridge Vendor is found index: 2
[   39.121630] Pci Bridge Vendor is 1022
[   39.122468] =========>dm_InitRateAdaptiveMask: bUseRAMask=0
[   39.122675] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   39.122677] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122678] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   39.122680] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122682] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   39.122683] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122685] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   39.122686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122688] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   39.122690] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122691] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   39.122693] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122694] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   39.122696] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122697] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   39.122699] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122700] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   39.122702] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122703] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   39.122705] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122707] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   39.122708] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122710] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   39.122711] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122713] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   39.122715] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.122716] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   39.122718] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   39.139947] rtl8192: wireless switch is on
[   39.261063] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   39.261067] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261069] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   39.261071] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261073] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   39.261075] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261076] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   39.261078] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261079] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   39.261081] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261082] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   39.261084] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261086] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   39.261087] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261089] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   39.261090] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261092] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   39.261094] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261095] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   39.261097] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261098] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   39.261100] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261102] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   39.261103] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261105] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   39.261106] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261108] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   39.261110] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   39.261112] cfg80211: World regulatory domain updated:
[   39.261113] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   39.261115] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.261117] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.261119] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.261120] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.261122] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.430073] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.571319] hda_codec: ALC892: BIOS auto-probing.
[   39.582100] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   39.582271] HDA Intel 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   39.582350] HDA Intel 0000:02:00.1: irq 54 for MSI/MSI-X
[   39.582370] HDA Intel 0000:02:00.1: setting latency timer to 64
[   39.710302] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   39.710308] ===>rtllib_start_scan()
[   39.710430] =====>rtl8192_set_chan()====ch:2
[   39.711427] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.731045] r8169 0000:06:00.0: eth0: link down
[   39.731754] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.770485] device-mapper: table: 252:0: sdc too small for target: start=0, len=6248092288, dev_size=1953525168
[   39.820098] =====>rtl8192_set_chan()====ch:3
[   39.921815] =====>rtl8192_set_chan()====ch:1
[   40.040052] =====>rtl8192_set_chan()====ch:2
[   40.124814] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[   40.124818] vgaarb: device changed decodes: PCI:0000:01:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   40.160017] =====>rtl8192_set_chan()====ch:3
[   40.280083] =====>rtl8192_set_chan()====ch:4
[   40.400074] =====>rtl8192_set_chan()====ch:5
[   40.520035] =====>rtl8192_set_chan()====ch:6
[   40.640027] =====>rtl8192_set_chan()====ch:7
[   40.760051] =====>rtl8192_set_chan()====ch:8
[   40.880078] =====>rtl8192_set_chan()====ch:9
[   41.000020] =====>rtl8192_set_chan()====ch:10
[   41.120030] =====>rtl8192_set_chan()====ch:11
[   41.240085] =====>rtl8192_set_chan()====ch:12
[   41.360056] =====>rtl8192_set_chan()====ch:13
[   41.480427] ===>rtllib_wx_set_power(): power disable
[   41.480713] =====>rtl8192_set_chan()====ch:1
[   41.520370] lp: driver loaded but no devices found
[   41.563057] ppdev: user-space parallel port driver
[   41.600086] =====>rtl8192_set_chan()====ch:2
[   41.720018] =====>rtl8192_set_chan()====ch:3
[   41.850044] =====>rtl8192_set_chan()====ch:4
[   41.970082] =====>rtl8192_set_chan()====ch:5
[   42.090089] =====>rtl8192_set_chan()====ch:6
[   42.210091] =====>rtl8192_set_chan()====ch:7
[   42.330057] =====>rtl8192_set_chan()====ch:8
[   42.450075] =====>rtl8192_set_chan()====ch:9
[   42.570075] =====>rtl8192_set_chan()====ch:10
[   42.690056] =====>rtl8192_set_chan()====ch:11
[   42.810079] =====>rtl8192_set_chan()====ch:12
[   42.930091] =====>rtl8192_set_chan()====ch:13
[   43.626200] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   44.725687] ===>rtllib_wx_set_power(): power disable
[   60.129047] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   60.129078] =====>rtl8192_set_chan()====ch:1
[   60.240064] =====>rtl8192_set_chan()====ch:2
[   60.360060] =====>rtl8192_set_chan()====ch:3
[   60.480059] =====>rtl8192_set_chan()====ch:4
[   60.600062] =====>rtl8192_set_chan()====ch:5
[   60.720059] =====>rtl8192_set_chan()====ch:6
[   60.840059] =====>rtl8192_set_chan()====ch:7
[   60.960071] =====>rtl8192_set_chan()====ch:8
[   61.080064] =====>rtl8192_set_chan()====ch:9
[   61.200059] =====>rtl8192_set_chan()====ch:10
[   61.320062] =====>rtl8192_set_chan()====ch:11
[   61.440059] =====>rtl8192_set_chan()====ch:12
[   61.560060] =====>rtl8192_set_chan()====ch:13
[   90.129280] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   90.129312] =====>rtl8192_set_chan()====ch:1
[   90.240064] =====>rtl8192_set_chan()====ch:2
[   90.360059] =====>rtl8192_set_chan()====ch:3
[   90.480059] =====>rtl8192_set_chan()====ch:4
[   90.600056] =====>rtl8192_set_chan()====ch:5
[   90.720066] =====>rtl8192_set_chan()====ch:6
[   90.840061] =====>rtl8192_set_chan()====ch:7
[   90.960068] =====>rtl8192_set_chan()====ch:8
[   91.080060] =====>rtl8192_set_chan()====ch:9
[   91.200059] =====>rtl8192_set_chan()====ch:10
[   91.320060] =====>rtl8192_set_chan()====ch:11
[   91.440059] =====>rtl8192_set_chan()====ch:12
[   91.560060] =====>rtl8192_set_chan()====ch:13
[  128.949002] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  128.949039] =====>rtl8192_set_chan()====ch:1
[  129.060052] =====>rtl8192_set_chan()====ch:2
[  129.180067] =====>rtl8192_set_chan()====ch:3
[  129.300067] =====>rtl8192_set_chan()====ch:4
[  129.410103] =====>rtl8192_set_chan()====ch:5
[  129.530113] =====>rtl8192_set_chan()====ch:6
[  129.650075] =====>rtl8192_set_chan()====ch:7
[  129.770072] =====>rtl8192_set_chan()====ch:8
[  129.890072] =====>rtl8192_set_chan()====ch:9
[  130.010130] =====>rtl8192_set_chan()====ch:10
[  130.130074] =====>rtl8192_set_chan()====ch:11
[  130.250072] =====>rtl8192_set_chan()====ch:12
[  130.370086] =====>rtl8192_set_chan()====ch:13
[  130.490775] alg name:WEP
[  130.512241] ===========>set_swcam():EntryNo is 0,KeyIndex is 0,KeyType is 5,is_mesh is 0
[  130.512394] ===>rtllib_start_scan()
[  130.512449] Linking with SunshineNetwork24TIVO,channel:11, qos:0, myHT:1, networkHT:1, mode:10 cur_net.flags:0x406
[  130.512470] Linking with SunshineNetwork24TIVO,channel:11, qos:0, myHT:1, networkHT:1, mode:10 cur_net.flags:0x406
[  130.512808] ===>rtllib_associate_procedure_wq(), chan:11
[  130.512815] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  130.512820] =====>rtl8192_set_chan()====ch:11
[  130.524639] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  130.530119] Associated successfully
[  130.530128] normal associate
[  130.530143] Using G rates:108
[  130.530149] Successfully associated, ht enabled
[  130.530157] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  130.530164] =====>rtl8192_set_chan()====ch:11
[  130.540203] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  130.540210] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  130.543382] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  130.670629] DHCP pkt src port:68, dest port:67!!
[  131.711133] dm_check_edca_turbo():iot peer is atheros, bssid:00:21:91:ea:a4:a7
[  131.762711] DHCP pkt src port:68, dest port:67!!
[  141.200094] wlan0: no IPv6 routers present
[  180.003295] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  180.003383] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  180.060125] =====>rtl8192_set_chan()====ch:1
[  180.180096] =====>rtl8192_set_chan()====ch:2
[  180.300096] =====>rtl8192_set_chan()====ch:3
[  180.420096] =====>rtl8192_set_chan()====ch:4
[  180.540096] =====>rtl8192_set_chan()====ch:5
[  180.660102] =====>rtl8192_set_chan()====ch:6
[  180.780096] =====>rtl8192_set_chan()====ch:7
[  180.900096] =====>rtl8192_set_chan()====ch:8
[  181.020105] =====>rtl8192_set_chan()====ch:9
[  181.140107] =====>rtl8192_set_chan()====ch:10
[  181.260104] =====>rtl8192_set_chan()====ch:11
[  181.380096] =====>rtl8192_set_chan()====ch:12
[  181.500096] =====>rtl8192_set_chan()====ch:13
[  181.620103] =====>rtl8192_set_chan()====ch:11
[  181.630161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  181.630170] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  220.007141] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  220.007236] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  220.060130] =====>rtl8192_set_chan()====ch:1
[  220.180104] =====>rtl8192_set_chan()====ch:2
[  220.300109] =====>rtl8192_set_chan()====ch:3
[  220.420096] =====>rtl8192_set_chan()====ch:4
[  220.540096] =====>rtl8192_set_chan()====ch:5
[  220.660104] =====>rtl8192_set_chan()====ch:6
[  220.780096] =====>rtl8192_set_chan()====ch:7
[  220.900096] =====>rtl8192_set_chan()====ch:8
[  221.020105] =====>rtl8192_set_chan()====ch:9
[  221.140087] =====>rtl8192_set_chan()====ch:10
[  221.260102] =====>rtl8192_set_chan()====ch:11
[  221.380096] =====>rtl8192_set_chan()====ch:12
[  221.500095] =====>rtl8192_set_chan()====ch:13
[  221.620118] =====>rtl8192_set_chan()====ch:11
[  221.630172] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  221.630181] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  280.007258] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  280.007345] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  280.060135] =====>rtl8192_set_chan()====ch:1
[  280.180103] =====>rtl8192_set_chan()====ch:2
[  280.300098] =====>rtl8192_set_chan()====ch:3
[  280.420096] =====>rtl8192_set_chan()====ch:4
[  280.540096] =====>rtl8192_set_chan()====ch:5
[  280.660103] =====>rtl8192_set_chan()====ch:6
[  280.780096] =====>rtl8192_set_chan()====ch:7
[  280.900096] =====>rtl8192_set_chan()====ch:8
[  281.020105] =====>rtl8192_set_chan()====ch:9
[  281.140104] =====>rtl8192_set_chan()====ch:10
[  281.260359] =====>rtl8192_set_chan()====ch:11
[  281.380094] =====>rtl8192_set_chan()====ch:12
[  281.500096] =====>rtl8192_set_chan()====ch:13
[  281.620104] =====>rtl8192_set_chan()====ch:11
[  281.630161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  281.630169] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  360.003705] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  360.003794] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  360.060126] =====>rtl8192_set_chan()====ch:1
[  360.180098] =====>rtl8192_set_chan()====ch:2
[  360.300096] =====>rtl8192_set_chan()====ch:3
[  360.420102] =====>rtl8192_set_chan()====ch:4
[  360.540096] =====>rtl8192_set_chan()====ch:5
[  360.660096] =====>rtl8192_set_chan()====ch:6
[  360.780103] =====>rtl8192_set_chan()====ch:7
[  360.900096] =====>rtl8192_set_chan()====ch:8
[  361.020105] =====>rtl8192_set_chan()====ch:9
[  361.140111] =====>rtl8192_set_chan()====ch:10
[  361.260096] =====>rtl8192_set_chan()====ch:11
[  361.380096] =====>rtl8192_set_chan()====ch:12
[  361.500102] =====>rtl8192_set_chan()====ch:13
[  361.620117] =====>rtl8192_set_chan()====ch:11
[  361.630174] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  361.630183] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  460.007428] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  460.007545] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  460.060132] =====>rtl8192_set_chan()====ch:1
[  460.180100] =====>rtl8192_set_chan()====ch:2
[  460.300096] =====>rtl8192_set_chan()====ch:3
[  460.420104] =====>rtl8192_set_chan()====ch:4
[  460.540096] =====>rtl8192_set_chan()====ch:5
[  460.660096] =====>rtl8192_set_chan()====ch:6
[  460.780104] =====>rtl8192_set_chan()====ch:7
[  460.900099] =====>rtl8192_set_chan()====ch:8
[  461.020106] =====>rtl8192_set_chan()====ch:9
[  461.140109] =====>rtl8192_set_chan()====ch:10
[  461.260099] =====>rtl8192_set_chan()====ch:11
[  461.380099] =====>rtl8192_set_chan()====ch:12
[  461.500106] =====>rtl8192_set_chan()====ch:13
[  461.620106] =====>rtl8192_set_chan()====ch:11
[  461.630163] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  461.630172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  491.395403] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  580.007712] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  580.007827] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  580.060119] =====>rtl8192_set_chan()====ch:1
[  580.180103] =====>rtl8192_set_chan()====ch:2
[  580.300104] =====>rtl8192_set_chan()====ch:3
[  580.420105] =====>rtl8192_set_chan()====ch:4
[  580.540104] =====>rtl8192_set_chan()====ch:5
[  580.660097] =====>rtl8192_set_chan()====ch:6
[  580.780096] =====>rtl8192_set_chan()====ch:7
[  580.900096] =====>rtl8192_set_chan()====ch:8
[  581.020106] =====>rtl8192_set_chan()====ch:9
[  581.140105] =====>rtl8192_set_chan()====ch:10
[  581.260094] =====>rtl8192_set_chan()====ch:11
[  581.380103] =====>rtl8192_set_chan()====ch:12
[  581.500099] =====>rtl8192_set_chan()====ch:13
[  581.620103] =====>rtl8192_set_chan()====ch:11
[  581.630161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  581.630170] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  680.429028] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  700.007431] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  700.007521] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  700.060116] =====>rtl8192_set_chan()====ch:1
[  700.180117] =====>rtl8192_set_chan()====ch:2
[  700.300097] =====>rtl8192_set_chan()====ch:3
[  700.420102] =====>rtl8192_set_chan()====ch:4
[  700.540104] =====>rtl8192_set_chan()====ch:5
[  700.660096] =====>rtl8192_set_chan()====ch:6
[  700.780063] =====>rtl8192_set_chan()====ch:7
[  700.900066] =====>rtl8192_set_chan()====ch:8
[  701.020049] =====>rtl8192_set_chan()====ch:9
[  701.140107] =====>rtl8192_set_chan()====ch:10
[  701.260106] =====>rtl8192_set_chan()====ch:11
[  701.380060] =====>rtl8192_set_chan()====ch:12
[  701.500068] =====>rtl8192_set_chan()====ch:13
[  701.620110] =====>rtl8192_set_chan()====ch:11
[  701.630170] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  701.630179] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  728.557913] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  736.135339] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  745.452424] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  822.010469] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  822.010578] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  822.070126] =====>rtl8192_set_chan()====ch:1
[  822.190044] =====>rtl8192_set_chan()====ch:2
[  822.310098] =====>rtl8192_set_chan()====ch:3
[  822.430097] =====>rtl8192_set_chan()====ch:4
[  822.550097] =====>rtl8192_set_chan()====ch:5
[  822.670105] =====>rtl8192_set_chan()====ch:6
[  822.790097] =====>rtl8192_set_chan()====ch:7
[  822.910097] =====>rtl8192_set_chan()====ch:8
[  823.030106] =====>rtl8192_set_chan()====ch:9
[  823.150097] =====>rtl8192_set_chan()====ch:10
[  823.270112] =====>rtl8192_set_chan()====ch:11
[  823.390100] =====>rtl8192_set_chan()====ch:12
[  823.510097] =====>rtl8192_set_chan()====ch:13
[  823.630105] =====>rtl8192_set_chan()====ch:11
[  823.640163] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  823.640172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[  860.247331] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  940.007614] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[  940.007705] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  940.060111] =====>rtl8192_set_chan()====ch:1
[  940.180097] =====>rtl8192_set_chan()====ch:2
[  940.300097] =====>rtl8192_set_chan()====ch:3
[  940.420046] =====>rtl8192_set_chan()====ch:4
[  940.540109] =====>rtl8192_set_chan()====ch:5
[  940.660055] =====>rtl8192_set_chan()====ch:6
[  940.780106] =====>rtl8192_set_chan()====ch:7
[  940.900104] =====>rtl8192_set_chan()====ch:8
[  941.020097] =====>rtl8192_set_chan()====ch:9
[  941.140055] =====>rtl8192_set_chan()====ch:10
[  941.260044] =====>rtl8192_set_chan()====ch:11
[  941.380106] =====>rtl8192_set_chan()====ch:12
[  941.500097] =====>rtl8192_set_chan()====ch:13
[  941.620103] =====>rtl8192_set_chan()====ch:11
[  941.630163] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  941.630173] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1060.007331] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1060.007421] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1060.060131] =====>rtl8192_set_chan()====ch:1
[ 1060.180099] =====>rtl8192_set_chan()====ch:2
[ 1060.300104] =====>rtl8192_set_chan()====ch:3
[ 1060.420105] =====>rtl8192_set_chan()====ch:4
[ 1060.540105] =====>rtl8192_set_chan()====ch:5
[ 1060.660116] =====>rtl8192_set_chan()====ch:6
[ 1060.780108] =====>rtl8192_set_chan()====ch:7
[ 1060.900119] =====>rtl8192_set_chan()====ch:8
[ 1061.020108] =====>rtl8192_set_chan()====ch:9
[ 1061.140108] =====>rtl8192_set_chan()====ch:10
[ 1061.260405] =====>rtl8192_set_chan()====ch:11
[ 1061.380055] =====>rtl8192_set_chan()====ch:12
[ 1061.500097] =====>rtl8192_set_chan()====ch:13
[ 1061.620110] =====>rtl8192_set_chan()====ch:11
[ 1061.630169] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1061.630178] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1129.356979] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1157.006406] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1180.007014] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1180.007103] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1180.060153] =====>rtl8192_set_chan()====ch:1
[ 1180.180102] =====>rtl8192_set_chan()====ch:2
[ 1180.300103] =====>rtl8192_set_chan()====ch:3
[ 1180.420105] =====>rtl8192_set_chan()====ch:4
[ 1180.540113] =====>rtl8192_set_chan()====ch:5
[ 1180.660097] =====>rtl8192_set_chan()====ch:6
[ 1180.780097] =====>rtl8192_set_chan()====ch:7
[ 1180.900097] =====>rtl8192_set_chan()====ch:8
[ 1181.020106] =====>rtl8192_set_chan()====ch:9
[ 1181.140105] =====>rtl8192_set_chan()====ch:10
[ 1181.260395] =====>rtl8192_set_chan()====ch:11
[ 1181.380066] =====>rtl8192_set_chan()====ch:12
[ 1181.500096] =====>rtl8192_set_chan()====ch:13
[ 1181.620102] =====>rtl8192_set_chan()====ch:11
[ 1181.630163] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1181.630172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1233.396272] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1300.007581] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1300.007672] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1300.060198] =====>rtl8192_set_chan()====ch:1
[ 1300.180112] =====>rtl8192_set_chan()====ch:2
[ 1300.300100] =====>rtl8192_set_chan()====ch:3
[ 1300.420097] =====>rtl8192_set_chan()====ch:4
[ 1300.540104] =====>rtl8192_set_chan()====ch:5
[ 1300.660096] =====>rtl8192_set_chan()====ch:6
[ 1300.780102] =====>rtl8192_set_chan()====ch:7
[ 1300.900109] =====>rtl8192_set_chan()====ch:8
[ 1301.020046] =====>rtl8192_set_chan()====ch:9
[ 1301.140103] =====>rtl8192_set_chan()====ch:10
[ 1301.260108] =====>rtl8192_set_chan()====ch:11
[ 1301.380068] =====>rtl8192_set_chan()====ch:12
[ 1301.500101] =====>rtl8192_set_chan()====ch:13
[ 1301.620112] =====>rtl8192_set_chan()====ch:11
[ 1301.630172] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1301.630181] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1420.007022] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1420.007114] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1420.060125] =====>rtl8192_set_chan()====ch:1
[ 1420.180102] =====>rtl8192_set_chan()====ch:2
[ 1420.300147] =====>rtl8192_set_chan()====ch:3
[ 1420.420066] =====>rtl8192_set_chan()====ch:4
[ 1420.540041] =====>rtl8192_set_chan()====ch:5
[ 1420.660040] =====>rtl8192_set_chan()====ch:6
[ 1420.780035] =====>rtl8192_set_chan()====ch:7
[ 1420.900042] =====>rtl8192_set_chan()====ch:8
[ 1421.020044] =====>rtl8192_set_chan()====ch:9
[ 1421.140043] =====>rtl8192_set_chan()====ch:10
[ 1421.260040] =====>rtl8192_set_chan()====ch:11
[ 1421.380065] =====>rtl8192_set_chan()====ch:12
[ 1421.500049] =====>rtl8192_set_chan()====ch:13
[ 1421.620048] =====>rtl8192_set_chan()====ch:11
[ 1421.630107] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1421.630118] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1430.215855] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1542.009619] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1542.060077] =====>rtl8192_set_chan()====ch:1
[ 1542.180105] =====>rtl8192_set_chan()====ch:2
[ 1542.300108] =====>rtl8192_set_chan()====ch:3
[ 1542.420097] =====>rtl8192_set_chan()====ch:4
[ 1542.540097] =====>rtl8192_set_chan()====ch:5
[ 1542.660112] =====>rtl8192_set_chan()====ch:6
[ 1542.780100] =====>rtl8192_set_chan()====ch:7
[ 1542.900097] =====>rtl8192_set_chan()====ch:8
[ 1543.020099] =====>rtl8192_set_chan()====ch:9
[ 1543.140086] =====>rtl8192_set_chan()====ch:10
[ 1543.260102] =====>rtl8192_set_chan()====ch:11
[ 1543.380108] =====>rtl8192_set_chan()====ch:12
[ 1543.500265] =====>rtl8192_set_chan()====ch:13
[ 1543.620107] =====>rtl8192_set_chan()====ch:11
[ 1543.630166] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1543.630175] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1618.326425] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1660.007033] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1660.007121] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1660.060137] =====>rtl8192_set_chan()====ch:1
[ 1660.180109] =====>rtl8192_set_chan()====ch:2
[ 1660.300104] =====>rtl8192_set_chan()====ch:3
[ 1660.420102] =====>rtl8192_set_chan()====ch:4
[ 1660.540103] =====>rtl8192_set_chan()====ch:5
[ 1660.660103] =====>rtl8192_set_chan()====ch:6
[ 1660.780103] =====>rtl8192_set_chan()====ch:7
[ 1660.900103] =====>rtl8192_set_chan()====ch:8
[ 1661.020113] =====>rtl8192_set_chan()====ch:9
[ 1661.140111] =====>rtl8192_set_chan()====ch:10
[ 1661.260406] =====>rtl8192_set_chan()====ch:11
[ 1661.380103] =====>rtl8192_set_chan()====ch:12
[ 1661.500102] =====>rtl8192_set_chan()====ch:13
[ 1661.620110] =====>rtl8192_set_chan()====ch:11
[ 1661.630168] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1661.630177] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1780.005964] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1780.006055] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1780.060118] =====>rtl8192_set_chan()====ch:1
[ 1780.180105] =====>rtl8192_set_chan()====ch:2
[ 1780.300104] =====>rtl8192_set_chan()====ch:3
[ 1780.420105] =====>rtl8192_set_chan()====ch:4
[ 1780.540104] =====>rtl8192_set_chan()====ch:5
[ 1780.660121] =====>rtl8192_set_chan()====ch:6
[ 1780.780106] =====>rtl8192_set_chan()====ch:7
[ 1780.900106] =====>rtl8192_set_chan()====ch:8
[ 1781.020106] =====>rtl8192_set_chan()====ch:9
[ 1781.140107] =====>rtl8192_set_chan()====ch:10
[ 1781.260106] =====>rtl8192_set_chan()====ch:11
[ 1781.380107] =====>rtl8192_set_chan()====ch:12
[ 1781.500193] =====>rtl8192_set_chan()====ch:13
[ 1781.620904] =====>rtl8192_set_chan()====ch:11
[ 1781.630962] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1781.630971] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 1900.007313] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1900.007397] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1900.060130] =====>rtl8192_set_chan()====ch:1
[ 1900.180106] =====>rtl8192_set_chan()====ch:2
[ 1900.300099] =====>rtl8192_set_chan()====ch:3
[ 1900.420097] =====>rtl8192_set_chan()====ch:4
[ 1900.540096] =====>rtl8192_set_chan()====ch:5
[ 1900.660097] =====>rtl8192_set_chan()====ch:6
[ 1900.780096] =====>rtl8192_set_chan()====ch:7
[ 1900.900097] =====>rtl8192_set_chan()====ch:8
[ 1901.020105] =====>rtl8192_set_chan()====ch:9
[ 1901.140090] =====>rtl8192_set_chan()====ch:10
[ 1901.260096] =====>rtl8192_set_chan()====ch:11
[ 1901.380097] =====>rtl8192_set_chan()====ch:12
[ 1901.500096] =====>rtl8192_set_chan()====ch:13
[ 1901.620105] =====>rtl8192_set_chan()====ch:11
[ 1901.630159] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1901.630168] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2020.007261] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2020.007349] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2020.060119] =====>rtl8192_set_chan()====ch:1
[ 2020.180105] =====>rtl8192_set_chan()====ch:2
[ 2020.300102] =====>rtl8192_set_chan()====ch:3
[ 2020.420097] =====>rtl8192_set_chan()====ch:4
[ 2020.540096] =====>rtl8192_set_chan()====ch:5
[ 2020.660118] =====>rtl8192_set_chan()====ch:6
[ 2020.780097] =====>rtl8192_set_chan()====ch:7
[ 2020.900096] =====>rtl8192_set_chan()====ch:8
[ 2021.020106] =====>rtl8192_set_chan()====ch:9
[ 2021.140106] =====>rtl8192_set_chan()====ch:10
[ 2021.260106] =====>rtl8192_set_chan()====ch:11
[ 2021.380096] =====>rtl8192_set_chan()====ch:12
[ 2021.500096] =====>rtl8192_set_chan()====ch:13
[ 2021.620104] =====>rtl8192_set_chan()====ch:11
[ 2021.630161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2021.630170] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2140.007511] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2140.007624] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2140.060134] =====>rtl8192_set_chan()====ch:1
[ 2140.180103] =====>rtl8192_set_chan()====ch:2
[ 2140.300098] =====>rtl8192_set_chan()====ch:3
[ 2140.420102] =====>rtl8192_set_chan()====ch:4
[ 2140.540095] =====>rtl8192_set_chan()====ch:5
[ 2140.660096] =====>rtl8192_set_chan()====ch:6
[ 2140.780102] =====>rtl8192_set_chan()====ch:7
[ 2140.900096] =====>rtl8192_set_chan()====ch:8
[ 2141.020107] =====>rtl8192_set_chan()====ch:9
[ 2141.140124] =====>rtl8192_set_chan()====ch:10
[ 2141.260386] =====>rtl8192_set_chan()====ch:11
[ 2141.380095] =====>rtl8192_set_chan()====ch:12
[ 2141.500102] =====>rtl8192_set_chan()====ch:13
[ 2141.620113] =====>rtl8192_set_chan()====ch:11
[ 2141.630171] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2141.630180] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2260.006994] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2260.007107] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2260.060135] =====>rtl8192_set_chan()====ch:1
[ 2260.180102] =====>rtl8192_set_chan()====ch:2
[ 2260.300098] =====>rtl8192_set_chan()====ch:3
[ 2260.420078] =====>rtl8192_set_chan()====ch:4
[ 2260.540096] =====>rtl8192_set_chan()====ch:5
[ 2260.660103] =====>rtl8192_set_chan()====ch:6
[ 2260.780102] =====>rtl8192_set_chan()====ch:7
[ 2260.900096] =====>rtl8192_set_chan()====ch:8
[ 2261.020105] =====>rtl8192_set_chan()====ch:9
[ 2261.140112] =====>rtl8192_set_chan()====ch:10
[ 2261.260396] =====>rtl8192_set_chan()====ch:11
[ 2261.380096] =====>rtl8192_set_chan()====ch:12
[ 2261.500102] =====>rtl8192_set_chan()====ch:13
[ 2261.620103] =====>rtl8192_set_chan()====ch:11
[ 2261.630161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2261.630170] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2281.171842] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2380.007427] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2380.007516] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2380.060129] =====>rtl8192_set_chan()====ch:1
[ 2380.180108] =====>rtl8192_set_chan()====ch:2
[ 2380.300104] =====>rtl8192_set_chan()====ch:3
[ 2380.420108] =====>rtl8192_set_chan()====ch:4
[ 2380.540106] =====>rtl8192_set_chan()====ch:5
[ 2380.660103] =====>rtl8192_set_chan()====ch:6
[ 2380.780117] =====>rtl8192_set_chan()====ch:7
[ 2380.900104] =====>rtl8192_set_chan()====ch:8
[ 2381.020102] =====>rtl8192_set_chan()====ch:9
[ 2381.140113] =====>rtl8192_set_chan()====ch:10
[ 2381.260406] =====>rtl8192_set_chan()====ch:11
[ 2381.380098] =====>rtl8192_set_chan()====ch:12
[ 2381.500110] =====>rtl8192_set_chan()====ch:13
[ 2381.620108] =====>rtl8192_set_chan()====ch:11
[ 2381.630167] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2381.630176] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2428.083086] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2500.007959] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2500.008048] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2500.060132] =====>rtl8192_set_chan()====ch:1
[ 2500.180103] =====>rtl8192_set_chan()====ch:2
[ 2500.300100] =====>rtl8192_set_chan()====ch:3
[ 2500.420101] =====>rtl8192_set_chan()====ch:4
[ 2500.540075] =====>rtl8192_set_chan()====ch:5
[ 2500.660107] =====>rtl8192_set_chan()====ch:6
[ 2500.780097] =====>rtl8192_set_chan()====ch:7
[ 2500.900105] =====>rtl8192_set_chan()====ch:8
[ 2501.020105] =====>rtl8192_set_chan()====ch:9
[ 2501.130107] =====>rtl8192_set_chan()====ch:10
[ 2501.250102] =====>rtl8192_set_chan()====ch:11
[ 2501.370101] =====>rtl8192_set_chan()====ch:12
[ 2501.490101] =====>rtl8192_set_chan()====ch:13
[ 2501.610094] =====>rtl8192_set_chan()====ch:11
[ 2501.620161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2501.620172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2508.503700] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2589.603877] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2620.007149] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2620.007254] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2620.060133] =====>rtl8192_set_chan()====ch:1
[ 2620.180096] =====>rtl8192_set_chan()====ch:2
[ 2620.300097] =====>rtl8192_set_chan()====ch:3
[ 2620.420096] =====>rtl8192_set_chan()====ch:4
[ 2620.540096] =====>rtl8192_set_chan()====ch:5
[ 2620.660113] =====>rtl8192_set_chan()====ch:6
[ 2620.780098] =====>rtl8192_set_chan()====ch:7
[ 2620.900096] =====>rtl8192_set_chan()====ch:8
[ 2621.020071] =====>rtl8192_set_chan()====ch:9
[ 2621.140104] =====>rtl8192_set_chan()====ch:10
[ 2621.260115] =====>rtl8192_set_chan()====ch:11
[ 2621.380096] =====>rtl8192_set_chan()====ch:12
[ 2621.500096] =====>rtl8192_set_chan()====ch:13
[ 2621.620108] =====>rtl8192_set_chan()====ch:11
[ 2621.630171] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2621.630181] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2740.007281] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2740.007381] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2740.060135] =====>rtl8192_set_chan()====ch:1
[ 2740.180108] =====>rtl8192_set_chan()====ch:2
[ 2740.300105] =====>rtl8192_set_chan()====ch:3
[ 2740.420105] =====>rtl8192_set_chan()====ch:4
[ 2740.540105] =====>rtl8192_set_chan()====ch:5
[ 2740.660105] =====>rtl8192_set_chan()====ch:6
[ 2740.780104] =====>rtl8192_set_chan()====ch:7
[ 2740.900105] =====>rtl8192_set_chan()====ch:8
[ 2741.020118] =====>rtl8192_set_chan()====ch:9
[ 2741.140090] =====>rtl8192_set_chan()====ch:10
[ 2741.260151] =====>rtl8192_set_chan()====ch:11
[ 2741.380098] =====>rtl8192_set_chan()====ch:12
[ 2741.500096] =====>rtl8192_set_chan()====ch:13
[ 2741.620105] =====>rtl8192_set_chan()====ch:11
[ 2741.630160] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2741.630169] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2860.007045] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2860.007150] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2860.060137] =====>rtl8192_set_chan()====ch:1
[ 2860.180104] =====>rtl8192_set_chan()====ch:2
[ 2860.300101] =====>rtl8192_set_chan()====ch:3
[ 2860.420105] =====>rtl8192_set_chan()====ch:4
[ 2860.540096] =====>rtl8192_set_chan()====ch:5
[ 2860.660097] =====>rtl8192_set_chan()====ch:6
[ 2860.780104] =====>rtl8192_set_chan()====ch:7
[ 2860.900098] =====>rtl8192_set_chan()====ch:8
[ 2861.020106] =====>rtl8192_set_chan()====ch:9
[ 2861.140097] =====>rtl8192_set_chan()====ch:10
[ 2861.260100] =====>rtl8192_set_chan()====ch:11
[ 2861.380095] =====>rtl8192_set_chan()====ch:12
[ 2861.500103] =====>rtl8192_set_chan()====ch:13
[ 2861.620105] =====>rtl8192_set_chan()====ch:11
[ 2861.629242] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2861.629251] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 2980.007335] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2980.007433] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2980.060122] =====>rtl8192_set_chan()====ch:1
[ 2980.180109] =====>rtl8192_set_chan()====ch:2
[ 2980.300102] =====>rtl8192_set_chan()====ch:3
[ 2980.420118] =====>rtl8192_set_chan()====ch:4
[ 2980.540103] =====>rtl8192_set_chan()====ch:5
[ 2980.660112] =====>rtl8192_set_chan()====ch:6
[ 2980.780102] =====>rtl8192_set_chan()====ch:7
[ 2980.900102] =====>rtl8192_set_chan()====ch:8
[ 2981.020113] =====>rtl8192_set_chan()====ch:9
[ 2981.140111] =====>rtl8192_set_chan()====ch:10
[ 2981.260111] =====>rtl8192_set_chan()====ch:11
[ 2981.380102] =====>rtl8192_set_chan()====ch:12
[ 2981.500103] =====>rtl8192_set_chan()====ch:13
[ 2981.620109] =====>rtl8192_set_chan()====ch:11
[ 2981.630166] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2981.630175] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3043.757030] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3100.007736] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3100.007827] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3100.060163] =====>rtl8192_set_chan()====ch:1
[ 3100.180112] =====>rtl8192_set_chan()====ch:2
[ 3100.300070] =====>rtl8192_set_chan()====ch:3
[ 3100.420101] =====>rtl8192_set_chan()====ch:4
[ 3100.540108] =====>rtl8192_set_chan()====ch:5
[ 3100.660073] =====>rtl8192_set_chan()====ch:6
[ 3100.780098] =====>rtl8192_set_chan()====ch:7
[ 3100.900113] =====>rtl8192_set_chan()====ch:8
[ 3101.020106] =====>rtl8192_set_chan()====ch:9
[ 3101.140049] =====>rtl8192_set_chan()====ch:10
[ 3101.260054] =====>rtl8192_set_chan()====ch:11
[ 3101.380043] =====>rtl8192_set_chan()====ch:12
[ 3101.500101] =====>rtl8192_set_chan()====ch:13
[ 3101.620051] =====>rtl8192_set_chan()====ch:11
[ 3101.630113] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3101.630123] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3220.007459] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3220.060121] =====>rtl8192_set_chan()====ch:1
[ 3220.180099] =====>rtl8192_set_chan()====ch:2
[ 3220.300097] =====>rtl8192_set_chan()====ch:3
[ 3220.420070] =====>rtl8192_set_chan()====ch:4
[ 3220.540063] =====>rtl8192_set_chan()====ch:5
[ 3220.660047] =====>rtl8192_set_chan()====ch:6
[ 3220.780071] =====>rtl8192_set_chan()====ch:7
[ 3220.900110] =====>rtl8192_set_chan()====ch:8
[ 3221.020053] =====>rtl8192_set_chan()====ch:9
[ 3221.141072] =====>rtl8192_set_chan()====ch:10
[ 3221.260072] =====>rtl8192_set_chan()====ch:11
[ 3221.380069] =====>rtl8192_set_chan()====ch:12
[ 3221.500070] =====>rtl8192_set_chan()====ch:13
[ 3221.620077] =====>rtl8192_set_chan()====ch:11
[ 3221.630136] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3221.630145] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3340.007211] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3340.007299] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3340.060124] =====>rtl8192_set_chan()====ch:1
[ 3340.180098] =====>rtl8192_set_chan()====ch:2
[ 3340.300097] =====>rtl8192_set_chan()====ch:3
[ 3340.420063] =====>rtl8192_set_chan()====ch:4
[ 3340.540099] =====>rtl8192_set_chan()====ch:5
[ 3340.660104] =====>rtl8192_set_chan()====ch:6
[ 3340.780097] =====>rtl8192_set_chan()====ch:7
[ 3340.900097] =====>rtl8192_set_chan()====ch:8
[ 3341.020105] =====>rtl8192_set_chan()====ch:9
[ 3341.140104] =====>rtl8192_set_chan()====ch:10
[ 3341.260112] =====>rtl8192_set_chan()====ch:11
[ 3341.380097] =====>rtl8192_set_chan()====ch:12
[ 3341.500101] =====>rtl8192_set_chan()====ch:13
[ 3341.620103] =====>rtl8192_set_chan()====ch:11
[ 3341.630163] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3341.630172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3398.477307] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3460.007435] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3460.007526] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3460.060142] =====>rtl8192_set_chan()====ch:1
[ 3460.180106] =====>rtl8192_set_chan()====ch:2
[ 3460.300066] =====>rtl8192_set_chan()====ch:3
[ 3460.420096] =====>rtl8192_set_chan()====ch:4
[ 3460.540100] =====>rtl8192_set_chan()====ch:5
[ 3460.660096] =====>rtl8192_set_chan()====ch:6
[ 3460.780096] =====>rtl8192_set_chan()====ch:7
[ 3460.900120] =====>rtl8192_set_chan()====ch:8
[ 3461.020105] =====>rtl8192_set_chan()====ch:9
[ 3461.140106] =====>rtl8192_set_chan()====ch:10
[ 3461.260398] =====>rtl8192_set_chan()====ch:11
[ 3461.380097] =====>rtl8192_set_chan()====ch:12
[ 3461.500098] =====>rtl8192_set_chan()====ch:13
[ 3461.620114] =====>rtl8192_set_chan()====ch:11
[ 3461.630173] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3461.630182] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3580.007307] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3580.007424] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3580.060119] =====>rtl8192_set_chan()====ch:1
[ 3580.180105] =====>rtl8192_set_chan()====ch:2
[ 3580.300101] =====>rtl8192_set_chan()====ch:3
[ 3580.420098] =====>rtl8192_set_chan()====ch:4
[ 3580.540097] =====>rtl8192_set_chan()====ch:5
[ 3580.660107] =====>rtl8192_set_chan()====ch:6
[ 3580.780105] =====>rtl8192_set_chan()====ch:7
[ 3580.900104] =====>rtl8192_set_chan()====ch:8
[ 3581.020113] =====>rtl8192_set_chan()====ch:9
[ 3581.140112] =====>rtl8192_set_chan()====ch:10
[ 3581.260102] =====>rtl8192_set_chan()====ch:11
[ 3581.380104] =====>rtl8192_set_chan()====ch:12
[ 3581.500107] =====>rtl8192_set_chan()====ch:13
[ 3581.620117] =====>rtl8192_set_chan()====ch:11
[ 3581.630176] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3581.630186] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3591.094104] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3700.007830] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3700.007946] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3700.060129] =====>rtl8192_set_chan()====ch:1
[ 3700.180105] =====>rtl8192_set_chan()====ch:2
[ 3700.300070] =====>rtl8192_set_chan()====ch:3
[ 3700.420111] =====>rtl8192_set_chan()====ch:4
[ 3700.540109] =====>rtl8192_set_chan()====ch:5
[ 3700.660110] =====>rtl8192_set_chan()====ch:6
[ 3700.780103] =====>rtl8192_set_chan()====ch:7
[ 3700.900125] =====>rtl8192_set_chan()====ch:8
[ 3701.020105] =====>rtl8192_set_chan()====ch:9
[ 3701.140087] =====>rtl8192_set_chan()====ch:10
[ 3701.260099] =====>rtl8192_set_chan()====ch:11
[ 3701.380096] =====>rtl8192_set_chan()====ch:12
[ 3701.500100] =====>rtl8192_set_chan()====ch:13
[ 3701.620104] =====>rtl8192_set_chan()====ch:11
[ 3701.630160] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3701.630168] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3820.007568] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3820.007653] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3820.060133] =====>rtl8192_set_chan()====ch:1
[ 3820.180110] =====>rtl8192_set_chan()====ch:2
[ 3820.300106] =====>rtl8192_set_chan()====ch:3
[ 3820.420088] =====>rtl8192_set_chan()====ch:4
[ 3820.540098] =====>rtl8192_set_chan()====ch:5
[ 3820.660097] =====>rtl8192_set_chan()====ch:6
[ 3820.780100] =====>rtl8192_set_chan()====ch:7
[ 3820.900096] =====>rtl8192_set_chan()====ch:8
[ 3821.020102] =====>rtl8192_set_chan()====ch:9
[ 3821.140091] =====>rtl8192_set_chan()====ch:10
[ 3821.260391] =====>rtl8192_set_chan()====ch:11
[ 3821.380098] =====>rtl8192_set_chan()====ch:12
[ 3821.500103] =====>rtl8192_set_chan()====ch:13
[ 3821.620113] =====>rtl8192_set_chan()====ch:11
[ 3821.630169] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3821.630178] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 3940.003547] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3940.003635] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3940.060132] =====>rtl8192_set_chan()====ch:1
[ 3940.180121] =====>rtl8192_set_chan()====ch:2
[ 3940.300096] =====>rtl8192_set_chan()====ch:3
[ 3940.420096] =====>rtl8192_set_chan()====ch:4
[ 3940.540096] =====>rtl8192_set_chan()====ch:5
[ 3940.660098] =====>rtl8192_set_chan()====ch:6
[ 3940.780103] =====>rtl8192_set_chan()====ch:7
[ 3940.900096] =====>rtl8192_set_chan()====ch:8
[ 3941.020105] =====>rtl8192_set_chan()====ch:9
[ 3941.140104] =====>rtl8192_set_chan()====ch:10
[ 3941.260105] =====>rtl8192_set_chan()====ch:11
[ 3941.380104] =====>rtl8192_set_chan()====ch:12
[ 3941.500109] =====>rtl8192_set_chan()====ch:13
[ 3941.620103] =====>rtl8192_set_chan()====ch:11
[ 3941.630160] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3941.630168] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4060.007809] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4060.007899] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4060.060110] =====>rtl8192_set_chan()====ch:1
[ 4060.180112] =====>rtl8192_set_chan()====ch:2
[ 4060.300098] =====>rtl8192_set_chan()====ch:3
[ 4060.420071] =====>rtl8192_set_chan()====ch:4
[ 4060.540100] =====>rtl8192_set_chan()====ch:5
[ 4060.660113] =====>rtl8192_set_chan()====ch:6
[ 4060.780143] =====>rtl8192_set_chan()====ch:7
[ 4060.900096] =====>rtl8192_set_chan()====ch:8
[ 4061.020106] =====>rtl8192_set_chan()====ch:9
[ 4061.140103] =====>rtl8192_set_chan()====ch:10
[ 4061.260072] =====>rtl8192_set_chan()====ch:11
[ 4061.380112] =====>rtl8192_set_chan()====ch:12
[ 4061.500107] =====>rtl8192_set_chan()====ch:13
[ 4061.620112] =====>rtl8192_set_chan()====ch:11
[ 4061.630171] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4061.630180] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4083.710436] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4176.523086] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4180.007975] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4180.008090] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4180.060080] =====>rtl8192_set_chan()====ch:1
[ 4180.180089] =====>rtl8192_set_chan()====ch:2
[ 4180.300097] =====>rtl8192_set_chan()====ch:3
[ 4180.420112] =====>rtl8192_set_chan()====ch:4
[ 4180.540071] =====>rtl8192_set_chan()====ch:5
[ 4180.660107] =====>rtl8192_set_chan()====ch:6
[ 4180.780113] =====>rtl8192_set_chan()====ch:7
[ 4180.900106] =====>rtl8192_set_chan()====ch:8
[ 4181.020104] =====>rtl8192_set_chan()====ch:9
[ 4181.140101] =====>rtl8192_set_chan()====ch:10
[ 4181.260114] =====>rtl8192_set_chan()====ch:11
[ 4181.380096] =====>rtl8192_set_chan()====ch:12
[ 4181.500106] =====>rtl8192_set_chan()====ch:13
[ 4181.620113] =====>rtl8192_set_chan()====ch:11
[ 4181.630172] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4181.630181] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4288.351217] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4300.007311] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4300.007401] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4300.060139] =====>rtl8192_set_chan()====ch:1
[ 4300.180097] =====>rtl8192_set_chan()====ch:2
[ 4300.300075] =====>rtl8192_set_chan()====ch:3
[ 4300.420098] =====>rtl8192_set_chan()====ch:4
[ 4300.540105] =====>rtl8192_set_chan()====ch:5
[ 4300.660102] =====>rtl8192_set_chan()====ch:6
[ 4300.780096] =====>rtl8192_set_chan()====ch:7
[ 4300.900096] =====>rtl8192_set_chan()====ch:8
[ 4301.020104] =====>rtl8192_set_chan()====ch:9
[ 4301.140108] =====>rtl8192_set_chan()====ch:10
[ 4301.260397] =====>rtl8192_set_chan()====ch:11
[ 4301.380096] =====>rtl8192_set_chan()====ch:12
[ 4301.500096] =====>rtl8192_set_chan()====ch:13
[ 4301.620104] =====>rtl8192_set_chan()====ch:11
[ 4301.630162] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4301.630172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4325.619581] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4420.007115] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4420.007204] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4420.060144] =====>rtl8192_set_chan()====ch:1
[ 4420.180098] =====>rtl8192_set_chan()====ch:2
[ 4420.300098] =====>rtl8192_set_chan()====ch:3
[ 4420.420405] =====>rtl8192_set_chan()====ch:4
[ 4420.540097] =====>rtl8192_set_chan()====ch:5
[ 4420.660100] =====>rtl8192_set_chan()====ch:6
[ 4420.780105] =====>rtl8192_set_chan()====ch:7
[ 4420.900097] =====>rtl8192_set_chan()====ch:8
[ 4421.020109] =====>rtl8192_set_chan()====ch:9
[ 4421.140112] =====>rtl8192_set_chan()====ch:10
[ 4421.260101] =====>rtl8192_set_chan()====ch:11
[ 4421.380112] =====>rtl8192_set_chan()====ch:12
[ 4421.500106] =====>rtl8192_set_chan()====ch:13
[ 4421.620106] =====>rtl8192_set_chan()====ch:11
[ 4421.630165] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4421.630174] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4540.007484] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4540.007573] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4540.060117] =====>rtl8192_set_chan()====ch:1
[ 4540.180113] =====>rtl8192_set_chan()====ch:2
[ 4540.300105] =====>rtl8192_set_chan()====ch:3
[ 4540.420101] =====>rtl8192_set_chan()====ch:4
[ 4540.540096] =====>rtl8192_set_chan()====ch:5
[ 4540.660104] =====>rtl8192_set_chan()====ch:6
[ 4540.780097] =====>rtl8192_set_chan()====ch:7
[ 4540.900101] =====>rtl8192_set_chan()====ch:8
[ 4541.020111] =====>rtl8192_set_chan()====ch:9
[ 4541.140105] =====>rtl8192_set_chan()====ch:10
[ 4541.260098] =====>rtl8192_set_chan()====ch:11
[ 4541.380101] =====>rtl8192_set_chan()====ch:12
[ 4541.500098] =====>rtl8192_set_chan()====ch:13
[ 4541.620122] =====>rtl8192_set_chan()====ch:11
[ 4541.630180] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4541.630189] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4660.000940] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4660.001022] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4660.060139] =====>rtl8192_set_chan()====ch:1
[ 4660.180070] =====>rtl8192_set_chan()====ch:2
[ 4660.300113] =====>rtl8192_set_chan()====ch:3
[ 4660.420113] =====>rtl8192_set_chan()====ch:4
[ 4660.540071] =====>rtl8192_set_chan()====ch:5
[ 4660.660139] =====>rtl8192_set_chan()====ch:6
[ 4660.780069] =====>rtl8192_set_chan()====ch:7
[ 4660.900086] =====>rtl8192_set_chan()====ch:8
[ 4661.020051] =====>rtl8192_set_chan()====ch:9
[ 4661.140107] =====>rtl8192_set_chan()====ch:10
[ 4661.260117] =====>rtl8192_set_chan()====ch:11
[ 4661.380098] =====>rtl8192_set_chan()====ch:12
[ 4661.500081] =====>rtl8192_set_chan()====ch:13
[ 4661.620064] =====>rtl8192_set_chan()====ch:11
[ 4661.630117] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4661.630122] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4780.007029] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4780.007136] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4780.060124] =====>rtl8192_set_chan()====ch:1
[ 4780.180104] =====>rtl8192_set_chan()====ch:2
[ 4780.300101] =====>rtl8192_set_chan()====ch:3
[ 4780.420097] =====>rtl8192_set_chan()====ch:4
[ 4780.540106] =====>rtl8192_set_chan()====ch:5
[ 4780.660098] =====>rtl8192_set_chan()====ch:6
[ 4780.780098] =====>rtl8192_set_chan()====ch:7
[ 4780.900104] =====>rtl8192_set_chan()====ch:8
[ 4781.020107] =====>rtl8192_set_chan()====ch:9
[ 4781.140089] =====>rtl8192_set_chan()====ch:10
[ 4781.260098] =====>rtl8192_set_chan()====ch:11
[ 4781.380086] =====>rtl8192_set_chan()====ch:12
[ 4781.500104] =====>rtl8192_set_chan()====ch:13
[ 4781.620105] =====>rtl8192_set_chan()====ch:11
[ 4781.630161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4781.630170] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 4900.007866] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4900.060121] =====>rtl8192_set_chan()====ch:1
[ 4900.180104] =====>rtl8192_set_chan()====ch:2
[ 4900.300100] =====>rtl8192_set_chan()====ch:3
[ 4900.420106] =====>rtl8192_set_chan()====ch:4
[ 4900.540097] =====>rtl8192_set_chan()====ch:5
[ 4900.660097] =====>rtl8192_set_chan()====ch:6
[ 4900.780095] =====>rtl8192_set_chan()====ch:7
[ 4900.900098] =====>rtl8192_set_chan()====ch:8
[ 4901.020114] =====>rtl8192_set_chan()====ch:9
[ 4901.140087] =====>rtl8192_set_chan()====ch:10
[ 4901.260111] =====>rtl8192_set_chan()====ch:11
[ 4901.380096] =====>rtl8192_set_chan()====ch:12
[ 4901.500096] =====>rtl8192_set_chan()====ch:13
[ 4901.620113] =====>rtl8192_set_chan()====ch:11
[ 4901.630168] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4901.630178] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 5020.007393] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5020.007482] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5020.060119] =====>rtl8192_set_chan()====ch:1
[ 5020.180104] =====>rtl8192_set_chan()====ch:2
[ 5020.300072] =====>rtl8192_set_chan()====ch:3
[ 5020.420102] =====>rtl8192_set_chan()====ch:4
[ 5020.540102] =====>rtl8192_set_chan()====ch:5
[ 5020.660103] =====>rtl8192_set_chan()====ch:6
[ 5020.780102] =====>rtl8192_set_chan()====ch:7
[ 5020.900104] =====>rtl8192_set_chan()====ch:8
[ 5021.020113] =====>rtl8192_set_chan()====ch:9
[ 5021.140111] =====>rtl8192_set_chan()====ch:10
[ 5021.260108] =====>rtl8192_set_chan()====ch:11
[ 5021.380102] =====>rtl8192_set_chan()====ch:12
[ 5021.500102] =====>rtl8192_set_chan()====ch:13
[ 5021.620109] =====>rtl8192_set_chan()====ch:11
[ 5021.630167] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5021.630176] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 5051.853925] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5140.007676] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5140.060133] =====>rtl8192_set_chan()====ch:1
[ 5140.180109] =====>rtl8192_set_chan()====ch:2
[ 5140.300104] =====>rtl8192_set_chan()====ch:3
[ 5140.420102] =====>rtl8192_set_chan()====ch:4
[ 5140.540102] =====>rtl8192_set_chan()====ch:5
[ 5140.660103] =====>rtl8192_set_chan()====ch:6
[ 5140.780112] =====>rtl8192_set_chan()====ch:7
[ 5140.900104] =====>rtl8192_set_chan()====ch:8
[ 5141.020114] =====>rtl8192_set_chan()====ch:9
[ 5141.140112] =====>rtl8192_set_chan()====ch:10
[ 5141.260105] =====>rtl8192_set_chan()====ch:11
[ 5141.380078] =====>rtl8192_set_chan()====ch:12
[ 5141.500102] =====>rtl8192_set_chan()====ch:13
[ 5141.620104] =====>rtl8192_set_chan()====ch:11
[ 5141.630163] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5141.630172] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 5178.215498] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5187.226826] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5260.007671] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5260.007760] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5260.060136] =====>rtl8192_set_chan()====ch:1
[ 5260.180105] =====>rtl8192_set_chan()====ch:2
[ 5260.300098] =====>rtl8192_set_chan()====ch:3
[ 5260.420107] =====>rtl8192_set_chan()====ch:4
[ 5260.530104] =====>rtl8192_set_chan()====ch:5
[ 5260.650097] =====>rtl8192_set_chan()====ch:6
[ 5260.770098] =====>rtl8192_set_chan()====ch:7
[ 5260.890073] =====>rtl8192_set_chan()====ch:8
[ 5261.010104] =====>rtl8192_set_chan()====ch:9
[ 5261.130108] =====>rtl8192_set_chan()====ch:10
[ 5261.250096] =====>rtl8192_set_chan()====ch:11
[ 5261.370097] =====>rtl8192_set_chan()====ch:12
[ 5261.490096] =====>rtl8192_set_chan()====ch:13
[ 5261.610108] =====>rtl8192_set_chan()====ch:11
[ 5261.620167] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5261.620176] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
[ 5273.451129] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5297.617745] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5380.007798] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 5380.007887] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5380.060134] =====>rtl8192_set_chan()====ch:1
[ 5380.180104] =====>rtl8192_set_chan()====ch:2
[ 5380.300100] =====>rtl8192_set_chan()====ch:3
[ 5380.420097] =====>rtl8192_set_chan()====ch:4
[ 5380.540097] =====>rtl8192_set_chan()====ch:5
[ 5380.660068] =====>rtl8192_set_chan()====ch:6
[ 5380.780083] =====>rtl8192_set_chan()====ch:7
[ 5380.900098] =====>rtl8192_set_chan()====ch:8
[ 5381.020105] =====>rtl8192_set_chan()====ch:9
[ 5381.140076] =====>rtl8192_set_chan()====ch:10
[ 5381.260103] =====>rtl8192_set_chan()====ch:11
[ 5381.380115] =====>rtl8192_set_chan()====ch:12
[ 5381.500102] =====>rtl8192_set_chan()====ch:13
[ 5381.620105] =====>rtl8192_set_chan()====ch:11
[ 5381.630165] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5381.630174] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
ubuntu@ubuntu:~$ 
```

---

### Post by sunshinelock on 2011-04-30
Okay, if this isn't going to work, is there a way to get back to 10.10 safely from the point I'm at right now without any data loss?

---

### Post by sunshinelock on 2011-05-01
A little more info if it's needed:

Hard drive array 1 (I'm not sure what the computer names it officially, but I'll call it array 1) is sda and sdb.  This is my Windows7 system partitioned into the operating system on sda1/sdb1 and the general storage on sda2/sdb2.

Hard drive array 2 (which is the array that Grub2 isn't picking up or whatever it's doing) is sdc and sdd.  This is my Ubuntu system and it should be partitioned with swap at sdc1/sdd1, Ubuntu root at sdc2/sdd2, and I think I had /home at sdc3/sdd3.

I'm in Windows7 right now and can see in:

Control Panel -> System and Security -> Administrative Tools -> Computer Management -> Storage -> Disk Management

That the Disk 0 is still Windows 7 (C:) and Double Backed Up (G:)

Disk 1 is partitioned 17.09 GB, 9.28 GB, and 904.95 GB.  There aren't label (D:, E:, or F:) attached, neither are there names on them.

I was running 10.10 on this very well until Friday afternoon when I decided I was going to upgrade to 11.04.

I'm fairly certain Grub was on Disk 1 somewhere (the linux combo).

My Raid is controlled by my motherboard.  It's not a software-driven system.

From problems I've read on this forum, a lot of focus is on software-driven raid issues and I cannot see anything yet similar to the problem I have.

I want to be able to just reconfigure whatever it is that's not syncing instead of re-installing the OS.  I have so much info stored in the sdc3/sdd3 that I don't want to risk (and maybe even some info in sdc2/sdd2).

---

### Post by sunshinelock on 2011-05-01
Well, according to this thread, post 1:

[http://ubuntuforums.org/showthread.php?t=1285650](http://ubuntuforums.org/showthread.php?t=1285650)

It suggests using testdisk.

I found it here:

[http://packages.ubuntu.com/natty/testdisk](http://packages.ubuntu.com/natty/testdisk)

Is this a good next step?  I really don't want to do anything that I cannot recover from.

---

### Post by sunshinelock on 2011-05-01
Spent the last several hours with testdisk and still having the same problems.  I changed the boot in GRUB2 to /dev/sda2 and still got the same errors.

Still stuck with a broken Ubuntu and I've put at least 24 hours of solid work into this over the last 2+ days.

---

### Post by tnine on 2011-05-01
I had this same problem.  I was on Ubuntu 10.10 server 64bit using 4 disks in a raid 5, with 1 windows disk.  Here are the steps I followed to get the system up and running again after the broken upgrade.

1. Download the desktop 64 bit live iso and boot to it.  Obviously if you're on 32 bit, get the 32 bit version
2. Open up the package manager and install "mdadm" and "lvm2"
3. Open a terminal and enter the following command

```

sudo mdadm --assemble --scan

```This should create a /dev/mdX ( in my case /dev/md0) device for your raid array.  I use LVM over my raid, so when assembled the raid, the LVM was auto detected.  

4. Open up the disk utility and verify the raid array was assembled correctly and mount the disks.
5. At this point you should back up ALL your data from the mounted disks.  It's probably your last chance to recover it.
6. Run the installer from the desktop icon.  When prompted unmount the raid drives.
7. Select "Upgrade"

For me the installer was smart enough to resolve the installation issues and after I rebooted it "just worked".  I hope this helps you!

Todd

---

### Post by sunshinelock on 2011-05-02
I have a question about that:

I have my RAID running directly through my motherboard for both the Ubuntu and Windows7 systems.

This mdadm is software-based RAID, isn't it?  Would this conflict with the montherboard RAID settings?

If no, then fine,

But if it means I have to change BIOS settings then that would end up killing my Windows7 system since I don't have a software system on that setup.

---

### Post by sunshinelock on 2011-05-02
That wasn't much help.

I installed mdadm and lvm2 from the Ubuntu Software Center.  I typed in you code and got this:

```

ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file or automatically
ubuntu@ubuntu:~$ 

```

So, still without my Ubuntu, just a stupid LiveCD and Windows7.

---

### Post by sunshinelock on 2011-05-02
So, here is the latest info from my RESULTS.txt, since I realize I may have altered a few things over the last few days:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/mapper/pdc_cdajibgfhj

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

pdc_cdajibgfhj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

pdc_cdajibgfhj2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   987,545,599   987,543,552   7 HPFS/NTFS
/dev/sda2         987,545,600 1,953,120,255   965,574,656   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32    15,625,215    15,625,184   b W95 FAT32


Drive: pdc_cdajibgfhj ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cdajibgfhj: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cdajibgfhj1   *          2,048   987,545,599   987,543,552   7 HPFS/NTFS
/dev/mapper/pdc_cdajibgfhj2        987,545,600 1,953,120,255   965,574,656   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cdajibgfhj1 5A99662B8FE00B1F                       ntfs       Windows 7                     
/dev/mapper/pdc_cdajibgfhj2 CE22E72322E70EF1                       ntfs       Double Backed Up              
/dev/mapper/pdc_cdajibgfhj: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc                                                promise_fasttrack_raid_member                               
/dev/sdd                                                promise_fasttrack_raid_member                               
/dev/sde1        604F-4A66                              vfat       PENDRIVE                      
/dev/sde: PTTYPE="dos" 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_cdajibgfhj
pdc_cdajibgfhj1
pdc_cdajibgfhj2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde1/boot/grub/grub.cfg: ===========================


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

=================== sde1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sde1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 6b ee 00 7e 3b 00 00  00 00 00 00 02 00 00 00  |.k..~;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 66 4a 4f 60 4e  4f 20 4e 41 4d 45 20 20  |..)fJO`NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 20  77 98 00 66 ba 00 00 00  |..E}.f. w..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_cdajibgfhj" [1/2] on /dev/sda
  No volume groups found
mdadm: No arrays found in config file or automatically

```

---

### Post by devguy on 2011-05-02
Welcome to the [club]("http://ubuntuforums.org/showthread.php?t=1742308") buddy.  No word whatsoever what's up.  I'm gonna try installing using the Alternate CD and see if that works (in the past, the alternate CD had better RAID support).

---

### Post by Fittersman on 2011-05-10
> **tnine said:**
> I had this same problem.  I was on Ubuntu 10.10 server 64bit using 4 disks in a raid 5, with 1 windows disk.  Here are the steps I followed to get the system up and running again after the broken upgrade.

1. Download the desktop 64 bit live iso and boot to it.  Obviously if you're on 32 bit, get the 32 bit version
2. Open up the package manager and install "mdadm" and "lvm2"
3. Open a terminal and enter the following command

```

sudo mdadm --assemble --scan

```This should create a /dev/mdX ( in my case /dev/md0) device for your raid array.  I use LVM over my raid, so when assembled the raid, the LVM was auto detected.  

4. Open up the disk utility and verify the raid array was assembled correctly and mount the disks.
5. At this point you should back up ALL your data from the mounted disks.  It's probably your last chance to recover it.
6. Run the installer from the desktop icon.  When prompted unmount the raid drives.
7. Select "Upgrade"

For me the installer was smart enough to resolve the installation issues and after I rebooted it "just worked".  I hope this helps you!

Todd

Thanks for these instructions. They worked for me on my ASUS P5Q Pro motherboard. I am using two 500GB harddrives in motherboard raid 1 (fakeraid). I was originally having issues mounting /home and /windows at bootup, but after running your instructions everything worked ok.

---

### Post by nutznboltz on 2011-05-28
What you want:

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/770600](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/770600)

---

