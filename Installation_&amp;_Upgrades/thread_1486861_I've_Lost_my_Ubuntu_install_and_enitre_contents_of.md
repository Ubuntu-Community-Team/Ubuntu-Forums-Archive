---
title: "I've Lost my Ubuntu install and enitre contents of HD!? :("
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Sarlix on 2010-05-18
Hi everyone, I'm not really sure how to start this post as I'm still in shell shock lol.

OK, this morning I decide it was time to format my windows partition (I dual boot windows and Ubuntu 9.10 Karmic ) I've done it before with no problems. It finished formatting the windows partition (I used my windows CD to boot into the repair console and formatted it from there)

I rebooted and was surprised to see the boot grub wasn't there any more. I know it tends to disappear when you install windows, but I don't remember it disappearing after getting rid of windows. I thought it would be no big deal and I would just need to follow the steps on how to get the grub back after a windows install. I followed the steps as normal but it didn't work, I kept on getting an 'error 17 something' when typing 'setup (hd0)' These were the commands I was using. 
        ```

   sudo grub

> root (hd0,0)

> setup (hd0)
```I rebooted anyway just to see if the grub was back, but it wasn't and it just says 'operating system not found' 

Prior to trying to get the grub back I could see my hard drive within the Ubuntu live cd (where I'm typing from now) it appeared under the 'places tab' but after doing the above commands and rebooting it's gone, which makes me think I have lost the contents of my whole hard drive! I can't access it at all. 

I can handle loosing all my media, photos, etc, but I had some artwork I have been working on for months, and completely irreplaceable. I would be pretty crushed if I've lost it. I know your thinking 'he should of backed it up' well I thought I had, but it appears I didn't...

Basically I'm hear to ask, beg, plead for ANY help anyone can give me. I don't know a lot about Linux and am totally out of my depth and have no idea what to do next. 

I guess you would want my read-out from the fdisk -l command so here it is:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14427      126993   850995205    7  HPFS/NTFS
/dev/sda2           48218       84195   271987362   74  Unknown

Disk /dev/sdb: 509 MB, 509410816 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c51687

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          62      497440    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(60, 254, 63) logical=(61, 237, 47)
ubuntu@ubuntu:~$ 
```It looked a lot different earlier, before trying to get the grub back. Which gives me another reason to think I've lost everything. If this is indeed the case, please break it to me gently as I think I might pass out.

Any help would be GREATLY appreciated. And please don't make fun of me for making such a complete hash of things. Thanks!

---

### Post by darkod on 2010-05-18
1. If you had a clean install of Karmic, it is coming with grub2, not the older grub1. The commands you quoted are for grub1.

2. You are right, your fdisk results look very bad, especially because according to the sectors numbers it looks like /dev/sda2 is inside /dev/sda1.

A good tool for recovery of lost partition is TestDisk. You can even install it and use it in live mode with:

sudo apt-get install testdisk

The software homepage:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

However, I don't have experience recovering with it, and can't give you step by step. I don't want to guess because I might make it even worse for you, and it's bad enough.

The website should have info how to use it. And other people here know, just hopefully they are online and will visit your thread.

---

### Post by Sarlix on 2010-05-18
Thanks for the quick reply!  I will look at TestDisk and the link you gave. Thank you.

---

### Post by kansasnoob on 2010-05-18
Be sure and look at the PhotoRec section:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

It's part of TestDisk and it's NOT just for photos.

I've had fairly good luck with it, just be patient and prepare for a challenge.

---

### Post by Sarlix on 2010-05-18
Hi again, I managed to get Testdisk installed and it found my three partitions, but I'm confused about the results and how to proceed. 



```
TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 39169 254 63  629265987
L Linux                39170   1  1 59917 254 63  333316557
L Linux Swap           59918   1  1 60800 254 63   14185332


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 170 GB / 158 GiB
``` "L Linux" is the partition my Ubuntu install is on, but I can't seem to access it. From what I understand I should be able to list files by pressing 'P' but it just dumps a load of data into a log file and I don't understand any of it. 


If I press Enter to continue I get taken to this screen:

```
TestDisk 6.11.3, Data Recovery 
Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 39169 254 63  629265987
 2 E extended LBA         39170   0  1 60800 254 63  347502015
 5 L Linux                39170   1  1 59917 254 63  333316557
 6 L Linux Swap           59918   1  1 60800 254 63   14185332

[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions

```And I have no idea what to do next. If I highlight 'write' it says "write partition structure to disk" 

If anyone can offer any further advice I would be most great full. :)

PS Thank you kansasnoob, I will take a look at PhotoRec if I have no luck with testdisk.


PPS This is my Testdisk log file if anyone can make any sense of it.



```
Tue May 18 18:46:48 2010
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009)
Compiler: GCC 3.4 - May  6 2009 14:37:46
ext2fs lib: 1.35, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: native_max 976773168 sectors
/dev/sda: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA ST3500418AS
Disk /dev/sdb - 509 MB / 485 MiB - CHS 1019 16 61, sector size=512 - CBM Flash Disk
Disk /dev/sr0 - 723 MB / 689 MiB - CHS 353266 1 1 (RO), sector size=2048 - TSSTcorp CDDVDW SH-S203D

Partition table type (auto): Intel
Disk /dev/sda - 500 GB / 465 GiB - ATA ST3500418AS
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=240 sector=63
check_part_i386 failed for partition type 07
check_part_i386 2 type 74: no test
Current partition structure:
Invalid NTFS or EXFAT boot
 1 * HPFS - NTFS          13577 238 11 119521 238 60 1701990410
 1 * HPFS - NTFS          13577 238 11 119521 238 60 1701990410
 2 P Sys=74               45381  70  3 79242  34 29  543974724
Space conflict between the following two partitions
 1 * HPFS - NTFS          13577 238 11 119521 238 60 1701990410
 2 P Sys=74               45381  70  3 79242  34 29  543974724
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
NTFS at 0/1/1
filesystem size           629265987
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               39329124
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 39169 254 63  629265987
     NTFS, 322 GB / 300 GiB

recover_EXT2: s_block_group_nr=0/1271, s_mnt_count=27/38, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 41664569
recover_EXT2: part_size 333316552
     Linux                39170   1  1 59917 254 58  333316552
     EXT4 Large file Sparse superblock, 170 GB / 158 GiB
     Linux Swap           59918   1  1 60800 254 43   14185312
     SWAP2 version 1, 7262 MB / 6926 MiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   * HPFS - NTFS              0   1  1 39169 254 63  629265987
     NTFS, 322 GB / 300 GiB
   L Linux                39170   1  1 59917 254 63  333316557
     EXT4 Large file Sparse superblock, 170 GB / 158 GiB
   L Linux Swap           59918   1  1 60800 254 63   14185332
     SWAP2 version 1, 7262 MB / 6926 MiB


Tue May 18 18:48:50 2010
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009)
Compiler: GCC 3.4 - May  6 2009 14:37:46
ext2fs lib: 1.35, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: native_max 976773168 sectors
/dev/sda: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA ST3500418AS
Disk /dev/sdb - 509 MB / 485 MiB - CHS 1019 16 61, sector size=512 - CBM Flash Disk
Disk /dev/sr0 - 723 MB / 689 MiB - CHS 353266 1 1 (RO), sector size=2048 - TSSTcorp CDDVDW SH-S203D

