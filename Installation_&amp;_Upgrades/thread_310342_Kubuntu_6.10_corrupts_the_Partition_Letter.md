---
title: "Kubuntu 6.10 corrupts the Partition Letter"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by true_friend on 2006-12-01
Hi folks
i am trying second time kubuntu 6.10 Edgy Eft. First i had installed it but after a few boots i could not boot my system from it. When i tried to erase that linux partition by partition magic (which i use always to do this for previous version also and worked perfectly) i could not erase the partition the error was partition letter is not correct. now today i installed it second time on same logical drive D: and same problem is occurring. i had to erase my full hard disk last time to correct this problem and i am thinking this time it would be the same.
i am sick of this situation.](*,) ](*,) ](*,)  i like kubuntu most but this problem..........
what i do??
have any other buddy faced this problem??
 or only i am. and i take it as my HardDisk's (maxtor 40 GB) problem???
Regards
True_Friend

---

### Post by true_friend on 2006-12-01
This is the error log i got from partition magic.
.......................................................
PowerQuest PartitionInfo 8.0 -- Windows NT/2000 Version
Date Generated:  12/01/06  13:10:22
Copyright (c)1994-2002, PowerQuest Corporation
Permission is granted for this utility to be freely copied so long
as it is not modified in any way.  All other rights are reserved.

