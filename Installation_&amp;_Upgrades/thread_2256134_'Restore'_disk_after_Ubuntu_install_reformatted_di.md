---
title: "'Restore' disk after Ubuntu install reformatted disk"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by mumbo2 on 2014-12-10
[B]Hi there,

In short I did an install of Ubuntu on a disk with two (three) partitions, ntfs, etx4 and swap. 
After the install Ubuntu was there with the total disk reformatted. Obvious not what I wanted. 
*My question is: Is is possible to get the old ntfs partition back?*


Problem is that the disk might be reformatted twice but I think it was reformatted onces 
because I think one of the times I saw an ntfs disk in the life session.

Another problem is the ntfs partition might be damaged by reformatting into ext lvm file system.
However files seems to be still there but need a deep scan to reach flatten file structure.[/B]


>Long story

**1) *What I did before and after problems*** + testdisk log file (see below)
a. Disk with an ntfs partition together with a (older) Ubuntu pre-installed on ext4 partition and with a swap partition.
b. Updated old ubuntu version with a live usb stick.
    It was succesfull. Also I think it left the ntfs partition untouched.
    But was unable to log in because of problems with acces to certain files.
c. First booted straight into 'grub rescue' mode.
    Guessing grub couldn't find the boot files.
    Another live session with the 'boot-repair' tool fixed the problem.
    But than (auto)login/Ubuntu startup hanged because of some file couldn't be accessed.
    (Couldn't find /dev/mapper/cryptswap1)
    Change of the disk reference (UUID) of the related file didn't solve the problem.    
    (think had something to do with swap, don't actually know)
    As the original account was encryppted (and choose the same encryption option at update)
    this might cause the problem of login (so I read).
c. To make life easy I went for the option to just do another (fresh) install 
     but this time with original os files deleted.
     To make life easy and avoid stupid misstake that I could make I choose the auto process,
     With the option of a LVM partition.
     Not realizing this will make life more difficult.
d. The current Ubuntu install process with mentioned options 'erased' (so I assumed)
     not only the partition of the current Ubuntu OS files but also the whole disk
     and made it into a ext file format!
     (Yes this is my own stupid misstake because the line beneath 
     the option of the install procedure said that everything will be erased.
     But it is also Ubuntu to blame just as much or not more.
     Because the text of the install option is left open for multiple interpretations.
     This is actually acknowledged by Ubuntu and they have it on their bug list for over a year.
     Furhter more I was expected to see an overview at the end of the install procedure 
     of the install processes. To exame the made choices. I blame not only myself but  mostly BAD design.)
e.  After the fresh install (after update and after so called 'second' install) in Ubuntu when I noticed no ntfs drive.
     (Downloaded gparted to confirm and :( )
     Disconnected drive and run some recovery tools.
f. Testdisk showed with a quick search two ext partitions. One with the Ubuntu os and one with ext lvm.
g. With a deep search it finds one NTFS partition (besides many ext patitions). (a possible ntfs partition that I want to recover)
    The partition however can not be read.
h. *_**What should be done in Testdisk?**_* (I find the info not very helpfull. Still have many questions?)

**2) Inestigated with tool**
i. Tried with another tool 'Partition find and  Mount' to acces the ntfs files (with file structure).
    [http://findandmount.com/](http://findandmount.com/)
f. Tool did find the ntfs partition also only with deep scan.
g. The discovered partition could be mounted.
h. However when accesed on vista the drive was unaccessible.
   The tool faq gives as anwser partition might be damaged.
i. Partition info from the tool:
    Starting LBA: 63
    Ending LBA: 428 116 58
    Capcity: 219 GB

**3) Investigated with tools**
j. Scan on vista with several tools show different partitions and results.
k. Vista disk manager shows two primary partitions one with 243 mb 
    and the other 232,65 GB (with unrecognized file system).
[SIZE=2](L. Recuva shows several 'unkown (\\.\HardiskVolume1)', 'unkown (\\.\HardiskVolume3)'...
    Some can be scanned and some not. One is a 10 GB NTFS (size doesn't seem right)
Others ares similar small sizes with ext4. 
    Some files can be recovered but most are unrecognizable, no name, structure.
    This layout of the disk is not how the disk was before the install.)[/SIZE]
IT SEEMS THAT SOME PARTITONS NOTIFIED IN RECUVA WERE FROM ANOTHER DISK

**3) *My other questions:***
j. [I][U]What does Ubuntu do when it deletes, reformat and install? 
    Does it makes changes to the whole disk or to some indexing files?[/U][/I]
k. *_Is my partition primary or logical?_*
    [http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical](http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical)
    Example is not clear to me. Yes it seems obvious but in reference to my example it is not.
   I see a lot of numbers: at which number does the partition start and stop.
   My ntfs partition as shown by testdisk (see below) does not indicate 1 1 or 0 1 but 1 10.
m. [U][I]Why are output numbers from tool 'Partition find and  Mount' and tool 'testdisk' different?
   Or are the outputs totally different and does LBA mean something else?
   Or are the numbers more a possible indication?
   Or does both tools find two different partitions?[/I][/U]
n. _*What does 'lseek err Invalid argument' from testdisk deepscan log results mean.*_
o. _*Is reformatting different than formating disk or partition?*_
p. _*Is reformatting different than deleting partition?*_


**4) Previous, prefered disk partition layout (as assumed)**
From the result of testdisk I think these partitions were on the disk before the install of Ubuntu:
Disk size 250 GB
> HPFS - NTFS partition with 219 GB / 204 GiB
   (0   1 10 26648 254 63  428116113)
    possible old storage partition
> ext4 partition with 29 GB / 27 GiB
   (26649   0  1 30237 254 63   57657285)
   possible os partition with old linux version
> swap partition with 1340 MB / 1278 MiB
   (30238   1  1 30400 254 63    2618532)
   possible swap partition
   
>>> ***_IS this layout correct?_*** I ask because I wonder where the partitions start and end.
   
      
[COLOR=#d3d3d3]
I forget it is better to wait with linux for two years before trying something new.
And when you do something do it yourself, do not let linux do it for you.
If it is not broken don't try/break it.
Coz one little change could break everything ;) .
And you have to go to the trouble of terminal.
With no little hope of succes.
Just jamming on the keyboard like a monkey[/COLOR]


[COLOR=#696969]
--------------------------------------------Testdisk log output - BEGIN --------------------------------------------------------------

Tue Dec  9 12:26:35 2014
Command line: TestDisk

TestDisk 7.0-WIP, Data Recovery Utility, October 2014
Christophe GRENIER <grenier@cgsecurity.org>
[/COLOR][[COLOR=#696969]http://www.cgsecurity.org[/COLOR]]("http://www.cgsecurity.org")[COLOR=#696969]
OS: Windows Vista (6002) SP2
Compiler: GCC 4.7, Cygwin 1007.25
Compilation date: 2014-11-13T18:59:50
ext2fs lib: 1.42.8, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20120504
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(/dev/sda)=160041885696
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(/dev/sdb)=250059350016
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\PhysicalDrive0)=160041885696
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\PhysicalDrive1)=250059350016
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\C:)=131148546048
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\D:)=2683305984
filewin32_getfilesize(\\.\E:) GetFileSize err Onjuiste functie.

