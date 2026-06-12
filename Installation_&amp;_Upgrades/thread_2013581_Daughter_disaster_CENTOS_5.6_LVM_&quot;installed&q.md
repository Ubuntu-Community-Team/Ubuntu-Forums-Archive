---
title: "Daughter disaster: CENTOS 5.6 LVM &quot;installed&quot; over Ubuntu 10.10"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by foggys916 on 2012-07-01
Well,

This morning I learn that my daughter has placed disc one of this set into the PC and installed a logical drive over the entire 250GB ATA drive on an HP Pavilion desktop.

Is all hope gone in potentially undoing this or retrieving photos, videos, documents etc etc.?

Using an old version of Puppy Linux and this reports as per the pic, /boot and LVM.

Steve, in a very tense household!

---

### Post by darkod on 2012-07-01
First, stop booting the computer from the hdd. Only live mode from CDs.

Get an ubuntu cd, boot into live mode, download and run testdisk and scan the hdd with the deep search. Full instructions here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I recommend first to scan it and post the screenshot of the scan result unless you know exactly what you are doing.

After we see the scan result we can advise you how to proceed.

Usually testdisk should be able to bring back older partitions, deleted or formatted. But lets see.

---

### Post by foggys916 on 2012-07-01
Thanks for the speedy reply.

Downloading 12.04 LTS as I type, will be back later.

Cheers

Steve

---

### Post by foggys916 on 2012-07-01
Hi Darko

Results of testdisk in the image and here;

[COLOR=Red]TestDisk 6.14-WIP, Data Recovery Utility, May 2012
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
>* Linux                    0   1  1    12 254 63     208782 [/boot]
 D Linux LVM               13   0  1 30400 254 63  488183220
 D Linux                 2107  38 44  6730 106 32   74272768
 D Linux                 2108  11 16  6731  79  4   74272768
 D Linux                 2109 211 23  6733  24 11   74272768
 D FAT12                 2725 112 12  2725 177 12    4096 [BOOTTEST]
 D Linux                 4623 100 22  6170   1 39   24846336
 D Linux Swap            6024  10  3  6803 248 37   12529664
 D Linux                 6170  34  9 12857 247 62  107440128
 D HPFS - NTFS           7039  15  1 29751 254 63  364883400
 D Linux                 9320 185 18 16008 144  8  107440128
 D Linux                 9322  32 55 16009 246 45  107440128
 D Linux Swap           12858  25 32 13665  15 46   12963840
 D Linux                13665  48 16 30401  75 10  268865536 [DATA]
 D Linux Swap           29625  46 54 30401  75 10   12468224
 D Linux Swap           29636 135  4 30401  75 10   12285952

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/COLOR]

Prior to Ubuntu, this PC had Vista installed (which is not now needed).

the partiton marked [DATA] does seem to list a folder (and its contents) that I made in the root directory whih does have a lot of the required data, but stuff that was in home directories is still wanted.

Helpful?

Cheers

Steve

---

### Post by darkod on 2012-07-01
Do you know more or less what was the layout at that time?

From what I can see, my assumption is:
Linux partition, start at 4623 cylinder, end at 6170, size 24846336 sectors (size 12132MB)
Linux partition, start 6170, end 12857, size 107440128 (52461MB)
Linux swap, start 12858, end 13665, size 12963840 (6330MB)
Linux, start 13665, end 30401, [DATA], size 268865536 (131282MB)

That is my guess judging by the start/end cylinders. Whether this is correct, and whether the data on all those partitions can be recovered is another matter.

If those partitions look like the ones you expect to have (you had), I suggest first to try whether you can list the files with P on each of them one by one. I guess you know how to do that since you already looked into [DATA].

If all of them list the data you expect, and if those are all the linux partitions you expect, you can try changing the D in front of each partition into P for primary or L for logical. It doesn't really matter, as long as you don't try to make more than 4 partitions primary. I would say the first primary and the other logical.
Then you can press Enter in testdisk to continue and it will list only these 4 partitions in the next screen. With write you can write a new table. But do this only if that's what you want!!!

If you want more advice, I can suggest first only trying to list the files on all those partitions (except the swap), and then post here what you find out. After that we can discuss changing the D into P/L and writing the table. I outlined the basics above.

---

### Post by foggys916 on 2012-07-02
Darko

I think I made the partition with [DATA] a separate partition (not sure about the rest), but apart from this partition, the residual NTFS partition and the new Linux boot partition (as a result of the 'mistake' CENTOS install), these are the only ones that list the files when 'P' is pressed. The others give a warning that the contents cannot be displayed. Unfortunately the program takes around an hour to run and I forgot to take a screen dump of the listed files in [DATA] and the exact text on the report that greets me where it cannot list the files.

Can I change the D to P for the [DATA] partition (the files listed seem OK) at a minimum? One assumes that the other stuff is unrecoverable (with testdisk) is it reports that the contents might be corrupted? ](*,)

