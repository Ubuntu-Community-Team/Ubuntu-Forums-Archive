---
title: "Installine Ubuntu for the first time will not GO"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by NoJock on 2006-02-21
Hi All:
Im new to linux but have installed dule boot with windows and mepis on my drive i would like to also install ubuntu as well but there seems to be a problem with the partitioning segment of the install.

here is my partition info

PowerQuest PartitionInfo 8.0 -- Windows NT/2000 Version
Date Generated:  02/21/06  11:43:52
Copyright (c)1994-2002, PowerQuest Corporation
Permission is granted for this utility to be freely copied so long
as it is not modified in any way.  All other rights are reserved.

PowerQuest, makers of PartitionMagic(r), Drive Image(tm), and DriveCopy(tm), can be reached at:
    Voice:  801-437-8900
    Fax:  801-226-8941
    Web site:  [http://www.powerquest.com/support/](http://www.powerquest.com/support/)
    E-mail:  [email]magic@powerquest.com[/email]

General System Information:
    Total Physical Memory (bytes):  670,613,504
    Used Physical Memory: (bytes):  235,147,264
    Maximum Page File Size: (bytes):  1,303,064,576
    Current Page File Size: (bytes):  220,270,592



===========================================================================================================
Disk Geometry Information for Disk 1:    25841 Cylinders,  240 Heads,  63 Sectors/Track
System              PartSect  # Boot BCyl Head Sect  FS    ECyl Head Sect    StartSect     NumSects
===========================================================================================================
DISK0_VOL1                 0  0  00     0    1    1  0C    1023  239   63           63   95,694,417
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  0  00      0    1    1  0C   6328  239   63        63  95694417
                           0  1  00  1023    0    1  0F    1023  239   63  117,210,240  273,505,680
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  1  00   7752    0    1  0F  25840  239   63 117210240 273505680
                           0  2  00  1023    0    1  83    1023  239   63   95,694,480   21,515,760
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
        0  2  00   6329    0    1  83   7751  239   63  95694480  21515760
                 117,210,240  0  00  1023    1    1  83    1023  239   63  117,210,303   30,617,937
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
117210240  0  00   7752    1    1  83   9776  239   63 117210303  30617937
                 117,210,240  1  00  1023    0    1  05    1023  239   63  147,918,960  242,796,960
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
117210240  1  00   9783    0    1  05  25840  239   63 147918960 242796960
                 147,918,960  0  00  1023    1    1  07    1023  239   63  147,919,023  242,796,897
Info: Begin C,H,S values were large drive placeholders.
Info: End C,H,S values were large drive placeholders.
  Actual values are:
147918960  0  00   9783    1    1  07  25840  239   63 147919023 242796897



===========================================================================================================
Partition Information for Disk 1:    190,779.3 Megabytes
Volume         PartType    Status    Size MB    PartSect  #   StartSect  TotalSects
===========================================================================================================
C:DISK0_VOL1   FAT32X      Pri      46,725.8           0  0          63  95,694,417
               Linux Ext2  Pri      10,505.7           0  2  95,694,480  21,515,760
               ExtendedX   Pri      133,547.7           0  1 117,210,240 273,505,680
Info: MBR Partition Table not in sequential order.
               EPBR        Log      14,950.2        None -- 117,210,240  30,618,000
               Linux Ext3  Log      14,950.2 117,210,240  0 117,210,303  30,617,937
               Unallocated Log          44.3        None -- 147,828,240      90,720
               EPBR        Log      118,553.2 117,210,240  1 147,918,960 242,796,960
D:             NTFS        Log      118,553.2 147,918,960  0 147,919,023 242,796,897


===========================================================================================================
Boot Record for drive C:   (Drive: 1, Starting sector: 63, Type: FAT32)
===========================================================================================================
 1. Jump:                   EB 58 90
 2. OEM Name:               MSWIN4.1
 3. Bytes per Sector:       512
 4. Sectors per Cluster:    64
 5. Reserved Sectors:       34
 6. Number of FAT's:        2
 7. Reserved:               0x0000
 8. Reserved:               0x0000
 9. Media Descriptor:       0xF8
10. Sectors per FAT:        0
11. Sectors per Track:      63  (0x3F)
12. Number of Heads:        240  (0xF0)
13. Hidden Sectors:         63  (0x3F)
14. Big Total Sectors:      95694368  (0x5B42E20)
15. Big Sectors per FAT:    11679
16. Extended Flags:         0x0000
17. FS Version:             0
18. First Cluster of Root:  2  (0x2)
19. FS Info Sector:         1
20. Backup Boot Sector:     6
21. Reserved:               000000000000000000000000 
22. Drive ID:               0x80
23. Reserved for NT:        0x00
24. Extended Boot Sig:      0x29
25. Serial Number:          0x38C425F8
26. Volume Name:            DISK0_VOL1
27. File System Type:       FAT32   
28. Boot Signature:         0xAA55

===========================================================================================================
Boot Record for drive *:   (Drive: 1, Starting sector: 95,694,480, Type: Ext2)
===========================================================================================================
Ext2 file system super block:
 1. Inodes count:           1346592
 2. Blocks count:           2689470
 3. Reserved blocks count:  134473
 4. Free blocks count:      2179344
 5. First data block:       0
 6. Logical block size:     2
 7. Logical fragment size:  2
 8. Blocks/group:           32768
 9. Fragments/group:        32768
10. Inodes/group:           16224
11. Mount time:             0x43FB4CA5
12. Last write time:        0x43FB4CA5
13. Mount count:            22
14. Max. mount count:       -1
15. Magic number:           EF53
16. State:                  0x0001
17. Error behavior:         0x0001
18. Minor revision level:   0
19. Last check time:        0x43F838C6
20. Max. time bet. checks:  2592000
21. Creator oper. system:   0
22. Major revision level:   1
23. Reserved block def. UID:0x0000
24. Reserved block def. GID:0x0000

===========================================================================================================
Boot Record for drive *:   (Drive: 1, Starting sector: 117,210,303, Type: Ext3)
===========================================================================================================
Ext3 file system super block:
 1. Inodes count:           1916928
 2. Blocks count:           3827242
 3. Reserved blocks count:  191362
 4. Free blocks count:      3734281
 5. First data block:       0
 6. Logical block size:     2
 7. Logical fragment size:  2
 8. Blocks/group:           32768
 9. Fragments/group:        32768
10. Inodes/group:           16384
11. Mount time:             0x43FB49F6
12. Last write time:        0x43FB4A2E
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
Boot Record for drive D:   (Drive: 1, Starting sector: 147,919,023, Type: NTFS)
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
16. Total NTFS Sectors:     242796896
17. MFT Start Cluster:      786432
18. MFT Mirror Start Clust: 16
19. Clusters per FRS:       246
20. Clusters per Index Blk: 1
21. Serial Number:          0xF610CAF110CAB83F
22. Checksum:               0  (0x0)
23. Boot Signature:         0xAA55

now im not sure why i cant install ubuntu on the hda5 partition but i have not for the life of be been able to do this.

Help please some one,, or am i looking to do something that just cant be done??

---

### Post by TrendyDark on 2006-02-21
Um. . .did you try to partitioning tool on the Ubuntu Install disk?

---

### Post by NoJock on 2006-02-21
[QUOTE=TrendyDark]Um. . .did you try to partitioning tool on the Ubuntu Install disk?[/QUOTE] 

Thanks for such a quick response!
Yes i did and it refuses to acceppt the partition and go forward.
the smilly facess are all there it sees the partition and just will not proceed.

---

### Post by eylisian on 2006-02-21
Did you highlight it and then go deeper? Like Format or Keep Existing Data? From when the partitioner starts can you detail the steps allowed until it fails?

---

### Post by NoJock on 2006-02-21
Thanks for your response.
Yes i selected the second line i think(dont remember) but it was the one to accept and go forward.
going forward when i get to the partitioning segment i do it manualy it takes me to the partition tabel  and i select the hda5 partition and go to the bottom and tell it to process and i will not go forward it just hangs nothing happens at all have done this several time. Could i install for mepis(linux) and go forward or what, im at a loss..

when i get to the partitioning  startes the parting
next i have
IDE1 master (hda) - 200.0 GB ST3200822A
#1 primary 49.0GB smily face fat32 /media/hda1
#3 primary 11.0GB smily face ext2 /media/hda3
#5 logical  15.7GB smily face ext3 /media/hda5
     logical   42.1MB    free space
#6 logical 124.3GB smily face ntsf /media/hda6 
I like what i see and highlite the finish partitioning and write changes to disk 
at this point it hangs and will not go forward.

---

### Post by NoJock on 2008-07-21
Fixed Thanks to all fixed. have moved to partition magic always works.

---