filewin32_setfilepointer(\\.\E:) SetFilePointer err Onjuiste functie.

Warning: can't get size for \\.\E:
Hard disk list
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ST916082 3AS, S/N:N50KFJ91, FW:3.AD
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - Samsung STORY Station, S/N:801130168383

Partition table type (auto): Intel
Disk /dev/sdb - 250 GB / 232 GiB - Samsung STORY Station
Partition table type: Intel

Analyse Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
Geometry from i386 MBR: head=255 sector=63

LVM2 magic value at 31/59/29
Current partition structure:
 1 * Linux                    0  32 33    31  26 59     497664
 2 E extended                31  59 27 30401  75 10  487895042
 5 L Linux LVM               31  59 29 30401  75 10  487895040
Backup partition structure
partition_save

search_part()
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63

recover_EXT2: s_block_group_nr=0/30, s_mnt_count=2/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 33    31  26 59     497664
     ext2 blocksize=1024 Sparse superblock, 254 MB / 243 MiB

LVM2 magic value at 31/59/29
part_size 487895040
     Linux LVM               31  59 29 30401  75 10  487895040
     LVM2, 249 GB / 232 GiB
file_pread(5,2,buffer,488398848(30401/107/43)) lseek err Invalid argument
file_pread(5,1,buffer,488398848(30401/107/43)) lseek err Invalid argument
file_pread(5,2,buffer,488398901(30401/108/33)) lseek err Invalid argument
file_pread(5,1,buffer,488398901(30401/108/33)) lseek err Invalid argument
file_pread(5,2,buffer,488398911(30401/108/43)) lseek err Invalid argument
file_pread(5,1,buffer,488398911(30401/108/43)) lseek err Invalid argument
file_pread(5,2,buffer,488398964(30401/109/33)) lseek err Invalid argument
file_pread(5,1,buffer,488398964(30401/109/33)) lseek err Invalid argument
file_pread(5,8,buffer,488397184(30401/81/17)) lseek err Invalid argument
file_pread(5,1,buffer,488397184(30401/81/17)) lseek err Invalid argument
file_pread(5,8,buffer,488397312(30401/83/19)) lseek err Invalid argument
file_pread(5,8,buffer,488397440(30401/85/21)) lseek err Invalid argument
file_pread(5,8,buffer,488397568(30401/87/23)) lseek err Invalid argument
file_pread(5,8,buffer,488397696(30401/89/25)) lseek err Invalid argument
file_pread(5,8,buffer,488397824(30401/91/27)) lseek err Invalid argument
file_pread(5,8,buffer,488397952(30401/93/29)) lseek err Invalid argument
file_pread(5,8,buffer,488398080(30401/95/31)) lseek err Invalid argument
file_pread(5,8,buffer,488398208(30401/97/33)) lseek err Invalid argument
file_pread(5,8,buffer,488398336(30401/99/35)) lseek err Invalid argument
file_pread(5,8,buffer,488398464(30401/101/37)) lseek err Invalid argument
file_pread(5,8,buffer,488398592(30401/103/39)) lseek err Invalid argument
file_pread(5,8,buffer,488398720(30401/105/41)) lseek err Invalid argument
file_pread(5,1,buffer,488398847(30401/107/42)) lseek err Invalid argument
file_pread(5,1,buffer,488398848(30401/107/43)) lseek err Invalid argument
file_pread(5,14,buffer,488398849(30401/107/44)) lseek err Invalid argument
file_pread(5,3,buffer,488398863(30401/107/58)) lseek err Invalid argument
file_pread(5,3,buffer,488398910(30401/108/42)) lseek err Invalid argument
file_pread(5,8,buffer,488398926(30401/108/58)) lseek err Invalid argument
file_pread(5,11,buffer,488398973(30401/109/42)) lseek err Invalid argument
file_pread(5,2,buffer,488400895(30401/140/11)) lseek err Invalid argument

