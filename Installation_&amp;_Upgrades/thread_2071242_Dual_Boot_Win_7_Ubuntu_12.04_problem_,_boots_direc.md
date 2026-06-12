---
title: "Dual Boot Win 7 /Ubuntu 12.04 problem , boots directly into windows"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by PowerArjun on 2012-10-14
Hey guys,

I installed ubuntu 12.04 on my ultrabook today but after restart, it boots directly into windows, my ultrabook has a 32gb ssd also, but i am not sure if that is the cause of all these problems.

After a few searches and running the command fdisk i got this :
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x14750923

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    29044735    14481408    7  HPFS/NTFS/exFAT
/dev/sda3        29044736   976764927   473860096    7  HPFS/NTFS/exFAT
omitting empty partition (6)

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14750908

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    16775167     8386560   84  OS/2 hidden C: drive
/dev/sdb2        16777214    62531583    22877185    5  Extended
/dev/sdb5        16777216    46008319    14615552   83  Linux


```Seems like ubuntu is on /dev/sdb5 ??

I also ran the boot info scrIpt ad here it is 

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No known boot loader is installed in the MBR of 
    /dev/mapper/isw_ccebggbeed_Dev_Cache.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb5 already mounted or sdb5 busy

isw_ccebggbeed_Dev_Cache1: _____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb5 already mounted or sdb5 busy
mount: unknown filesystem type ''

isw_ccebggbeed_Dev_Cache2: _____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sdb5 already mounted or sdb5 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    29,044,735    28,962,816   7 NTFS / exFAT / HPFS
/dev/sda3          29,044,736   976,764,927   947,720,192   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    16,775,167    16,773,120  84 OS/2 hidden C: drive
/dev/sdb2          16,777,214    62,531,583    45,754,370   5 Extended
/dev/sdb5          16,777,216    46,008,319    29,231,104  83 Linux
Invalid MBR Signature found.
Empty Partition.


Drive: isw_ccebggbeed_Dev_Cache _____________________________________________________________________

Disk /dev/mapper/isw_ccebggbeed_Dev_Cache: 23.4 GB, 23422173184 bytes
255 heads, 63 sectors/track, 2847 cylinders, total 45746432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/mapper/isw_ccebggbeed_Dev_Cache1    ?           224    14,483,679    14,483,456  40 Venix 80286
/dev/mapper/isw_ccebggbeed_Dev_Cache2            327,680    20,250,623    19,922,944   0 Empty

/dev/mapper/isw_ccebggbeed_Dev_Cache1 overlaps with /dev/mapper/isw_ccebggbeed_Dev_Cache2

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        C6765A7B765A6C65                       ntfs       RECOVERY
/dev/sda3        909C5E5B9C5E3C42                       ntfs       OS
/dev/sdb5        9731d688-1c93-43f9-9a12-ebe082baeb30   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/mapper/isw_ccebggbeed_Dev_Cache

00000000  49 6e 74 65 6c 20 49 4d  53 4d 20 4e 56 20 43 61  |Intel IMSM NV Ca|
00000010  63 68 65 20 43 66 67 2e  20 53 69 67 2e 20 20 20  |che Cfg. Sig.   |
00000020  06 00 aa 00 4a 01 00 00  01 00 00 00 00 00 00 00  |....J...........|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 ff 2b 32 01 00  |............+2..|
000000b0  03 00 41 54 35 39 31 31  56 33 56 47 41 32 50 41  |..AT5911V3VGA2PA|
000000c0  00 00 00 00 00 00 53 00  00 00 00 00 00 00 00 00  |......S.........|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 c2 00 00 00 4b  |...............K|
00000150  01 00 01 00 00 00 00 00  12 01 00 d4 01 00 00 00  |................|
00000160  26 02 00 e7 02 00 00 e7  26 02 20 00 00 00 00 00  |&.......&. .....|
00000170  01 00 00 00 00 00 c0 db  fb ff 9c b1 ff ff ff ff  |................|
00000180  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000190  ff ff ff ff ff ff 30 01  00 00 00 00 80 01 20 01  |......0....... .|
000001a0  00 00 00 40 22 00 00 20  00 00 00 00 00 00 87 cd  |...@".. ........|
000001b0  ac 3d 87 cd ac 3d 00 00  00 00 00 70 27 02 a0 00  |.=...=.....p'...|
000001c0  00 00 40 00 00 00 e0 00  00 00 00 00 dd 00 00 00  |..@.............|
000001d0  00 00 00 00 00 00 00 00  05 00 00 00 30 01 00 00  |............0...|
000001e0  10 37 00 00 00 00 00 00  00 00 00 00 00 00 84 ff  |.7..............|
000001f0  12 19 06 00 00 00 84 ff  f5 69 00 00 00 00 84 ff  |.........i......|
00000200

Unknown BootLoader on isw_ccebggbeed_Dev_Cache1


Unknown BootLoader on isw_ccebggbeed_Dev_Cache2



=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
hexdump: sda1/??@\E1?.\C7: Input/output error
hexdump: sda1/??@\E1?.\C7: Input/output error
hexdump: sda1/??@\E1?.\C7: Input/output error
hexdump: sda1/\EE?.?: Input/output error
hexdump: sda1/\EE?.?: Input/output error
hexdump: sda1/\EE?.?: Input/output error
hexdump: sda1/0000.1s: Input/output error
hexdump: sda1/0000.1s: Input/output error
hexdump: sda1/0000.1s: Input/output error
hexdump: sda1/16s.s: Input/output error
hexdump: sda1/16s.s: Input/output error
hexdump: sda1/16s.s: Input/output error
hexdump: sda1/?3\A03\F76\E4.\F7: Input/output error
hexdump: sda1/?3\A03\F76\E4.\F7: Input/output error
hexdump: sda1/?3\A03\F76\E4.\F7: Input/output error
hexdump: sda1/456789ab.cde: Input/output error
hexdump: sda1/456789ab.cde: Input/output error
hexdump: sda1/456789ab.cde: Input/output error
hexdump: sda1/c%02d%c.%2d: Input/output error
hexdump: sda1/c%02d%c.%2d: Input/output error
hexdump: sda1/c%02d%c.%2d: Input/output error
hexdump: sda1/COND.pm: Input/output error
hexdump: sda1/COND.pm: Input/output error
hexdump: sda1/COND.pm: Input/output error
hexdump: sda1/d%c%02d.%02: Input/output error
hexdump: sda1/d%c%02d.%02: Input/output error
hexdump: sda1/d%c%02d.%02: Input/output error
hexdump: sda1/?F?6\FA`.6\EE: Input/output error
hexdump: sda1/?F?6\FA`.6\EE: Input/output error
hexdump: sda1/?F?6\FA`.6\EE: Input/output error
hexdump: sda1/ict$prin.ter: Input/output error
hexdump: sda1/ict$prin.ter: Input/output error
hexdump: sda1/ict$prin.ter: Input/output error
hexdump: sda1/n=: Input/output error
hexdump: sda1/n=: Input/output error
hexdump: sda1/n=: Input/output error
hexdump: sda1/p\E2\A0.?f: Input/output error
hexdump: sda1/p\E2\A0.?f: Input/output error
hexdump: sda1/p\E2\A0.?f: Input/output error
hexdump: sda1/r-h-s-a-: Input/output error
hexdump: sda1/r-h-s-a-: Input/output error
hexdump: sda1/r-h-s-a-: Input/output error
hexdump: sda1/s..%s: Input/output error
hexdump: sda1/s..%s: Input/output error
hexdump: sda1/s..%s: Input/output error
hexdump: sda1/s.%s%: Input/output error
hexdump: sda1/s.%s%: Input/output error
hexdump: sda1/s.%s%: Input/output error
hexdump: sda1/st.lev: Input/output error
hexdump: sda1/st.lev: Input/output error
hexdump: sda1/st.lev: Input/output error
hexdump: sda1/ty.del: Input/output error
hexdump: sda1/ty.del: Input/output error
hexdump: sda1/ty.del: Input/output error
hexdump: sda1/untry.WS: Input/output error
hexdump: sda1/untry.WS: Input/output error
hexdump: sda1/untry.WS: Input/output error
hexdump: sda1/y.y_o: Input/output error
hexdump: sda1/y.y_o: Input/output error
hexdump: sda1/y.y_o: Input/output error
hexdump: /dev/mapper/isw_ccebggbeed_Dev_Cache1: No such file or directory
hexdump: /dev/mapper/isw_ccebggbeed_Dev_Cache1: No such file or directory
hexdump: /dev/mapper/isw_ccebggbeed_Dev_Cache2: No such file or directory
hexdump: /dev/mapper/isw_ccebggbeed_Dev_Cache2: No such file or directory