Partition table type (auto): Intel
Disk /dev/sda - 500 GB / 465 GiB - ATA ST3500418AS
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=240 sector=63
check_part_i386 failed for partition type 07
check_part_i386 2 type 74: no test
Current partition structure:
Invalid NTFS or EXFAT boot
 1 * HPFS - NTFS          13577 238 11 119521 238 60 1701990410
 1 * HPFS - NTFS          13577 238 11 119521 238 60 1701990410
 2 P Sys=74               45381  70  3 79242  34 29  543974724
Space conflict between the following two partitions
 1 * HPFS - NTFS          13577 238 11 119521 238 60 1701990410
 2 P Sys=74               45381  70  3 79242  34 29  543974724
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
NTFS at 0/1/1
filesystem size           629265987
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               39329124
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 39169 254 63  629265987
     NTFS, 322 GB / 300 GiB

recover_EXT2: s_block_group_nr=0/1271, s_mnt_count=27/38, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 41664569
recover_EXT2: part_size 333316552
     Linux                39170   1  1 59917 254 58  333316552
     EXT4 Large file Sparse superblock, 170 GB / 158 GiB
     Linux Swap           59918   1  1 60800 254 43   14185312
     SWAP2 version 1, 7262 MB / 6926 MiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   * HPFS - NTFS              0   1  1 39169 254 63  629265987
     NTFS, 322 GB / 300 GiB
   L Linux                39170   1  1 59917 254 63  333316557
     EXT4 Large file Sparse superblock, 170 GB / 158 GiB
   L Linux Swap           59918   1  1 60800 254 63   14185332
     SWAP2 version 1, 7262 MB / 6926 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1 39169 254 63  629265987
 2 E extended LBA         39170   0  1 60800 254 63  347502015
 5 L Linux                39170   1  1 59917 254 63  333316557
 6 L Linux Swap           59918   1  1 60800 254 63   14185332
```Sorry for all the text.

---

### Post by darkod on 2010-05-18
> **Sarlix said:**
> 

If I press Enter to continue I get taken to this screen:

```
TestDisk 6.11.3, Data Recovery 
Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 39169 254 63  629265987
 2 E extended LBA         39170   0  1 60800 254 63  347502015
 5 L Linux                39170   1  1 59917 254 63  333316557
 6 L Linux Swap           59918   1  1 60800 254 63   14185332