Results
   * Linux                    0  32 33    31  26 59     497664
     ext2 blocksize=1024 Sparse superblock, 254 MB / 243 MiB
   P Linux LVM               31  59 29 30401  75 10  487895040
     LVM2, 249 GB / 232 GiB


dir_partition inode=2
   * Linux                    0  32 33    31  26 59     497664
     ext2 blocksize=1024 Sparse superblock, 254 MB / 243 MiB
Directory /
       2 drwxr-xr-x     0      0      1024  8-Dec-2014 20:16 .
       2 drwxr-xr-x     0      0      1024  8-Dec-2014 20:16 ..
      11 drwx------     0      0     12288  8-Dec-2014 19:56 lost+found
   12049 drwxr-xr-x     0      0      1024  8-Dec-2014 20:14 grub
      12 -rw-------     0      0   3381262 15-Jul-2014 06:29 System.map-3.13.0-32-generic
      13 -rw-r--r--     0      0   1162712 15-Jul-2014 06:29 abi-3.13.0-32-generic
      14 -rw-r--r--     0      0    165611 15-Jul-2014 06:29 config-3.13.0-32-generic
      15 -rw-r--r--     0      0    176500 12-Mar-2014 13:31 memtest86+.bin
      16 -rw-r--r--     0      0    178176 12-Mar-2014 13:31 memtest86+.elf
      17 -rw-r--r--     0      0    178680 12-Mar-2014 13:31 memtest86+_multiboot.bin
      18 -rw-r--r--     0      0   5798112  8-Dec-2014 20:06 vmlinuz-3.13.0-32-generic