```Is there any way to reinstall Grub onto the correct location?

Thanx,
Arjun

---

### Post by oldfred on 2012-10-14
I am seeing a lot of these Intel Smart Response systems. They somehow use RAID and the Desktop installer does not include the RAID drivers. Most that have made it work disable the RAID. Some re-enable after Ubuntu, some install Ubuntu to SSD.

I do not have Intel SRT but saved these links:
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

---

### Post by jerry-va on 2012-12-10
[SIZE=3]INTEL SMART RESPONSE & RAPID START TECHNOLOGIES[/SIZE]

Hi, All,
Got a new mbd (Asus Z77), did research, here's some info on SSD caching and SRT, Intel's Smart Response Technology.

There are three "smart technologies" in Intel's 2012 Desktop Responsiveness Technology collection:


[LIST]
[*] Smart Response Technology (SRT) - caches frequently used sectors of an HDD into a Solid State Drive (SSD).
[/LIST]

[LIST]
[*] Rapid [re-]Start Technology - caches DRAM in a Solid State Drive
[/LIST]

[LIST]
[*] Smart Connect Technology - keeps your Twitter, Facebook and email accounts up to date even if you let your PC go to sleep.  Presumably the PC is constantly waking up to do this.
[/LIST]
     I won't discuss Smart Connect further, maybe you know more about it.

SRT technology achieves a logical drive which is like the physical  hybrid drives from Seagate (e.g., the Seagate Momentus XT series).   Rapid [re-]Start Technology enables you to turn on the SLEEP function in  BIOS, but save the DRAM to an SSD.  Wakeup is then nearly instant.   DRAM & SSD are both blocks of solid-state memory, but DRAM is  volatile so it's great to be able to cache it onto a solid-state drive.    Once you can have your computer back in an instant with the shopping  cart where you left it, we can let PCs shut down instead of making them  wait for us.  This saves power big-time. 

**CACHE FUNCTION**
The cache system copies hard-disk drive sectors to the  SSD cache drive,  monitoring disk traffic to see which sectors are requested most often.   In order to give the system Logical Block Address ("sector") access  (underneath opsys-dependent, file-system-level access), the two drives  have to be declared as a RAID array in the BIOS.  Firmware in the Intel  chipset (present since Sandy Bridge) must then be accessed to stipulate  that this is not really a RAID array afterall.  Rather, you have to  specify that one drive is the SSD Cache and some other drive (or drives)  are to be accelerated.  It appears that a motherboard  manufacturer-furnished DVD of drivers with an install wizard that runs  only under Windows :-(   has to be used to access the chipset firmware.   Presumably the drivers interface an NTFS-based file system ("Explorer")  and the drivers, not just the install wizard, run only under Windows.    Good screen shots [here]("http://ubuntuforums.org/showthread.php?t=2038121"):  [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)  <rant> At this point, all of Linux Land has been told, to put it  politely, to wait your turn for drivers (or,more bluntly, told to get  lost).   It is, in my humble and considered opinion, conspiratorial and  gratuitous for Big Corporation Intel to arrange with Big Corporation  Microsoft to place access to BIOS and chipset firmware in an operating  system.  This is a BIOS setup that belongs in the BIOS. </rant>

** CACHE SIZES, PARTITIONS**
The largest cache size (largest number of LBA blocks) that Intel's  2012-vintage SRT can keep track adds up to 64GB.  If you have 4 fully  populated DRAM slots x 8 GB, then Rapid [re-]Start needs an additional  32GB.  Thus, the SSD cache drive should be at least 96GB.  After  designating cache and acceleration-target drives, the cache drive has to  be partitioned with two separate partitions, one for SRT and another  for Rapid[re-]Start.  The only detailed instructions I've seen speak of  creating a 96GB SRT partition and then shrinking it to 64GB to create  the leftover 32GB space.  Don't know what's going on here.  We cannot  create SRT and Rapid [re-]Start partitions directly because they have to  be in the same volume or journal?

** ONLY INTEL DRIVES FOR DESKTOP RESPONSIVENESS TECH**
Since it is the chipset (Southbridge) firmware that creates the special  LBA-level, semi-RAID hybrid logical drive from two (or more) physical  ones, only SATA drives whose hard drive controller and RAID controller  reside in the chipset can be used for SRT and Rapid [re-]Start.  The  current A77 chipset offers only two SATA III 6Gb/s drives, so those are  your cache and accelerated [boot] drives.  The other 4 Intel drives in  this A77 chipset are only 3Gb/s, so there is no point in spreading the  small 64GB SRT cache to them.  In those 4 Intel chipset 3 Gb/s slots,  one could build a RAID array with Seagate Momentus drives (750 GB, 32MB  conventional buffer, 8GB SSD cache, notebook size).  After 2 + 4 SATAs,  it's all over for the A77 chipset and any more Intel Desktop  Responsiveness Technologies.  So you could look for a motherboard with  an additional non-Intel HDC controller chip providing SATA III 6Gb/s  sockets and run a fast 2-drive RAID 0 or 1 array there.

Conceptually, I like the idea of making the SSD a permanent part of the  computer case, while the boot drives come and go as sizes change and  (ugh) drives die.  The SSD could die too of course, but there's nothing  on it to save before you slip in the replacement -- it's just a cache.

**SSD CONCERNS**
SSDs are less robust than many assume.  Their memory depends on packets  of electrons that can ebb away, faster at higher temps.  A $700  enterprise SSD drive  guarantees 10 years; no one's talking about the  drives you and I typically use.  And ordinary HDDs?  Magnetic domains  written on the sea floor by the planet's magnetic field reversals  remained for 750 million years to track the oceans creation and  establish the reality of continental drift.    Meanwhile, Smart Response  Technology (SRT) has no TRIM commands; writing won't be optimal if you  have to erase first.  And does the Intel firmware have load leveling?  I  do not know, but cache usage is so intense, it probably does not  matter.  Intel says to buy SSDs put together with more robust SLC  (Single-Level Cell) chips, but Intel is the only supplier I've found so  far that's making SLCs.  I'll go with cheap MLCs & just replace the  drive if it goes.  It's only a cache.  

I still want both Smart Response and Rapid [re-]Start technology in  Ubuntu.  Where's the best forum for Ubuntu community and developers to  stay in touch?
Thanks everyone.  

I want Ubuntu to host all my virtual machines, and I don't think I'll switch to Win7 as the host system just to get SRT and Rapid [re-]Start.  
--jerry-va

---