Many thanks for the on going help.

Steve

---

### Post by foggys916 on 2012-07-02
...oh and I think I made /home a separate partition but I can't remember the size, and obviously (presently?!?!) I can't list files that might be in the old /home partition.

---

### Post by darkod on 2012-07-02
Yes, you can make only [DATA] into P but I am worried that testdisk says to write the changes only after you are happy with the "new" list. So, not sure if that means you can forget about getting data back from the other partitions.

Also, I am wondering if we should take listing of the files (or not listing) for granted. Not sure if that means there will be no files after you recover some of the other Linux partitions.

I have to leave the decision to you. If nothing, recovering only [DATA] doesn't hurt recovering the others too. If there are no files on them, tough luck.

So, you can make all three Linux partition I mentioned (forget about Swap, you don't need it) into P, and write the table. Then boot again in live mode and see what you can read on the hdd partitions.

---

### Post by foggys916 on 2012-07-03
Many thanks, I'll give it a go in a day or so.

If I get lost I might be back on a new thread.

Bye for now......

---

### Post by foggys916 on 2012-07-31
[COLOR=black][FONT=Tahoma][COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]Well not sure if much else is recoverable, but.....[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]I have managed to recover the homes folder that was on a separate partition, and a partition which had some old data (/DATA)..[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]I have uploaded the full testdisk output (names of home folders removed), and pictures of the reports from the partition tool in Ubuntu (when I run a Live version of the platform).[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]I suppose the main question is that there is what appears to be two partitions, one with a capacity of 47.17 GB and the other with 6.18 GB capacity. One is the original root partition, but I can't remember which. I think the 6.18 GB held the standard load and the 47.17 GB was a /opt parition that would hold extra installs and other non OS files (downloads etc etc). The /boot partition has the CENTOS boot info, which won't be needed.[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]Looking at the testdisk report and images what do people think about the 47.17 and 6.18 GB “slots”, are they recoverable?[/FONT][/COLOR][/FONT][/COLOR]
 
 
[COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]Any extra help is most gratefully received.[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][COLOR=navy][FONT=Verdana]Best to all[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][FONT=Verdana][COLOR=navy]ST[/COLOR][/FONT][/FONT][/COLOR]
 
[IMG]http://www.premier.talktalk.net/ubuntuforums/1.png[/IMG]
 
[IMG]http://www.premier.talktalk.net/ubuntuforums/2.png[/IMG]
 
[IMG]http://www.premier.talktalk.net/ubuntuforums/3.png[/IMG]
 
[IMG]http://www.premier.talktalk.net/ubuntuforums/4.png[/IMG]
 
 
FULL TESTDISK LOG
 
 
[FONT=Courier New]Mon Jul 9 18:35:47 2012[/FONT]
[FONT=Courier New]Command line: TestDisk[/FONT]
[FONT=Courier New]TestDisk 6.14-WIP, Data Recovery Utility, May 2012[/FONT]
[FONT=Courier New]Christophe GRENIER <[/FONT][EMAIL="grenier@cgsecurity.org"][FONT=Courier New]grenier@cgsecurity.org[/FONT][/EMAIL][FONT=Courier New]>[/FONT]
[[FONT=Courier New]http://www.cgsecurity.org[/FONT]]("http://www.cgsecurity.org")
[FONT=Courier New]OS: Linux, kernel 3.0.0-12-generic (#20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011) i686[/FONT]
[FONT=Courier New]Compiler: GCC 4.4[/FONT]
[FONT=Courier New]Compilation date: 2012-07-05T08:10:14[/FONT]
[FONT=Courier New]ext2fs lib: 1.41.12, ntfs lib: libntfs-3g, reiserfs lib: 0.3.1-rc8, ewf lib: 20100226[/FONT]
[FONT=Courier New]/dev/sda: LBA, LBA48, DCO support[/FONT]
[FONT=Courier New]/dev/sda: size 488397168 sectors[/FONT]
[FONT=Courier New]/dev/sda: user_max 488397168 sectors[/FONT]
[FONT=Courier New]/dev/sda: dco 488397168 sectors[/FONT]
[FONT=Courier New]Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512[/FONT]
[FONT=Courier New]/dev/sr0 is not an ATA disk[/FONT]
[FONT=Courier New]Hard disk list[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - SAMSUNG SP2504C, S/N:S09QJ1HLC42543, FW:VT100-49[/FONT]
[FONT=Courier New]Disk /dev/sdc - 8028 KB / 7840 KiB - CHS 245 2 32, sector size=512 - Generic USB CF Reader, FW:1.01[/FONT]
[FONT=Courier New]Disk /dev/sr0 - 729 MB / 695 MiB - CHS 355992 1 1 (RO), sector size=2048 - ATAPI DVD A DH16AYH, FW:YH13[/FONT]
[FONT=Courier New]Partition table type (auto): Intel[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - SAMSUNG SP2504C[/FONT]
[FONT=Courier New]Partition table type: Intel[/FONT]
[FONT=Courier New]Analyse Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]Geometry from i386 MBR: head=255 sector=63[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=2[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=2[/FONT]
[FONT=Courier New]Current partition structure:[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]2 E extended LBA 6170 1 40 30401 75 10 389275648[/FONT]
[FONT=Courier New]5 L Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]X extended 13665 47 1 30401 75 10 268865614[/FONT]
[FONT=Courier New]6 L Linux 13665 48 16 30401 75 10 268865536 [DATA][/FONT]
[FONT=Courier New]search_part()[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/12, s_mnt_count=10/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=1024[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 104388[/FONT]
[FONT=Courier New]recover_EXT2: part_size 208776[/FONT]
[FONT=Courier New]Linux 0 1 1 12 254 57 208776 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]LVM2 magic value at 13/0/1[/FONT]
[FONT=Courier New]part_size 488183220[/FONT]
[FONT=Courier New]Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]Results[/FONT]
[FONT=Courier New]* Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]P Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]interface_write()[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]2 P Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]search_part()[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/12, s_mnt_count=10/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=1024[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 104388[/FONT]
[FONT=Courier New]recover_EXT2: part_size 208776[/FONT]
[FONT=Courier New]Linux 0 1 1 12 254 57 208776 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]block_group_nr 3[/FONT]
[FONT=Courier New]recover_EXT2: "e2fsck -b 24577 -B 1024 device" may be needed[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=3/12, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=1024[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 104388[/FONT]
[FONT=Courier New]recover_EXT2: part_size 208776[/FONT]
[FONT=Courier New]Linux 0 1 1 12 254 57 208776 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock Backup superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]LVM2 magic value at 13/0/1[/FONT]
[FONT=Courier New]part_size 488183220[/FONT]
[FONT=Courier New]Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]BAD_RS LBA=1968055299 3122256[/FONT]
[FONT=Courier New]check_FAT: can't read FAT boot sector[/FONT]
[FONT=Courier New]check_part_i386 failed for partition type 04[/FONT]
[FONT=Courier New]FAT16 <32M 122505 198 1 295059 218 13 2772081283[/FONT]
[FONT=Courier New]This partition ends after the disk limits. (start=1968055299, size=2772081283, end=445169285, disk end=488397168)[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/283, s_mnt_count=1/30, s_blocks_per_group=32768, s_inodes_per_group=8176[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 9284096[/FONT]
[FONT=Courier New]recover_EXT2: part_size 74272768[/FONT]
[FONT=Courier New]Linux 2107 38 44 6730 106 32 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/283, s_mnt_count=29/30, s_blocks_per_group=32768, s_inodes_per_group=8176[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 9284096[/FONT]
[FONT=Courier New]recover_EXT2: part_size 74272768[/FONT]
[FONT=Courier New]Linux 2108 11 16 6731 79 4 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/283, s_mnt_count=29/30, s_blocks_per_group=32768, s_inodes_per_group=8176[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 9284096[/FONT]
[FONT=Courier New]recover_EXT2: part_size 74272768[/FONT]
[FONT=Courier New]Linux 2109 211 23 6733 24 11 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]check_FAT: Unusual media descriptor (0xf0!=0xf8)[/FONT]
[FONT=Courier New]FAT12 at 2725/112/12[/FONT]
[FONT=Courier New]FAT1 : 1-9[/FONT]
[FONT=Courier New]FAT2 : 10-18[/FONT]
[FONT=Courier New]start_rootdir : 19[/FONT]
[FONT=Courier New]Data : 33-2879[/FONT]
[FONT=Courier New]sectors : 2880[/FONT]
[FONT=Courier New]cluster_size : 1[/FONT]
[FONT=Courier New]no_of_cluster : 2847 (2 - 2848)[/FONT]
[FONT=Courier New]fat_length 9 calculated 9[/FONT]
[FONT=Courier New]heads/cylinder 2 (FAT) != 255 (HD)[/FONT]
[FONT=Courier New]sect/track 18 (FAT) != 63 (HD)[/FONT]
[FONT=Courier New]FAT12 at 2725/112/12[/FONT]
[FONT=Courier New]FAT12 2725 112 12 2725 157 56 2880 [BOOTTEST][/FONT]
[FONT=Courier New]FAT12, blocksize=512, 1474 KB / 1440 KiB[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/94, s_mnt_count=37/38, s_blocks_per_group=32768, s_inodes_per_group=8176[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 3105792[/FONT]
[FONT=Courier New]recover_EXT2: part_size 24846336[/FONT]
[FONT=Courier New]Linux 4623 100 22 6170 1 39 24846336[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 12 GB / 11 GiB[/FONT]
[FONT=Courier New]Linux Swap 6024 10 3 6803 248 21 12529648[/FONT]
[FONT=Courier New]SWAP2 version 1, 6415 MB / 6117 MiB[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/409, s_mnt_count=24/31, s_blocks_per_group=32768, s_inodes_per_group=8192[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 13430016[/FONT]
[FONT=Courier New]recover_EXT2: part_size 107440128[/FONT]
[FONT=Courier New]Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]BAD_RS LBA=2074729475 3122256[/FONT]
[FONT=Courier New]check_FAT: can't read FAT boot sector[/FONT]
[FONT=Courier New]check_part_i386 failed for partition type 04[/FONT]
[FONT=Courier New]FAT16 <32M 129145 238 57 301700 4 6 2772081283[/FONT]
[FONT=Courier New]This partition ends after the disk limits. (start=2074729475, size=2772081283, end=551843461, disk end=488397168)[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/409, s_mnt_count=20/31, s_blocks_per_group=32768, s_inodes_per_group=8192[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 13430016[/FONT]
[FONT=Courier New]recover_EXT2: part_size 107440128[/FONT]
[FONT=Courier New]Linux 9320 185 18 16008 144 8 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/409, s_mnt_count=20/31, s_blocks_per_group=32768, s_inodes_per_group=8192[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 13430016[/FONT]
[FONT=Courier New]recover_EXT2: part_size 107440128[/FONT]
[FONT=Courier New]Linux 9322 32 55 16009 246 45 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]Linux Swap 12858 25 32 13665 15 30 12963824[/FONT]
[FONT=Courier New]SWAP2 version 1, 6637 MB / 6329 MiB[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/1025, s_mnt_count=43/33, s_blocks_per_group=32768, s_inodes_per_group=8192[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=4096[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 33608192[/FONT]
[FONT=Courier New]recover_EXT2: part_size 268865536[/FONT]
[FONT=Courier New]Linux 13665 48 16 30401 75 10 268865536 [DATA][/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 137 GB / 128 GiB[/FONT]
[FONT=Courier New]Linux Swap 29625 46 54 30401 74 57 12468208[/FONT]
[FONT=Courier New]SWAP2 version 1, 6383 MB / 6087 MiB[/FONT]
[FONT=Courier New]Linux Swap 29636 135 4 30401 74 57 12285936[/FONT]
[FONT=Courier New]SWAP2 version 1, 6290 MB / 5998 MiB[/FONT]
[FONT=Courier New]NTFS at 29751/254/63[/FONT]
[FONT=Courier New]filesystem size 364883400[/FONT]
[FONT=Courier New]sectors_per_cluster 8[/FONT]
[FONT=Courier New]mft_lcn 786432[/FONT]
[FONT=Courier New]mftmirr_lcn 16[/FONT]
[FONT=Courier New]clusters_per_mft_record -10[/FONT]
[FONT=Courier New]clusters_per_index_record 1[/FONT]
[FONT=Courier New]HPFS - NTFS 7039 15 1 29751 254 63 364883400[/FONT]
[FONT=Courier New]NTFS found using backup sector, blocksize=4096, 186 GB / 173 GiB[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]Check the harddisk size: HD jumpers settings, BIOS detection...[/FONT]
[FONT=Courier New]The harddisk (250 GB / 232 GiB) seems too small! (< 2481 GB / 2311 GiB)[/FONT]
[FONT=Courier New]The following partitions can't be recovered:[/FONT]
[FONT=Courier New]FAT16 <32M 122505 198 1 295059 218 13 2772081283[/FONT]
[FONT=Courier New]FAT16 <32M 129145 238 57 301700 4 6 2772081283[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=3[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=2[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=2[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]Results[/FONT]
[FONT=Courier New]* Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]Linux 2107 38 44 6730 106 32 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]Linux 2108 11 16 6731 79 4 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]Linux 2109 211 23 6733 24 11 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]FAT12 2725 112 12 2725 177 12 4096 [BOOTTEST][/FONT]
[FONT=Courier New]FAT12, blocksize=512, 2097 KB / 2048 KiB[/FONT]
[FONT=Courier New]Linux 4623 100 22 6170 1 39 24846336[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 12 GB / 11 GiB[/FONT]
[FONT=Courier New]Linux Swap 6024 10 3 6803 248 37 12529664[/FONT]
[FONT=Courier New]SWAP2 version 1, 6415 MB / 6118 MiB[/FONT]
[FONT=Courier New]Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]HPFS - NTFS 7039 15 1 29751 254 63 364883400[/FONT]
[FONT=Courier New]NTFS found using backup sector, blocksize=4096, 186 GB / 173 GiB[/FONT]
[FONT=Courier New]Linux 9320 185 18 16008 144 8 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]Linux 9322 32 55 16009 246 45 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]Linux Swap 12858 25 32 13665 15 46 12963840[/FONT]
[FONT=Courier New]SWAP2 version 1, 6637 MB / 6330 MiB[/FONT]
[FONT=Courier New]Linux 13665 48 16 30401 75 10 268865536 [DATA][/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 137 GB / 128 GiB[/FONT]
[FONT=Courier New]Linux Swap 29625 46 54 30401 75 10 12468224[/FONT]
[FONT=Courier New]SWAP2 version 1, 6383 MB / 6088 MiB[/FONT]
[FONT=Courier New]Linux Swap 29636 135 4 30401 75 10 12285952[/FONT]
[FONT=Courier New]SWAP2 version 1, 6290 MB / 5999 MiB[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 9322 32 55 16009 246 45 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 9320 185 18 16008 144 8 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 2133571402.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 31-Jul-2011 08:41 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 31-Jul-2011 08:41 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 16384 2-May-2011 21:51 lost+found[/FONT]
[FONT=Courier New]2097153 drwxr-xr-x 1000 1000 4096 8-Jul-2012 17:56 [HOME FOLDER1 - NAME REMOVED][/FONT]
[FONT=Courier New]131073 drwxr-xr-x 1001 1001 4096 28-Jun-2012 17:21 [HOME FOLDER2 - NAME REMOVED][/FONT]
[FONT=Courier New]2883585 drwxr-xr-x 1002 1001 4096 30-Jun-2012 05:52 [HOME FOLDER3 - NAME REMOVED][/FONT]
[FONT=Courier New]786433 drwx------ 0 0 4096 31-Jul-2011 08:41 .Trash-0[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 4623 100 22 6170 1 39 24846336[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 12 GB / 11 GiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 16384 2-May-2011 21:51 lost+found[/FONT]
[FONT=Courier New]130817 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 Adobe[/FONT]
[FONT=Courier New]392449 drwxr-xr-x 0 0 4096 19-Jul-2011 08:43 Adobe AIR[/FONT]
[FONT=Courier New]X 523273 -rw-r--r-- 0 0 710 24-Jun-2012 07:34 BBC iPlayer Desktop.dpkg-new[/FONT]
[FONT=Courier New]X 523273 -rw-r--r-- 0 0 710 24-Jun-2012 07:34 BBC iPlayer Desktop[/FONT]
[FONT=Courier New]523271 drwxr-xr-x 0 0 4096 30-May-2011 11:35 google[/FONT]
 
[FONT=Courier New]dir_partition inode=0[/FONT]
[FONT=Courier New]FAT12 2725 112 12 2725 177 12 4096 [BOOTTEST][/FONT]
[FONT=Courier New]FAT12, blocksize=512, 2097 KB / 2048 KiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 -r-xr-xr-x 0 0 24810 7-Jan-1999 07:03 IBMBIO.COM[/FONT]
[FONT=Courier New]51 -r-xr-xr-x 0 0 30880 7-Jan-1999 07:03 IBMDOS.COM[/FONT]
[FONT=Courier New]112 -rwxr-xr-x 0 0 66785 7-Jan-1999 07:03 COMMAND.COM[/FONT]
[FONT=Courier New]245 drwxr-xr-x 0 0 0 24-Oct-2001 11:15 DRDOS[/FONT]
[FONT=Courier New]2844 drwxr-xr-x 0 0 0 30-Oct-2001 19:30 OAK[/FONT]
[FONT=Courier New]1379 drwxr-xr-x 0 0 0 24-Jun-2003 13:16 NR[/FONT]
[FONT=Courier New]1419 -rwxr-xr-x 0 0 267650 10-Oct-2002 13:08 WWBMU.EXE[/FONT]
[FONT=Courier New]389 -rwxr-xr-x 0 0 2888 24-Feb-2004 09:03 README.TXT[/FONT]
[FONT=Courier New]386 -rwxr-xr-x 0 0 1920 6-Jul-2005 13:26 DCONFIG.SYS[/FONT]
[FONT=Courier New]388 -rwxr-xr-x 0 0 582 6-Jul-2005 13:27 AUTODOS7.BAT[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2109 211 23 6733 24 11 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2108 11 16 6731 79 4 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 2133571387.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2107 38 44 6730 106 32 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]* Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 1024 1-Jul-2012 07:21 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 1024 1-Jul-2012 07:21 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 12288 1-Jul-2012 07:14 lost+found[/FONT]
[FONT=Courier New]2009 drwxr-xr-x 0 0 1024 1-Jul-2012 07:26 grub[/FONT]
[FONT=Courier New]X 12 -rw-r--r-- 0 0 80032 12-Mar-2009 19:06 message;4feff966[/FONT]
[FONT=Courier New]12 -rw-r--r-- 0 0 80032 12-Mar-2009 19:06 message[/FONT]
[FONT=Courier New]18 -rw------- 0 0 3376097 ntfs_mst_post_read_fixup_warn: magic: 0x8301671d size: 1024 usa_ofs: 605 usa_count: 12562: Invalid argument[/FONT]
[FONT=Courier New]Record 0 has no FILE magic (0x8301671d)[/FONT]
[FONT=Courier New]Failed to load $MFT: Input/output error[/FONT]
[FONT=Courier New]ntfs_mst_post_read_fixup_warn: magic: 0x8301671d size: 1024 usa_ofs: 605 usa_count: 12562: Invalid argument[/FONT]
[FONT=Courier New]Record 0 has no FILE magic (0x8301671d)[/FONT]
[FONT=Courier New]Failed to load $MFT: Input/output error[/FONT]
[FONT=Courier New]ntfs_mst_post_read_fixup_warn: magic: 0x8301671d size: 1024 usa_ofs: 605 usa_count: 12562: Invalid argument[/FONT]
[FONT=Courier New]Record 0 has no FILE magic (0x8301671d)[/FONT]
[FONT=Courier New]Failed to load $MFT: Input/output error[/FONT]
[FONT=Courier New]ntfs_mst_post_read_fixup_warn: magic: 0x8301671d size: 1024 usa_ofs: 605 usa_count: 12562: Invalid argument[/FONT]
[FONT=Courier New]Record 0 has no FILE magic (0x8301671d)[/FONT]
[FONT=Courier New]Failed to load $MFT: Input/output error[/FONT]
[FONT=Courier New]1-Jul-2012 07:21 initrd-2.6.18-238.el5.img[/FONT]
[FONT=Courier New]13 -rw-r--r-- 0 0 158 13-Jan-2011 21:59 .vmlinuz-2.6.18-238.el5.hmac[/FONT]
[FONT=Courier New]14 -rw-r--r-- 0 0 979708 13-Jan-2011 21:59 System.map-2.6.18-238.el5[/FONT]
[FONT=Courier New]15 -rw-r--r-- 0 0 69815 13-Jan-2011 21:59 config-2.6.18-238.el5[/FONT]
[FONT=Courier New]16 -rw-r--r-- 0 0 112421 13-Jan-2011 22:00 symvers-2.6.18-238.el5.gz[/FONT]
[FONT=Courier New]17 -rw-r--r-- 0 0 1888052 13-Jan-2011 21:59 vmlinuz-2.6.18-238.el5[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2107 38 44 6730 106 32 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 9322 32 55 16009 246 45 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]ntfs_device_testdisk_io_ioctl() unimplemented[/FONT]
[FONT=Courier New]ntfs_device_testdisk_io_ioctl() unimplemented[/FONT]
[FONT=Courier New]Not an exFAT boot sector.[/FONT]
[FONT=Courier New]ntfs_device_testdisk_io_ioctl() unimplemented[/FONT]
[FONT=Courier New]ntfs_device_testdisk_io_ioctl() unimplemented[/FONT]
[FONT=Courier New]HPFS - NTFS 7039 15 1 29751 254 63 364883400[/FONT]
[FONT=Courier New]NTFS found using backup sector, blocksize=4096, 186 GB / 173 GiB[/FONT]
[FONT=Courier New]Can't open filesystem. Filesystem seems damaged.[/FONT]
 
[FONT=Courier New]dir_partition inode=0[/FONT]
[FONT=Courier New]FAT12 2725 112 12 2725 177 12 4096 [BOOTTEST][/FONT]
[FONT=Courier New]FAT12, blocksize=512, 2097 KB / 2048 KiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 -r-xr-xr-x 0 0 24810 7-Jan-1999 07:03 IBMBIO.COM[/FONT]
[FONT=Courier New]51 -r-xr-xr-x 0 0 30880 7-Jan-1999 07:03 IBMDOS.COM[/FONT]
[FONT=Courier New]112 -rwxr-xr-x 0 0 66785 7-Jan-1999 07:03 COMMAND.COM[/FONT]
[FONT=Courier New]245 drwxr-xr-x 0 0 0 24-Oct-2001 11:15 DRDOS[/FONT]
[FONT=Courier New]2844 drwxr-xr-x 0 0 0 30-Oct-2001 19:30 OAK[/FONT]
[FONT=Courier New]1379 drwxr-xr-x 0 0 0 24-Jun-2003 13:16 NR[/FONT]
[FONT=Courier New]1419 -rwxr-xr-x 0 0 267650 10-Oct-2002 13:08 WWBMU.EXE[/FONT]
[FONT=Courier New]389 -rwxr-xr-x 0 0 2888 24-Feb-2004 09:03 README.TXT[/FONT]
[FONT=Courier New]386 -rwxr-xr-x 0 0 1920 6-Jul-2005 13:26 DCONFIG.SYS[/FONT]
[FONT=Courier New]388 -rwxr-xr-x 0 0 582 6-Jul-2005 13:27 AUTODOS7.BAT[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2109 211 23 6733 24 11 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2108 11 16 6731 79 4 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 2133571387.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 2107 38 44 6730 106 32 74272768[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 38 GB / 35 GiB[/FONT]
[FONT=Courier New]ext2fs_dir_iterate failed with error 1.[/FONT]
[FONT=Courier New]Directory /[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]Linux 4623 100 22 6170 1 39 24846336[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 12 GB / 11 GiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 16384 2-May-2011 21:51 lost+found[/FONT]
[FONT=Courier New]130817 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 Adobe[/FONT]
[FONT=Courier New]392449 drwxr-xr-x 0 0 4096 19-Jul-2011 08:43 Adobe AIR[/FONT]
[FONT=Courier New]X 523273 -rw-r--r-- 0 0 710 24-Jun-2012 07:34 BBC iPlayer Desktop.dpkg-new[/FONT]
[FONT=Courier New]X 523273 -rw-r--r-- 0 0 710 24-Jun-2012 07:34 BBC iPlayer Desktop[/FONT]
[FONT=Courier New]523271 drwxr-xr-x 0 0 4096 30-May-2011 11:35 google[/FONT]
[FONT=Courier New]dir_partition inode=523271[/FONT]
[FONT=Courier New]Linux 4623 100 22 6170 1 39 24846336[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock, 12 GB / 11 GiB[/FONT]
[FONT=Courier New]Directory /google[/FONT]
[FONT=Courier New]523271 drwxr-xr-x 0 0 4096 30-May-2011 11:35 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 ..[/FONT]
[FONT=Courier New]X 523272 drwxr-xr-x 0 0 4096 28-Jun-2012 05:30 chrome.dpkg-new[/FONT]
[FONT=Courier New]523272 drwxr-xr-x 0 0 4096 28-Jun-2012 05:30 chrome[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 16384 2-May-2011 21:51 lost+found[/FONT]
[FONT=Courier New]130817 drwxr-xr-x 0 0 4096 10-Sep-2011 22:38 Adobe[/FONT]
[FONT=Courier New]392449 drwxr-xr-x 0 0 4096 19-Jul-2011 08:43 Adobe AIR[/FONT]
[FONT=Courier New]X 523273 -rw-r--r-- 0 0 710 24-Jun-2012 07:34 BBC iPlayer Desktop.dpkg-new[/FONT]
[FONT=Courier New]X 523273 -rw-r--r-- 0 0 710 24-Jun-2012 07:34 BBC iPlayer Desktop[/FONT]
[FONT=Courier New]523271 drwxr-xr-x 0 0 4096 30-May-2011 11:35 google[/FONT]
[FONT=Courier New]interface_write()[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]simulate write![/FONT]
[FONT=Courier New]write_mbr_i386: starting...[/FONT]
[FONT=Courier New]write_all_log_i386: starting...[/FONT]
[FONT=Courier New]No extended partition[/FONT]
[FONT=Courier New]Interface Advanced[/FONT]
[FONT=Courier New]Geometry from i386 MBR: head=255 sector=63[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=2[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=2[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]2 E extended LBA 6170 1 40 30401 75 10 389275648[/FONT]
[FONT=Courier New]5 L Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]X extended 13665 47 1 30401 75 10 268865614[/FONT]
[FONT=Courier New]6 L Linux 13665 48 16 30401 75 10 268865536 [DATA][/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 137 GB / 128 GiB[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]5 L Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]ext4 blocksize=4096 Large file Sparse superblock Recover, 55 GB / 51 GiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 31-Jul-2011 08:41 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 4096 31-Jul-2011 08:41 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 16384 2-May-2011 21:51 lost+found[/FONT]
[FONT=Courier New]2097153 drwxr-xr-x 1000 1000 4096 8-Jul-2012 17:56 [HOME FOLDER1 - NAME REMOVED][/FONT]
[FONT=Courier New]131073 drwxr-xr-x 1001 1001 4096 28-Jun-2012 17:21 [HOME FOLDER2 - NAME REMOVED][/FONT]
[FONT=Courier New]2883585 drwxr-xr-x 1002 1001 4096 30-Jun-2012 05:52 [HOME FOLDER3 - NAME REMOVED][/FONT]
[FONT=Courier New]786433 drwx------ 0 0 4096 31-Jul-2011 08:41 .Trash-0[/FONT]
 
[FONT=Courier New]dir_partition inode=2[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]Directory /[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 1024 1-Jul-2012 07:21 .[/FONT]
[FONT=Courier New]2 drwxr-xr-x 0 0 1024 1-Jul-2012 07:21 ..[/FONT]
[FONT=Courier New]11 drwx------ 0 0 12288 1-Jul-2012 07:14 lost+found[/FONT]
[FONT=Courier New]2009 drwxr-xr-x 0 0 1024 1-Jul-2012 07:26 grub[/FONT]
[FONT=Courier New]X 12 -rw-r--r-- 0 0 80032 12-Mar-2009 19:06 message;4feff966[/FONT]
[FONT=Courier New]12 -rw-r--r-- 0 0 80032 12-Mar-2009 19:06 message[/FONT]
[FONT=Courier New]18 -rw------- 0 0 3376097 1-Jul-2012 07:21 initrd-2.6.18-238.el5.img[/FONT]
[FONT=Courier New]13 -rw-r--r-- 0 0 158 13-Jan-2011 21:59 .vmlinuz-2.6.18-238.el5.hmac[/FONT]
[FONT=Courier New]14 -rw-r--r-- 0 0 979708 13-Jan-2011 21:59 System.map-2.6.18-238.el5[/FONT]
[FONT=Courier New]15 -rw-r--r-- 0 0 69815 13-Jan-2011 21:59 config-2.6.18-238.el5[/FONT]
[FONT=Courier New]16 -rw-r--r-- 0 0 112421 13-Jan-2011 22:00 symvers-2.6.18-238.el5.gz[/FONT]
[FONT=Courier New]17 -rw-r--r-- 0 0 1888052 13-Jan-2011 21:59 vmlinuz-2.6.18-238.el5[/FONT]
[FONT=Courier New]New options :[/FONT]
[FONT=Courier New]Dump : No[/FONT]
[FONT=Courier New]Align partition: Yes[/FONT]
[FONT=Courier New]Expert mode : No[/FONT]
[FONT=Courier New]Analyse Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]Geometry from i386 MBR: head=255 sector=63[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=2[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=2[/FONT]
[FONT=Courier New]Current partition structure:[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]2 E extended LBA 6170 1 40 30401 75 10 389275648[/FONT]
[FONT=Courier New]5 L Linux 6170 34 9 12857 247 62 107440128[/FONT]
[FONT=Courier New]X extended 13665 47 1 30401 75 10 268865614[/FONT]
[FONT=Courier New]6 L Linux 13665 48 16 30401 75 10 268865536 [DATA][/FONT]
[FONT=Courier New]Backup partition structure[/FONT]
[FONT=Courier New]partition_save[/FONT]
[FONT=Courier New]search_part()[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/12, s_mnt_count=10/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=1024[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 104388[/FONT]
[FONT=Courier New]recover_EXT2: part_size 208776[/FONT]
[FONT=Courier New]Linux 0 1 1 12 254 57 208776 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]LVM2 magic value at 13/0/1[/FONT]
[FONT=Courier New]part_size 488183220[/FONT]
[FONT=Courier New]Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]Results[/FONT]
[FONT=Courier New]* Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]P Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]interface_write()[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]2 P Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]search_part()[/FONT]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=0/12, s_mnt_count=10/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=1024[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 104388[/FONT]
[FONT=Courier New]recover_EXT2: part_size 208776[/FONT]
[FONT=Courier New]Linux 0 1 1 12 254 57 208776 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]block_group_nr 3[/FONT]
[FONT=Courier New]recover_EXT2: "e2fsck -b 24577 -B 1024 device" may be needed[/FONT]
[FONT=Courier New]recover_EXT2: s_block_group_nr=3/12, s_mnt_count=0/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2008[/FONT]
[FONT=Courier New]recover_EXT2: s_blocksize=1024[/FONT]
[FONT=Courier New]recover_EXT2: s_blocks_count 104388[/FONT]
[FONT=Courier New]recover_EXT2: part_size 208776[/FONT]
[FONT=Courier New]Linux 0 1 1 12 254 57 208776 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock Backup superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]LVM2 magic value at 13/0/1[/FONT]
[FONT=Courier New]part_size 488183220[/FONT]
[FONT=Courier New]Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]Search for partition aborted[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=8 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=16 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=32 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=64 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=128 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=240 nbr=1[/FONT]
[FONT=Courier New]get_geometry_from_list_part_aux head=255 nbr=4[/FONT]
[FONT=Courier New]Results[/FONT]
[FONT=Courier New]* Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]ext3 blocksize=1024 Sparse superblock, 106 MB / 101 MiB[/FONT]
[FONT=Courier New]P Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]LVM2, 249 GB / 232 GiB[/FONT]
[FONT=Courier New]interface_write()[/FONT]
[FONT=Courier New]1 * Linux 0 1 1 12 254 63 208782 [/boot][/FONT]
[FONT=Courier New]2 P Linux LVM 13 0 1 30400 254 63 488183220[/FONT]
[FONT=Courier New]simulate write![/FONT]
[FONT=Courier New]write_mbr_i386: starting...[/FONT]
[FONT=Courier New]write_all_log_i386: starting...[/FONT]
[FONT=Courier New]No extended partition[/FONT]
[FONT=Courier New]TestDisk exited normally.[/FONT][/FONT][/COLOR]

---