X     20 -rw-r--r--     0      0         0  8-Dec-2014 20:16 initrd.img-3.13.0-32-generic.dpkg-bak
      19 -rw-r--r--     0      0  19944721  8-Dec-2014 20:16 initrd.img-3.13.0-32-generic
X     19 -rw-r--r--     0      0  19944721  8-Dec-2014 20:16 initrd.img-3.13.0-32-generic.new

interface_write()
 1 * Linux                    0  32 33    31  26 59     497664
 2 P Linux LVM               31  59 29 30401  75 10  487895040
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.

search_part()
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63

recover_EXT2: s_block_group_nr=0/30, s_mnt_count=2/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 33    31  26 59     497664
     ext2 blocksize=1024 Sparse superblock, 254 MB / 243 MiB

block_group_nr 1

recover_EXT2: "e2fsck -b 8193 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=1/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

block_group_nr 3

recover_EXT2: "e2fsck -b 24577 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=3/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

block_group_nr 5

recover_EXT2: "e2fsck -b 40961 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=5/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

block_group_nr 7

recover_EXT2: "e2fsck -b 57345 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=7/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

block_group_nr 9

recover_EXT2: "e2fsck -b 73729 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=9/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

block_group_nr 25

recover_EXT2: "e2fsck -b 204801 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=25/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

block_group_nr 27

recover_EXT2: "e2fsck -b 221185 -B 1024 device" may be needed
recover_EXT2: s_block_group_nr=27/30, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 248832
recover_EXT2: part_size 497664
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB

LVM2 magic value at 31/59/29
part_size 487895040
     Linux LVM               31  59 29 30401  75 10  487895040
     LVM2, 249 GB / 232 GiB

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=3/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB

block_group_nr 1

recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=1/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 5

recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=5/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 7

recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=7/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 9

recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=9/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 25

recover_EXT2: "e2fsck -b 819200 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=25/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 27

recover_EXT2: "e2fsck -b 884736 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=27/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 49

recover_EXT2: "e2fsck -b 1605632 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=49/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 81

recover_EXT2: "e2fsck -b 2654208 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=81/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 125

recover_EXT2: "e2fsck -b 4096000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=125/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 243

recover_EXT2: "e2fsck -b 7962624 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=243/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 343

recover_EXT2: "e2fsck -b 11239424 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=343/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 625

recover_EXT2: "e2fsck -b 20480000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=625/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

block_group_nr 729

recover_EXT2: "e2fsck -b 23887872 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=729/1857, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 249 GB / 232 GiB

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                15197 101  9 45510  23 17  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
This partition ends after the disk limits. (start=244146176, size=486973440, end=731119615, disk end=488397168)

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                15200 181 22 45513 103 30  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
This partition ends after the disk limits. (start=244199424, size=486973440, end=731172863, disk end=488397168)

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                15201   1  1 45513 178  9  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
This partition ends after the disk limits. (start=244204128, size=486973440, end=731177567, disk end=488397168)

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                15203  99  1 45516  21  9  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
This partition ends after the disk limits. (start=244242432, size=486973440, end=731215871, disk end=488397168)

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                15204 136 37 45517  58 45  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
This partition ends after the disk limits. (start=244260864, size=486973440, end=731234303, disk end=488397168)

recover_EXT2: s_block_group_nr=0/1857, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 60871680
recover_EXT2: part_size 486973440
     Linux                15205 174 10 45518  96 18  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
This partition ends after the disk limits. (start=244279296, size=486973440, end=731252735, disk end=488397168)
NTFS at 26648/254/63
filesystem size           428116113
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               12207030
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1 10 26648 254 63  428116113
     NTFS found using backup sector, blocksize=4096, 219 GB / 204 GiB

