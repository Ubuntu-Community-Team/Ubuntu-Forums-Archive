---
title: "this computer has no operaating systems on it"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by soumo on 2009-11-16
Hi all,

if anyone can provide some insight, I would appreciate it.  I have not found this problem elsewhere on the forums though some similar ones.

I have an ASUS EEE PC netbook, with functioning Win & XP OSes.  I tried installing karmic from a usb key, but at the step that asks where to install, I am left with only the entire disk as the option.  

If I try the advanced manual option, I am told that there is no operating system installed on this computer,and again only left with the option to do an install over the whole partition.

If I use the live USB or Windows partition, there are a number of partitions including an ext3 and linux swap!

Here is the setup (see picture):
XP        NTFS 
Win 7     NTFS
41.59GB   EXT3 (has previous jaunty on it)
Cyclone   NTFS storage partition
4GB linux swap
30MB EFI system partition (I believe ASUS Bios uses this to speed up the boot up by using it to store the previous boot info or something like that)

One potential solution I found, might be to use testdisk to delete the MFT table and redetect it, but I'm afraid to try it...

-Thanks in advance.

---

### Post by wilee-nilee on 2009-11-16
Is the W7 a upgrade and have you removed any partitions like a recovery.

---

### Post by soumo on 2009-11-16
Yes I did wipe out the recovery partition when I first got the system.  It came with XP which I kept, and I installed jaunty & then win 7 fresh (not as an upgrade) in their own partition.  I can't seem to access jaunty (I think it's the grub that got messed up after win 7) so I thought I'd install karmic over it to 'fix' it.  Otherwise I suppose I could get into jaunty and do an upgrade.

When I use the live karmic, fdisk -l gives me the proper partitions.

-Thanks for the speedy reply.

---

### Post by darkod on 2009-11-16
You have 4 primary partitions PLUS a logical one? How did that happen?

Isn't the maximum 3 primary + logical (extended) or 4 primary total?

PS. I stand corrected, you have a logical drive not partition.

The partitioning is little confusing but you should be able to install karmic on your previous / and use the same swap space. If you run karmic with Try ubuntu option and open Gparted, how does it show the partitions? Correctly? I would take a look how Gparted is "understanding" them, not just Win7.

---

### Post by wilee-nilee on 2009-11-16
I ran into a similar unallocated with the removal of a XP recovery after I install W7 in the partition after XP which had Karmic in the next. I just did a fresh custom install of W7 and sized the partition to half the HD then installed Karmic.

The XP partition apparently had the MBR in it, I removed it while trying to remove the XP as the W7 was a upgrade. the Upgrade key worked while XP was still on the HD W7 had been live installed from XP. So when I fresh installed the key wouldn't work so i called the W7 tech team and they cracked the key in.

I had actually cracked the W7 key but MS called this a non verified system over the phone so that is why I did a complete fresh install, and had them crack it.

---

### Post by louieb on 2009-11-16
> **soumo said:**
> ...When I use the live karmic, fdisk -l gives me the proper partitions...

Please post the **fdisk -l** output. Its easier to spot problems with the partition table. Want to look for a primary partition inside an extended partition. - its a common windows partitioner screw up.

---

### Post by soumo on 2009-11-16
Thanks for all the help folks! I think I'm beggining to understand a bit more.

sudo fdisk-l:
Note, sdb is the usb live karmic key...
 
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4c5ef4d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766        8414    61440592+   7  HPFS/NTFS
/dev/sda3            8415       19452    88662735    5  Extended
/dev/sda4           19453       19457       40162+  ef  EFI (FAT-12/16/32)
/dev/sda5           13844       18942    40957717+   7  HPFS/NTFS
/dev/sda6            8415       13843    43608379+  83  Linux
/dev/sda7           18943       19452     4096543+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2097 MB, 2097152000 bytes
255 heads, 63 sectors/track, 254 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00055603

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         255     2047968+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(253, 254, 63) logical=(254, 245, 55)


Testdisk Log:
> 

Fri Nov 13 21:19:31 2009
Command line: TestDisk

TestDisk 6.12-WIP, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009) i686
Compiler: GCC 4.4 - Oct 30 2009 00:02:37
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       312581808 sectors
/dev/sda: user_max   312581808 sectors
/dev/sda: native_max 312581808 sectors
/dev/sda: dco        312581808 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA ST9160310AS
Disk /dev/sdb - 2097 MB / 2000 MiB - CHS 1016 65 62, sector size=512 - CBM Flash Disk

