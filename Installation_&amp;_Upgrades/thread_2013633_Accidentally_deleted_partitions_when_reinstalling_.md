---
title: "Accidentally deleted partitions when reinstalling Ubuntu, need help recovering data."
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by thunderpenguin on 2012-07-01
Hi

I have a laptop with a 500 GB harddisk. It had a Ubuntu and  Windows 7 dualboot but now after a partitioning mistake it only has  Ubuntu.

For Ubuntu I had a root partition, a home partition and a swap partition. 
For Windows I had a main partition and a backup partition for  backing up data on the main partition.

In my home partition I had some encrypted home folders from previous Ubuntu installs.

I wanted to access the data in these encrypted partitions.

I  followed this webpage  [https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)  and I created a new folder called backup in my home partition to copy  the data from the encrypted home folders.

I managed to put all the data from the encrypted home folders into the backup folder.

I deleted all the encrypted home folders.

I decided to reinstall Ubuntu and choose not to encrypt the new user's home folder.

In  the installer's partitioning stage it told me Ubuntu and Windows were  already on the harddisk and whether to install alongside or erase entire  disk and install Ubuntu.

Without thinking properly I chose to erase entire disk and install Ubuntu.

I didn't notice my mistake until after I had installed Ubuntu and installed the updates for Ubuntu.