recover_EXT2: s_block_group_nr=0/219, s_mnt_count=34/37, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7207160
recover_EXT2: part_size 57657280
     Linux                26649   0  1 30237 254 58   57657280
     ext4 blocksize=4096 Large file Sparse superblock, 29 GB / 27 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/219, s_mnt_count=0/37, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7207160
recover_EXT2: part_size 57657280
     Linux                26649   0  1 30237 254 58   57657280
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 29 GB / 27 GiB
     Linux Swap           30238   1  1 30400 254 43    2618512
     SWAP2 version 1, pagesize=4096, 1340 MB / 1278 MiB
     Linux Swap           30344  14  7 30400 167 23     909296
     SWAP2 version 1, pagesize=4096, 465 MB / 443 MiB
file_pread(5,2,buffer,488398848(30401/107/43)) lseek err Invalid argument
file_pread(5,1,buffer,488398848(30401/107/43)) lseek err Invalid argument
file_pread(5,2,buffer,488398901(30401/108/33)) lseek err Invalid argument
file_pread(5,1,buffer,488398901(30401/108/33)) lseek err Invalid argument
file_pread(5,2,buffer,488398911(30401/108/43)) lseek err Invalid argument
file_pread(5,1,buffer,488398911(30401/108/43)) lseek err Invalid argument
file_pread(5,2,buffer,488398964(30401/109/33)) lseek err Invalid argument
file_pread(5,1,buffer,488398964(30401/109/33)) lseek err Invalid argument
file_pread(5,8,buffer,488397184(30401/81/17)) lseek err Invalid argument
file_pread(5,1,buffer,488397184(30401/81/17)) lseek err Invalid argument
file_pread(5,8,buffer,488397277(30401/82/47)) lseek err Invalid argument
file_pread(5,8,buffer,488397312(30401/83/19)) lseek err Invalid argument
file_pread(5,8,buffer,488397405(30401/84/49)) lseek err Invalid argument
file_pread(5,8,buffer,488397440(30401/85/21)) lseek err Invalid argument
file_pread(5,8,buffer,488397533(30401/86/51)) lseek err Invalid argument
file_pread(5,8,buffer,488397568(30401/87/23)) lseek err Invalid argument
file_pread(5,8,buffer,488397661(30401/88/53)) lseek err Invalid argument
file_pread(5,8,buffer,488397696(30401/89/25)) lseek err Invalid argument
file_pread(5,8,buffer,488397789(30401/90/55)) lseek err Invalid argument
file_pread(5,8,buffer,488397824(30401/91/27)) lseek err Invalid argument
file_pread(5,8,buffer,488397917(30401/92/57)) lseek err Invalid argument
file_pread(5,8,buffer,488397952(30401/93/29)) lseek err Invalid argument
file_pread(5,8,buffer,488398045(30401/94/59)) lseek err Invalid argument
file_pread(5,8,buffer,488398080(30401/95/31)) lseek err Invalid argument
file_pread(5,8,buffer,488398173(30401/96/61)) lseek err Invalid argument
file_pread(5,8,buffer,488398208(30401/97/33)) lseek err Invalid argument
file_pread(5,8,buffer,488398301(30401/98/63)) lseek err Invalid argument
file_pread(5,8,buffer,488398336(30401/99/35)) lseek err Invalid argument
file_pread(5,8,buffer,488398429(30401/101/2)) lseek err Invalid argument
file_pread(5,8,buffer,488398464(30401/101/37)) lseek err Invalid argument
file_pread(5,8,buffer,488398557(30401/103/4)) lseek err Invalid argument
file_pread(5,8,buffer,488398592(30401/103/39)) lseek err Invalid argument
file_pread(5,8,buffer,488398685(30401/105/6)) lseek err Invalid argument
file_pread(5,8,buffer,488398720(30401/105/41)) lseek err Invalid argument
file_pread(5,8,buffer,488398813(30401/107/8)) lseek err Invalid argument
file_pread(5,1,buffer,488398847(30401/107/42)) lseek err Invalid argument
file_pread(5,1,buffer,488398848(30401/107/43)) lseek err Invalid argument
file_pread(5,14,buffer,488398849(30401/107/44)) lseek err Invalid argument
file_pread(5,3,buffer,488398863(30401/107/58)) lseek err Invalid argument
file_pread(5,3,buffer,488398910(30401/108/42)) lseek err Invalid argument
file_pread(5,8,buffer,488398926(30401/108/58)) lseek err Invalid argument
file_pread(5,11,buffer,488398973(30401/109/42)) lseek err Invalid argument
file_pread(5,2,buffer,488400895(30401/140/11)) lseek err Invalid argument
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (250 GB / 232 GiB) seems too small! (< 374 GB / 348 GiB)
The following partitions can't be recovered:
     Linux                15197 101  9 45510  23 17  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
     Linux                15200 181 22 45513 103 30  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
     Linux                15201   1  1 45513 178  9  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
     Linux                15203  99  1 45516  21  9  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
     Linux                15204 136 37 45517  58 45  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
     Linux                15205 174 10 45518  96 18  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=255 nbr=4