Partition table type (auto): Intel
Disk /dev/sda - 160 GB / 149 GiB - ATA ST9160310AS
Partition table type: Intel

Analyse Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
NTFS at 765/0/1
Info: size boot_sector 122881177, partition 122881185
check_part_i386 4 type EF: no test
NTFS at 13843/0/1
get_geometry_from_list_part_aux head=255 nbr=14
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=14
Current partition structure:
 1 * HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
 2 P HPFS - NTFS            765   0  1  8413 254 63  122881185 [7]
 3 E extended              8414   0  1 19451 254 63  177325470
 4 P EFI (FAT-12/16/32)   19452   0  1 19456 254 63      80325
 5 L HPFS - NTFS          13843   0  1 18941 254 63   81915435 [Cyclone]
   X extended              8414   0  2 13842 254 63   87216884
 6 L Linux                 8414   2  1 13842 254 63   87216759
   X extended             18942   0  1 19451 254 63    8193150
 7 L Linux Swap           18942   1  1 19451 254 63    8193087
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
NTFS at 0/1/1
filesystem size           12289662
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
     NTFS, 6292 MB / 6000 MiB
NTFS at 765/0/1
filesystem size           122881177
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               8021455
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS            765   0  1  8413 254 55  122881177 [7]
     NTFS, 62 GB / 58 GiB

recover_EXT2: s_block_group_nr=0/676, s_mnt_count=0/21, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 22165683
recover_EXT2: part_size 177325464
     Linux                 8414   0  1 19451 254 57  177325464 [Ubu]
     EXT4 Large file Sparse superblock, 90 GB / 84 GiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   * HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
     NTFS, 6292 MB / 6000 MiB
   P HPFS - NTFS            765   0  1  8413 254 63  122881185 [7]
     NTFS, 62 GB / 58 GiB
   P Linux                 8414   0  1 19451 254 63  177325470 [Ubu]
     EXT4 Large file Sparse superblock, 90 GB / 84 GiB

interface_write()
 1 * HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
 2 P HPFS - NTFS            765   0  1  8413 254 63  122881185 [7]
 3 P Linux                 8414   0  1 19451 254 63  177325470 [Ubu]

search_part()
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
NTFS at 0/1/1
filesystem size           12289662
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
     NTFS, 6292 MB / 6000 MiB
NTFS at 764/254/63
filesystem size           12289662
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
     NTFS found using backup sector!, 6292 MB / 6000 MiB
NTFS at 765/0/1
filesystem size           122881177
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               8021455
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS            765   0  1  8413 254 55  122881177 [7]
     NTFS, 62 GB / 58 GiB
NTFS at 8413/254/63
filesystem size           122881177
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               8021455
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS            765   0  9  8413 254 63  122881177
     NTFS found using backup sector!, 62 GB / 58 GiB

recover_EXT2: s_block_group_nr=0/676, s_mnt_count=0/21, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 22165683
recover_EXT2: part_size 177325464
     Linux                 8414   0  1 19451 254 57  177325464 [Ubu]
     EXT4 Large file Sparse superblock, 90 GB / 84 GiB

recover_EXT2: s_block_group_nr=0/332, s_mnt_count=11/38, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 10902094
recover_EXT2: part_size 87216752
     Linux                 8414   2  1 13842 254 56   87216752
     EXT4 Large file Sparse superblock, 44 GB / 41 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/332, s_mnt_count=0/38, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 10902094
recover_EXT2: part_size 87216752
     Linux                 8414   2  1 13842 254 56   87216752
     EXT4 Large file Sparse superblock Backup superblock, 44 GB / 41 GiB
NTFS at 10441/254/63
filesystem size           167750667
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 10441 254 63  167750667 [XP]
     NTFS found using backup sector!, 85 GB / 79 GiB
NTFS at 10442/0/1
filesystem size           128343285
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          10442   0  1 18430 254 63  128343285
     NTFS, 65 GB / 61 GiB
NTFS at 13843/0/1
filesystem size           81915435
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               5119714
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          13843   0  1 18941 254 63   81915435 [Cyclone]
     NTFS, 41 GB / 39 GiB
NTFS at 18941/254/63
filesystem size           81915435
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               5119714
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          13843   0  1 18941 254 63   81915435 [Cyclone]
     NTFS found using backup sector!, 41 GB / 39 GiB
     Linux Swap           18942   1  1 19451 254 40    8193064
     SWAP2 version 1, 4194 MB / 4000 MiB