I  followed this webpage:  [http://www.dedoimedo.com/computers/linux-data-recovery.html](http://www.dedoimedo.com/computers/linux-data-recovery.html) which shows  how to use Testdisk to recover deleted data and partitions.

Analyse only showed my current Linux partitions so I did Deeper Search.

After Deeper Search finished it gave me a message saying the harddisk is too small and it can't recover some of my data.

I am not sure what to do after this.

I have attached screenshots of testdisk during deeper search and after deeper search 

Here is my testdisk.log file

```


Sun Jul  1 03:48:49 2012
Command line: TestDisk

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.2.0-23-generic (#36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012) x86_64
Compiler: GCC 4.6
Compilation date: 2012-02-05T07:15:52
ext2fs lib: 1.42, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: native_max 976773168 sectors
/dev/sda: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - SAMSUNG HM500JI, S/N:S20CJ9GZ404820, FW:2AC101C4
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - WD 10EAVS External, FW:1.75
Disk /dev/sr0 - 839 MB / 801 MiB - CHS 410112 1 1 (RO), sector size=2048 - TSSTcorp CDDVDW TS-L633C, S/N:d1F3456789 L N3P, FW:SC00

Partition table type (auto): Intel
Disk /dev/sda - 500 GB / 465 GiB - SAMSUNG HM500JI
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
Current partition structure:
 1 * Linux                    0  32 33 60296 221 21  968667136
 2 E extended             60296 253 52 60801  47 46    8099842
 5 L Linux Swap           60296 253 54 60801  47 46    8099840
Computes LBA from CHS for Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=8/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB

Results
   * Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
   P Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB

interface_write()
 1 * Linux                    0  32 33 60296 221 21  968667136
 2 P Linux Swap           60296 253 54 60801  47 30    8099824

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=8/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
NTFS at 1958/64/26
filesystem size           31457280
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               1966079
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33  1958  64 26   31457280
     NTFS found using backup sector!, 16 GB / 15 GiB
NTFS at 1958/64/27
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1958  64 27  1971   0 13     204800 [System Reserved]
     NTFS, 104 MB / 100 MiB
NTFS at 1971/0/13
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1958  64 27  1971   0 13     204800 [System Reserved]
     NTFS found using backup sector!, 104 MB / 100 MiB
NTFS at 1971/0/14
filesystem size           472551424
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1971   0 14 31385 246 29  472551424
     NTFS, 241 GB / 225 GiB

recover_EXT2: s_block_group_nr=0/41, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1375232
recover_EXT2: part_size 11001856
     Linux                10964 122 39 11649  80 15   11001856
     EXT4 Large file Sparse superblock Recover, 5632 MB / 5372 MiB

recover_EXT2: s_block_group_nr=0/153, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5016832
recover_EXT2: part_size 40134656
     Linux                11737  38 14 14235 106 15   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/153, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5016832
recover_EXT2: part_size 40134656
     Linux                11740 215 60 14239  28 61   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/153, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5016832
recover_EXT2: part_size 40134656
     Linux                11748  61 26 14246 129 27   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=3/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30041 202 50 90338 136 38  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482621440, size=968667136, end=1451288575, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=2/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30046 195 38 90343 129 26  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482701312, size=968667136, end=1451368447, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30051  90 56 90348  24 44  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482775040, size=968667136, end=1451442175, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30054   8 35 90350 197 23  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482818048, size=968667136, end=1451485183, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30054  73 36 90351   7 24  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482822144, size=968667136, end=1451489279, disk end=976784130)
NTFS at 31385/246/29
filesystem size           472551424
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1971   0 14 31385 246 29  472551424
     NTFS found using backup sector!, 241 GB / 225 GiB
NTFS at 31385/246/30
filesystem size           472555520
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          31385 246 30 60801  47 46  472555520
     NTFS, 241 GB / 225 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=60/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4882432
recover_EXT2: part_size 39059456
     Linux                31386  23 62 33817 110 21   39059456
     EXT4 Large file Sparse superblock, 19 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=59/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4882432
recover_EXT2: part_size 39059456
     Linux                32448 102 39 34879 188 61   39059456
     EXT4 Large file Sparse superblock Recover, 19 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=57/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4882432
recover_EXT2: part_size 39059456
     Linux                32454 132 63 34885 219 22   39059456
     EXT4 Large file Sparse superblock Recover, 19 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/1638, s_mnt_count=30/26, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 53698560
recover_EXT2: part_size 429588480
     Linux                34060 170 31 60801  80 15  429588480
     EXT4 Large file Sparse superblock, 219 GB / 204 GiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39173  86 18 40157 127 34   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39173 216 20 40158   2 36   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39175  63 57 40159 105 10   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39178 144  7 40162 185 23   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39178 209  8 40162 250 24   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
BAD_RS LBA=690532352 11084850
check_part_i386 failed for partition type 0C
     FAT32 LBA            42983 165 63 42983 198 31       2048
BAD_RS LBA=697872384 11084850
check_part_i386 failed for partition type 0C
     FAT32 LBA            43440 139 28 43440 171 59       2048
FAT12 at 44132/2/31
FAT1 : 1-2
FAT2 : 3-4
start_rootdir : 5
Data : 37-2044
sectors : 2048
cluster_size : 4
no_of_cluster : 502 (2 - 503)
fat_length 2 calculated 2
heads/cylinder 64 (FAT) != 255 (HD)
sect/track 32 (FAT) != 63 (HD)

FAT12 at 44132/2/31
     FAT12                44132   2 31 44132  34 62       2048 [RESIZE_ME]
     FAT12, 1048 KB / 1024 KiB

recover_EXT2: s_block_group_nr=0/1638, s_mnt_count=28/26, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 53698560
recover_EXT2: part_size 429588480
     Linux                47401 138 34 74142  48 18  429588480
     EXT4 Large file Sparse superblock Recover, 219 GB / 204 GiB
This partition ends after the disk limits. (start=761505792, size=429588480, end=1191094271, disk end=976784130)
     Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (500 GB / 465 GiB) seems too small! (< 743 GB / 692 GiB)
The following partitions can't be recovered:
     Linux                30041 202 50 90338 136 38  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30046 195 38 90343 129 26  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30051  90 56 90348  24 44  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30054   8 35 90350 197 23  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30054  73 36 90351   7 24  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                47401 138 34 74142  48 18  429588480
     EXT4 Large file Sparse superblock Recover, 219 GB / 204 GiB

Results
     HPFS - NTFS              0  32 33  1958  64 26   31457280
     NTFS found using backup sector!, 16 GB / 15 GiB
     Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     HPFS - NTFS           1958  64 27  1971   0 13     204800 [System Reserved]
     NTFS, 104 MB / 100 MiB
     HPFS - NTFS           1971   0 14 31385 246 29  472551424
     NTFS, 241 GB / 225 GiB
     Linux                10964 122 39 11649  80 15   11001856
     EXT4 Large file Sparse superblock Recover, 5632 MB / 5372 MiB
     Linux                11737  38 14 14235 106 15   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB
     Linux                11740 215 60 14239  28 61   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB
     Linux                11748  61 26 14246 129 27   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB
     HPFS - NTFS          31385 246 30 60801  47 46  472555520
     NTFS, 241 GB / 225 GiB
     Linux                31386  23 62 33817 110 21   39059456
     EXT4 Large file Sparse superblock, 19 GB / 18 GiB
     Linux                32448 102 39 34879 188 61   39059456
     EXT4 Large file Sparse superblock Recover, 19 GB / 18 GiB
     Linux                32454 132 63 34885 219 22   39059456
     EXT4 Large file Sparse superblock Recover, 19 GB / 18 GiB
     Linux                34060 170 31 60801  80 15  429588480
     EXT4 Large file Sparse superblock, 219 GB / 204 GiB
     Linux                39173  86 18 40157 127 34   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
     Linux                39173 216 20 40158   2 36   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
     Linux                39175  63 57 40159 105 10   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
     Linux                39178 144  7 40162 185 23   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
     Linux                39178 209  8 40162 250 24   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
     FAT32 LBA            42983 165 63 42983 198 31       2048
     FAT32 LBA            43440 139 28 43440 171 59       2048
     FAT12                44132   2 31 44132  34 62       2048 [RESIZE_ME]
     FAT12, 1048 KB / 1024 KiB
     Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Geometry from i386 MBR: head=255 sector=63
Current partition structure:
 1 * Linux                    0  32 33 60296 221 21  968667136
 2 E extended             60296 253 52 60801  47 46    8099842
 5 L Linux Swap           60296 253 54 60801  47 46    8099840
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=8/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB

Results
   * Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
   P Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB

interface_write()
 1 * Linux                    0  32 33 60296 221 21  968667136
 2 P Linux Swap           60296 253 54 60801  47 30    8099824

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=8/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
NTFS at 1958/64/26
filesystem size           31457280
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               1966079
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33  1958  64 26   31457280
     NTFS found using backup sector!, 16 GB / 15 GiB
NTFS at 1958/64/27
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1958  64 27  1971   0 13     204800 [System Reserved]
     NTFS, 104 MB / 100 MiB
NTFS at 1971/0/13
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1958  64 27  1971   0 13     204800 [System Reserved]
     NTFS found using backup sector!, 104 MB / 100 MiB
NTFS at 1971/0/14
filesystem size           472551424
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1971   0 14 31385 246 29  472551424
     NTFS, 241 GB / 225 GiB

recover_EXT2: s_block_group_nr=0/41, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1375232
recover_EXT2: part_size 11001856
     Linux                10964 122 39 11649  80 15   11001856
     EXT4 Large file Sparse superblock Recover, 5632 MB / 5372 MiB

recover_EXT2: s_block_group_nr=0/153, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5016832
recover_EXT2: part_size 40134656
     Linux                11737  38 14 14235 106 15   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/153, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5016832
recover_EXT2: part_size 40134656
     Linux                11740 215 60 14239  28 61   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/153, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5016832
recover_EXT2: part_size 40134656
     Linux                11748  61 26 14246 129 27   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=3/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30041 202 50 90338 136 38  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482621440, size=968667136, end=1451288575, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=2/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30046 195 38 90343 129 26  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482701312, size=968667136, end=1451368447, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30051  90 56 90348  24 44  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482775040, size=968667136, end=1451442175, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30054   8 35 90350 197 23  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482818048, size=968667136, end=1451485183, disk end=976784130)

recover_EXT2: s_block_group_nr=0/3695, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 121083392
recover_EXT2: part_size 968667136
     Linux                30054  73 36 90351   7 24  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
This partition ends after the disk limits. (start=482822144, size=968667136, end=1451489279, disk end=976784130)
NTFS at 31385/246/29
filesystem size           472551424
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           1971   0 14 31385 246 29  472551424
     NTFS found using backup sector!, 241 GB / 225 GiB
NTFS at 31385/246/30
filesystem size           472555520
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          31385 246 30 60801  47 46  472555520
     NTFS, 241 GB / 225 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=60/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4882432
recover_EXT2: part_size 39059456
     Linux                31386  23 62 33817 110 21   39059456
     EXT4 Large file Sparse superblock, 19 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=59/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4882432
recover_EXT2: part_size 39059456
     Linux                32448 102 39 34879 188 61   39059456
     EXT4 Large file Sparse superblock Recover, 19 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=57/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4882432
recover_EXT2: part_size 39059456
     Linux                32454 132 63 34885 219 22   39059456
     EXT4 Large file Sparse superblock Recover, 19 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/1638, s_mnt_count=30/26, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 53698560
recover_EXT2: part_size 429588480
     Linux                34060 170 31 60801  80 15  429588480
     EXT4 Large file Sparse superblock, 219 GB / 204 GiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39173  86 18 40157 127 34   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39173 216 20 40158   2 36   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39175  63 57 40159 105 10   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39178 144  7 40162 185 23   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB

recover_EXT2: s_block_group_nr=0/60, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1976320
recover_EXT2: part_size 15810560
     Linux                39178 209  8 40162 250 24   15810560 [_CentOS-6.2-x86_]
     EXT4 Large file Sparse superblock Recover, 8095 MB / 7720 MiB
BAD_RS LBA=690532352 11084850
check_part_i386 failed for partition type 0C
     FAT32 LBA            42983 165 63 42983 198 31       2048
BAD_RS LBA=697872384 11084850
check_part_i386 failed for partition type 0C
     FAT32 LBA            43440 139 28 43440 171 59       2048
FAT12 at 44132/2/31
FAT1 : 1-2
FAT2 : 3-4
start_rootdir : 5
Data : 37-2044
sectors : 2048
cluster_size : 4
no_of_cluster : 502 (2 - 503)
fat_length 2 calculated 2
heads/cylinder 64 (FAT) != 255 (HD)
sect/track 32 (FAT) != 63 (HD)

FAT12 at 44132/2/31
     FAT12                44132   2 31 44132  34 62       2048 [RESIZE_ME]
     FAT12, 1048 KB / 1024 KiB

recover_EXT2: s_block_group_nr=0/1638, s_mnt_count=28/26, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 53698560
recover_EXT2: part_size 429588480
     Linux                47401 138 34 74142  48 18  429588480
     EXT4 Large file Sparse superblock Recover, 219 GB / 204 GiB
This partition ends after the disk limits. (start=761505792, size=429588480, end=1191094271, disk end=976784130)
     Linux Swap           60296 253 54 60801  47 30    8099824
     SWAP2 version 1, 4147 MB / 3954 MiB
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (500 GB / 465 GiB) seems too small! (< 743 GB / 692 GiB)
The following partitions can't be recovered:
     Linux                30041 202 50 90338 136 38  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30046 195 38 90343 129 26  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30051  90 56 90348  24 44  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30054   8 35 90350 197 23  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                30054  73 36 90351   7 24  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     Linux                47401 138 34 74142  48 18  429588480
     EXT4 Large file Sparse superblock Recover, 219 GB / 204 GiB

Results
     HPFS - NTFS              0  32 33  1958  64 26   31457280
     NTFS found using backup sector!, 16 GB / 15 GiB
     Linux                    0  32 33 60296 221 21  968667136
     EXT4 Large file Sparse superblock Recover, 495 GB / 461 GiB
     HPFS - NTFS           1958  64 27  1971   0 13     204800 [System Reserved]
     NTFS, 104 MB / 100 MiB
     HPFS - NTFS           1971   0 14 31385 246 29  472551424
     NTFS, 241 GB / 225 GiB
     Linux                10964 122 39 11649  80 15   11001856
     EXT4 Large file Sparse superblock Recover, 5632 MB / 5372 MiB
     Linux                11737  38 14 14235 106 15   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB
     Linux                11740 215 60 14239  28 61   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB
     Linux                11748  61 26 14246 129 27   40134656
     EXT4 Large file Sparse superblock Recover, 20 GB / 19 GiB
     HPFS
```[IMG]http://www.dropbox.com/s/8on2p47p6jyj18f/testdiskdeepersearch.png[/IMG][IMG]https://www.dropbox.com/s/8on2p47p6jyj18f/testdiskdeepersearch.png[/IMG]

I am not sure why the second and fourth partition are describing some partitions as centos. I had centos in a virtualbox vm maybe that is why,

Please help me recover my partitions and data. 
[IMG]https://www.dropbox.com/s/8on2p47p6jyj18f/testdiskdeepersearch.png[/IMG]


[IMG]https://www.dropbox.com/s/8on2p47p6jyj18f/testdiskdeepersearch.png[/IMG]

---

### Post by Dedoimedo on 2012-07-02
If you actually deleted partitions and then placed several GB worth of data over them, then it will be extremely difficult to virtually impossible to recover data. One of the first steps in recovery is not to change things.

You will probably never get your partitions back, so you should try data recovery only and salvage files, as many as you can.

Regards,
Dedoimedo

---

### Post by raja.genupula on 2012-07-02
[https://help.ubuntu.com/community/DataRecovery/](https://help.ubuntu.com/community/DataRecovery/) read this .

---

### Post by thunderpenguin on 2012-07-02
Thank you. I used Photorec to recover most of my data.

---