Results
     HPFS - NTFS              0   1 10 26648 254 63  428116113
     NTFS found using backup sector, blocksize=4096, 219 GB / 204 GiB
     Linux                    0  32 31    31  26 57     497664
     ext2 blocksize=1024 Sparse superblock Backup superblock, 254 MB / 243 MiB
     Linux                    0  32 33    31  26 59     497664
     ext2 blocksize=1024 Sparse superblock, 254 MB / 243 MiB
     Linux LVM               31  59 29 30401  75 10  487895040
     LVM2, 249 GB / 232 GiB
     Linux                   31  91 61 30344  14  6  486973440
     ext4 blocksize=4096 Large file Sparse superblock Recover, 249 GB / 232 GiB
     Linux                26649   0  1 30237 254 63   57657285
     ext4 blocksize=4096 Large file Sparse superblock, 29 GB / 27 GiB
     Linux Swap           30238   1  1 30400 254 63    2618532
     SWAP2 version 1, pagesize=4096, 1340 MB / 1278 MiB
     Linux Swap           30344  14  7 30400 167 39     909312
     SWAP2 version 1, pagesize=4096, 465 MB / 444 MiB
Not an exFAT boot sector.

     HPFS - NTFS              0   1 10 26648 254 63  428116113
     NTFS found using backup sector, blocksize=4096, 219 GB / 204 GiB
Can't open filesystem. Filesystem seems damaged.he website of testdisk

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

--------------------------------------------Testdisk log output - END --------------------------------------------------------------


ps. It would be helpfull when helping to explain what the process/commands do with one or two lines of text.
    It could also be helpfull to just add a line in front of the command.
    For example a made up command:
    [root acces] [install programm] [-a(utomatic)] [-r(emove)] [text file on desktop]
    sudo apt-got -a -r /home/desktop/help.txt
    
    (It would also be helpfull of some explanatory info lines were added to testdisk procedures 
    instead on listing the text on a 'lost' webpage of testdisk.
    For example analysis: will scan certain small disk locations to indicate boottable or someting like that)[/COLOR]

    
        
**WHATEVER YOU DO I APPRECIATE YOUR EFFORT.**

_**>>>  TANKS IN ADVANCE  <<<**_

---

### Post by mumbo2 on 2014-12-10
I think in my case the reformat and instal of Ubuntu overwritten some parts of the ntfs partition and that is why the ntfs file system is damage and can not be accessed directly.    

Fiona from cgs forum points out that the old ntfs partition and the new ext partitions overlap. Ntfs partition is partly overwritten:  
HPFS - NTFS 0 1 10 26648 254 63 428116113 
NTFS found using backup sector, blocksize=4096, [COLOR=#BF0000]219 GB / 204 GiB  [COLOR=#BF0000]* 

Linux 0 32 33 31 26 59 497664[/COLOR] 
ext2 blocksize=1024 Sparse superblock, 254 MB / 243 MiB [/COLOR]   

My next question is: is there a tool, procedure, method anything to get my files from the ntfs partition back with filenames and folder strucure. I assume most files are still there and it is known from testdisk that the filesystem was a ntfs filesystem and the beginning and end of the partition is known and also is known that there is a backup file MTF (so I assume at backup sector). So there must be a way to get my folder/files back> Am I right?    

**No one has the anwser to my questions?**

---