[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions

```And I have no idea what to do next. If I highlight 'write' it says "write partition structure to disk" 

If anyone can offer any further advice I would be most great full. :)


This looks good to me, in theory. The sectors match as sequential partitions. Write partition table is what you would need, that would tell the hdd (and to the OSs) what is where.

But I have never used this, wait for second opinion. :)

Kansas, you still out there? :)

---

### Post by Sarlix on 2010-05-18
OK thanks Darkod, I will wait for a second opinion before proceeding then. In the mean time I will continue to study that wiki page for any insight. If I manage to get this sorted I'll be sure to make a full account of what I did, as to help any others in a similar position.

:)

---

### Post by darkod on 2010-05-18
The more I think about it, I'm 99% sure you only need to make that choice Write partition table. The sectors look correct, your disk has 60801, out of which windows is until 39169, and from 39170 the extended partition starts with root and swap inside sharing it split by sector 59917.

I think you can be very optimistic.

But again, I never tried this. :) It looks right to me, just hitting that option will probably solve your pain. :)

---

### Post by vince2678 on 2010-05-18
> **Sarlix said:**
> Hi again, I managed to get Testdisk installed and it found my three partitions, but I'm confused about the results and how to proceed. 



```
TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 39169 254 63  629265987
L Linux                39170   1  1 59917 254 63  333316557
L Linux Swap           59918   1  1 60800 254 63   14185332


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 170 GB / 158 GiB
``` "L Linux" is the partition my Ubuntu install is on, but I can't seem to access it. From what I understand I should be able to list files by pressing 'P' but it just dumps a load of data into a log file and I don't understand any of it. 


If I press Enter to continue I get taken to this screen:

```
TestDisk 6.11.3, Data Recovery 
Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 39169 254 63  629265987
 2 E extended LBA         39170   0  1 60800 254 63  347502015
 5 L Linux                39170   1  1 59917 254 63  333316557
 6 L Linux Swap           59918   1  1 60800 254 63   14185332

[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions

```

Why not try to write to disk ? Or use the data with fdisk and enter the starts and ends manually?

---

### Post by Sarlix on 2010-05-19
Hi guys, just letting you know I managed to retrieve my lost data! The 'write partition structure to disk' option did the trick. So yay!

Thanks for all the input, I couldn't of done it without you. And a special thanks to Darkod.

Below, I'm going to go through the process I followed to resolve my issue, and hope it may help anyone else who happens to stumble upon this thread.



The "sudo apt-get install testdisk" command didn't work for me, so I had to go to the Testdisk site and download a RPM file. Which I then had to make into a Deb file by using a program called 'Alien'

(Disclaimer: This is probably a very non professional way of doing this, but hey-ho :)

I downloaded the RPM file from: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)  and saved it to the Desktop.

Then opened the terminal and typed:

```
sudo apt-get install alien
```I then pointed to where the RPM was, in my case:

```
ubuntu@ubuntu:~$ cd Desktop
```Then

```
sudo alien -k "name of the RPM file".rpm
```That should of made a Deb file and placed it on the Desktop

Now you can just double click the Deb file to install testdisk, or:

```
sudo alien -i "name of the Deb file".deb
```Next you need to make a folder for testdisk to save it's log file/s to, or anything else it might output. For ease I made a folder on the desktop and called it 'recover'

So navigate to the folder you just created:

```
cd Desktop/recover
```Then run testdisk:

To run testdisk type in the terminal:

```
sudo testdisk
```You will be met with this screen:

```
TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


TestDisk is a free data recovery software designed to help recover lost
partitions and/or make non-booting disks bootable again when these symptoms
are caused by faulty software, certain types of viruses or human error.
It can also be used to repair some filesystem errors.

Information gathered during TestDisk use can be recorded for later
review. If you choose to create the text file, testdisk.log , it
will contain TestDisk options, technical information and various
outputs; including any folder/file names TestDisk was used to find and
list onscreen.

Use arrow keys to select, then press Enter key:
[ Create ]  Create a new log file
[ Append ]  Append information to log file
[ No Log ]  Don't record anything
```Click on 'Create' and it should put a log file in the 'recover' folder on the Desktop.

The next screen will show your hard drive and any other removerable drives, such as flash or external hard drives

You will want to select the drive you are trying to mend/recover and click 'proceed'

You will then be taken to this screen:

```
TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 500 GB / 465 GiB - ATA ST3500418AS

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.
```You will want to select the '[Intel ] Intel/PC partition' Tab


The rest of the process will depend on your particular situation. Reading through what I did may help, or you can visit this page:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Save_the_partition_table_or_search_for_more_partitions.3F](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Save_the_partition_table_or_search_for_more_partitions.3F)
 
for better instructions.

---

### Post by kansasnoob on 2010-05-21
I'm glad you got this sorted. My DSL flaked out on me following a thunderstorm and it's still acting up off and on.

I actually thought you might have to resort to PhotoRec, but you did great!

---