FAT32 at 19197/0/1
FAT1 : 40-4036
FAT2 : 4037-8033
start_rootdir : 3969794 root cluster : 495222
Data : 8034-4096569
sectors : 4096575
cluster_size : 8
no_of_cluster : 511067 (2 - 511068)
fat_length 3997 calculated 3993

FAT32 at 19197/0/1
     FAT32 LBA            19197   0  1 19451 254 63    4096575 [PE]
     FAT32, 2097 MB / 2000 MiB
FAT32 at 19197/0/7
FAT1 : 40-4036
FAT2 : 4037-8033
start_rootdir : 3969794 root cluster : 495222
Data : 8034-4096569
sectors : 4096575
cluster_size : 8
no_of_cluster : 511067 (2 - 511068)
fat_length 3997 calculated 3993
set_FAT_info: name from BS used

FAT32 at 19197/0/7
     FAT32 LBA            19197   0  1 19451 254 63    4096575 [NO NAME]
     FAT found using backup sector!, 2097 MB / 2000 MiB
NTFS at 764/254/50
filesystem size           12289649
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 764/254/63
filesystem size           12289662
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 765/0/1
filesystem size           122881177
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               8021455
clusters_per_mft_record   -10
clusters_per_index_record 1
get_geometry_from_list_part_aux head=255 nbr=16
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
get_geometry_from_list_part_aux head=240 nbr=2
get_geometry_from_list_part_aux head=255 nbr=16

Results
     HPFS - NTFS              0   1  1   764 254 63   12289662 [XP]
     NTFS, 6292 MB / 6000 MiB
     HPFS - NTFS              0   1  1 10441 254 63  167750667 [XP]
     NTFS found using backup sector!, 85 GB / 79 GiB
     HPFS - NTFS            764 254 50  1529 254 63   12289739
     NTFS, 6292 MB / 6000 MiB
     HPFS - NTFS            764 254 63  1529 254 63   12289726
     NTFS, 6292 MB / 6000 MiB
     HPFS - NTFS            765   0  1  8413 254 63  122881185 [7]
     NTFS, 62 GB / 58 GiB
     HPFS - NTFS            765   0  9  8413 254 63  122881177
     NTFS found using backup sector!, 62 GB / 58 GiB
     Linux                 8414   0  1 19451 254 63  177325470 [Ubu]
     EXT4 Large file Sparse superblock, 90 GB / 84 GiB
     Linux                 8414   2  1 13842 254 63   87216759
     EXT4 Large file Sparse superblock, 44 GB / 41 GiB
     HPFS - NTFS          10442   0  1 18430 254 63  128343285
     NTFS, 65 GB / 61 GiB
     HPFS - NTFS          13843   0  1 18941 254 63   81915435 [Cyclone]
     NTFS, 41 GB / 39 GiB
     Linux Swap           18942   1  1 19451 254 63    8193087
     SWAP2 version 1, 4194 MB / 4000 MiB
     FAT32 LBA            19197   0  1 19451 254 63    4096575 [PE]
     FAT32, 2097 MB / 2000 MiB

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.


---

### Post by louieb on 2009-11-16
Looked for a primary partition inside an extended partition. Everything looks good - no problem there.

Look a little odd - never have seen a ? in the boot flag column and have not seen the "doesn't look like a partition table" message before.

Don't see any reason for the installer having a problem. And no idea of what to look for next.  Out of ideas here.
 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4c5ef4d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766        8414    61440592+   7  HPFS/NTFS
/dev/sda3            8415       19452    88662735    5  Extended
/dev/sda4           19453       19457       40162+  ef  EFI (FAT-12/16/32)
/dev/sda5           13844       18942    40957717+   7  HPFS/NTFS
/dev/sda6            8415       13843    43608379+  83  Linux
/dev/sda7           18943       19452     4096543+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by soumo on 2009-11-16
Thanks for looking :)

---

### Post by soumo on 2009-11-23
Anyone?

---

### Post by rajasthanub on 2010-05-02
i am getting this message when i run fdisk -l

can u help 


omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbc1cbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/sda3            5101        7650    20482843+   b  W95 FAT32
/dev/sda5            2551        2672      979902   82  Linux swap / Solaris
/dev/sda6            2673        5100    19502878+  83  Linux
/dev/sda7            7651        9728    16691503+   b  W95 FAT32

---