PowerQuest, makers of PartitionMagic(r), Drive Image(tm), and DriveCopy(tm), can be reached at:
    Voice:  801-437-8900
    Fax:  801-226-8941
    Web site:  [http://www.powerquest.com/support/](http://www.powerquest.com/support/)
    E-mail:  [email]magic@powerquest.com[/email]

General System Information:
    Total Physical Memory (bytes):  267,894,784
    Used Physical Memory: (bytes):  121,028,608
    Maximum Page File Size: (bytes):  648,675,328
    Current Page File Size: (bytes):  84,766,720



===========================================================================================================
Disk Geometry Information for Disk 1:    5310 Cylinders,  240 Heads,  63 Sectors/Track
System              PartSect  # Boot BCyl Head Sect  FS    ECyl Head Sect    StartSect     NumSects
===========================================================================================================
                           0  0  80     0    1    1  07    1023  239   63           63   20,487,537
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  0  80      0    1    1  07   1354  239   63        63  20487537
                           0  1  00  1023  179   63  0F    1023  239   63   20,498,939   59,773,141
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  1  00   1355  179   63  0F   5308  239   63  20498939  59773141
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 179.
Info: Partition didn't begin on head boundary.
  ucBeginSector expected to be 1, not 63.
NO NAME           20,498,939  0  00  1023  180    1  0B    1023  239   63   20,498,940    6,339,060
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 20498939  0  00   1355  180    1  0B   1774  239   63  20498940   6339060
Error #105: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 180.
                  20,498,939  1  00  1023   90    1  05    1023  254   63   40,965,750   20,481,930
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 20498939  1  00   2709   90    1  05   4063  239   63  40965750  20481930
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 90.
NO NAME           40,965,750  0  00  1023    1    1  0B    1023  239   63   40,975,263   20,472,417
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 40965750  0  00   2710    1    1  0B   4063  239   63  40975263  20472417
                  40,965,750  1  00  1023    0    1  05    1023  254   63   61,447,680   18,824,400
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 40965750  1  00   4064    0    1  05   5308  239   63  61447680  18824400
NO NAME           61,447,680  0  00  1023    1    1  0B    1023  239   63   61,447,743   18,824,337
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 61447680  0  00   4064    1    1  0B   5308  239   63  61447743  18824337
                  61,447,680  1  00  1023   90    1  05    1023  194   63   26,828,550   13,478,535
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 61447680  1  00   1774   90    1  05   2665  194   63  26828550  13478535
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 90.
Info: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 194.
Error #120: Logical Drive chain extends toward start of drive.
                  26,828,550  0  80  1023  254   63  83    1023  254   63   26,828,613   13,478,472
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 26828550  0  80   1774   91    1  83   2665  194   63  26828613  13478472
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 91.
Info: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 194.
                  26,828,550  1  00  1023  195    1  05    1023  254   63   40,307,085      658,665
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 26828550  1  00   2665  195    1  05   2709   89   63  40307085    658665
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 195.
Info: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 89.
SWAPSPACE2        40,307,085  0  00  1023  254   63  82    1023  254   63   40,307,148      658,602
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
 40307085  0  00   2665  196    1  82   2709   89   63  40307148    658602
Info: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 196.
Info: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 239, not 89.



===========================================================================================================
Partition Information for Disk 1:    39,202.7 Megabytes
Volume         PartType    Status    Size MB    PartSect  #   StartSect  TotalSects
===========================================================================================================
C:             NTFS        Pri,Boot 10,003.7           0  0          63  20,487,537
               ExtendedX   Pri      29,186.1           0  1  20,498,939  59,773,141
               EPBR        Log       3,095.2        None --  20,498,939   6,339,061
D:NO NAME      FAT32       Log       3,095.2  20,498,939  0  20,498,940   6,339,060
Error #114: Logical starting at 20498940 is not one head away from EPBR.
               EPBR        Log       6,581.3  61,447,680  1  26,828,550  13,478,535
Warning #113: EPBR partition starting at 26828550 overlaps previous EPBR partition.
               Linux Ext3  Log,Boot  6,581.3  26,828,550  0  26,828,613  13,478,472
               EPBR        Log         321.6  26,828,550  1  40,307,085     658,665
*:SWAPSPACE2   Linux Swap  Log         321.6  40,307,085  0  40,307,148     658,602
               EPBR        Log      10,000.9  20,498,939  1  40,965,750  20,481,930
E:NO NAME      FAT32       Log       9,996.3  40,965,750  0  40,975,263  20,472,417
Error #114: Logical starting at 40975263 is not one head away from EPBR.
               EPBR        Log       9,191.6  40,965,750  1  61,447,680  18,824,400
F:NO NAME      FAT32       Log       9,191.6  61,447,680  0  61,447,743  18,824,337
               Unallocated Pri           7.4        None --  80,272,080      15,120


===========================================================================================================
Boot Record for drive C:   (Drive: 1, Starting sector: 63, Type: NTFS)
===========================================================================================================
 1. Jump:                   EB 52 90
 2. OEM Name:               NTFS    
 3. Bytes per Sector:       512
 4. Sectors per Cluster:    8
 5. Reserved Sectors:       0
 6. Number of FATs:         0
 7. Root Dir Entries:       0
 8. Total Sectors:          0
 9. Media Descriptor:       0xF8
10. Sectors per FAT:        0
11. Sectors per Track:      63  (0x3F)
12. Number of Heads:        240  (0xF0)
13. Hidden Sectors:         63  (0x3F)
14. Total Sectors (>32MB):  0  (0x0)
15. Unused:                 0x80008000
16. Total NTFS Sectors:     20487536
17. MFT Start Cluster:      786432
18. MFT Mirror Start Clust: 1280471
19. Clusters per FRS:       246
20. Clusters per Index Blk: 1
21. Serial Number:          0x7C883CDB883C961C
22. Checksum:               0  (0x0)
23. Boot Signature:         0xAA55

===========================================================================================================
Boot Record for drive D:   (Drive: 1, Starting sector: 20,498,940, Type: FAT32)
===========================================================================================================
 1. Jump:                   EB 58 90
 2. OEM Name:               MSWIN4.1
 3. Bytes per Sector:       512
 4. Sectors per Cluster:    16
 5. Reserved Sectors:       39
 6. Number of FAT's:        2
 7. Reserved:               0x0000
 8. Reserved:               0x0000
 9. Media Descriptor:       0xF8
10. Sectors per FAT:        0
11. Sectors per Track:      63  (0x3F)
12. Number of Heads:        240  (0xF0)
13. Hidden Sectors:         20498940  (0x138C9FC)
14. Big Total Sectors:      6329610  (0x60950A)
15. Big Sectors per FAT:    3090
16. Extended Flags:         0x0000
17. FS Version:             0
18. First Cluster of Root:  2  (0x2)
19. FS Info Sector:         1
20. Backup Boot Sector:     6
21. Reserved:               000000000000000000000000 
22. Drive ID:               0x80
23. Reserved for NT:        0x00
24. Extended Boot Sig:      0x29
25. Serial Number:          0xE06D8C6F
26. Volume Name:            NO NAME    
27. File System Type:       FAT32   
28. Boot Signature:         0xAA55

===========================================================================================================
Boot Record for drive *:   (Drive: 1, Starting sector: 26,828,613, Type: Ext3)
===========================================================================================================
Ext3 file system super block:
 1. Inodes count:           843648
 2. Blocks count:           1684809
 3. Reserved blocks count:  84240
 4. Free blocks count:      1199780
 5. First data block:       0
 6. Logical block size:     2
 7. Logical fragment size:  2
 8. Blocks/group:           32768
 9. Fragments/group:        32768
10. Inodes/group:           16224
11. Mount time:             0x457020A2
12. Last write time:        0x457024FF
13. Mount count:            1
14. Max. mount count:       30
15. Magic number:           EF53
16. State:                  0x0001
17. Error behavior:         0x0001
18. Minor revision level:   0
19. Last check time:        0x00000000
20. Max. time bet. checks:  0
21. Creator oper. system:   0
22. Major revision level:   1
23. Reserved block def. UID:0x0000
24. Reserved block def. GID:0x0000

===========================================================================================================
Boot Record for drive E:   (Drive: 1, Starting sector: 40,975,263, Type: FAT32)
===========================================================================================================
 1. Jump:                   EB 58 90
 2. OEM Name:               MSDOS5.0
 3. Bytes per Sector:       512
 4. Sectors per Cluster:    16
 5. Reserved Sectors:       34
 6. Number of FAT's:        2
 7. Reserved:               0x0000
 8. Reserved:               0x0000
 9. Media Descriptor:       0xF8
10. Sectors per FAT:        0
11. Sectors per Track:      63  (0x3F)
12. Number of Heads:        240  (0xF0)
13. Hidden Sectors:         63  (0x3F)
14. Big Total Sectors:      20472417  (0x1386261)
15. Big Sectors per FAT:    9987
16. Extended Flags:         0x0000
17. FS Version:             0
18. First Cluster of Root:  2  (0x2)
19. FS Info Sector:         1
20. Backup Boot Sector:     6
21. Reserved:               000000000000000000000000 
22. Drive ID:               0x80
23. Reserved for NT:        0x00
24. Extended Boot Sig:      0x29
25. Serial Number:          0x18581276
26. Volume Name:            NO NAME    
27. File System Type:       FAT32   
28. Boot Signature:         0xAA55

===========================================================================================================
Boot Record for drive F:   (Drive: 1, Starting sector: 61,447,743, Type: FAT32)
===========================================================================================================
 1. Jump:                   EB 58 90
 2. OEM Name:               MSDOS5.0
 3. Bytes per Sector:       512
 4. Sectors per Cluster:    16
 5. Reserved Sectors:       34
 6. Number of FAT's:        2
 7. Reserved:               0x0000
 8. Reserved:               0x0000
 9. Media Descriptor:       0xF8
10. Sectors per FAT:        0
11. Sectors per Track:      63  (0x3F)
12. Number of Heads:        240  (0xF0)
13. Hidden Sectors:         63  (0x3F)
14. Big Total Sectors:      18824337  (0x11F3C91)
15. Big Sectors per FAT:    9183
16. Extended Flags:         0x0000
17. FS Version:             0
18. First Cluster of Root:  2  (0x2)
19. FS Info Sector:         1
20. Backup Boot Sector:     6
21. Reserved:               000000000000000000000000 
22. Drive ID:               0x80
23. Reserved for NT:        0x00
24. Extended Boot Sig:      0x29
25. Serial Number:          0x246341E5
26. Volume Name:            NO NAME    
27. File System Type:       FAT32   
28. Boot Signature:         0xAA55
....................................................

---

### Post by true_friend on 2006-12-01
Currently at kubuntu. tried to mount divhda1 the drive C: by windwos and got and error. by applyling follwoing command got this out put.
..................................
ss@ss-desktop:~$ dmesg | tail
[   49.433721] Bluetooth: RFCOMM socket layer initialized
[   49.433745] Bluetooth: RFCOMM TTY layer initialized
[   49.433749] Bluetooth: RFCOMM ver 1.7
[  164.237503] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  670.845189] ISO 9660 Extensions: Microsoft Joliet Level 3
[  671.588825] ISOFS: changing to secondary root
[ 1169.416552] FAT: bogus number of reserved sectors
[ 1169.416564] VFS: Can't find a valid FAT filesystem on dev hda1.
[ 1439.165260] FAT: bogus number of reserved sectors
[ 1439.165269] VFS: Can't find a valid FAT filesystem on dev hda1.
................................
any suggesstions?
other three partitions were successfully mounted. now going to restart and i am 100% sure it could not be able to boot linux system again as my last expereience was same.

---

### Post by Sef on 2006-12-18
> PowerQuest, makers of PartitionMagic

PM and LInux don't always get along.   Download [GParted]("http://gparted.sourceforge.net/livecd.php") and use that instead.

---

