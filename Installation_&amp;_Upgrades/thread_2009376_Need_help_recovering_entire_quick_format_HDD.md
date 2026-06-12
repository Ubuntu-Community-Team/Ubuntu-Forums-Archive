---
title: "Need help recovering entire quick format HDD"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by Jakin on 2012-06-24
Hello, i have run into some issues this morning, and for the past well------- 6hours i have been trying to recover my quick formatted HDD; How? Well i was trying to resize my ubuntu partition to fill the extra 20gb i had sitting unallocated on my "500 GB" harddrive (real size when i bought it and found out is 462 GB :P) The very instant that i realised it formated the entire drive rather than the 20gb i had unallocated on the drive, i hit the power button. 
I cannot access any of the partitions, so i am on LiveCD of ubuntu, and have searched around, tried TestDisk, and here are my results:

-------------------------------------------------------

Sun Jun 24 15:54:43 2012
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.38-8-generic (#42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011)
Compiler: GCC 4.5 - Oct 17 2010 19:13:58
ext2fs lib: 1.41.14, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: native_max 976773168 sectors
/dev/sda: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA ST95005620AS
Disk /dev/sr0 - 732 MB / 698 MiB - CHS 357479 1 1 (RO), sector size=2048 - hp DVDRAM GT30L

Partition table type (auto): Intel
Disk /dev/sda - 500 GB / 465 GiB - ATA ST95005620AS
Partition table type: Intel

Interface Advanced

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
No partition is bootable
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
NTFS at 51/0/1
filesystem size           861375845
sectors_per_cluster       8
mft_lcn                   618618
mftmirr_lcn               8434343
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             51   0  1 53669  42 29  861375845
     NTFS, 441 GB / 410 GiB
NTFS at 56280/0/1
filesystem size           33482128
sectors_per_cluster       8
mft_lcn                   769743
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]
     NTFS, 17 GB / 15 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=10/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58364  61  2 60801  47 46   39149568
     EXT4 Large file Sparse superblock, 20 GB / 18 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * HPFS - NTFS             51   0  1 53669  42 29  861375845
     NTFS, 441 GB / 410 GiB
   P HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]
     NTFS, 17 GB / 15 GiB
   P Linux                58364  61  2 60801  47 46   39149568
     EXT4 Large file Sparse superblock, 20 GB / 18 GiB

interface_write()
 1 * HPFS - NTFS             51   0  1 53669  42 29  861375845
 2 P HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]
 3 P Linux                58364  61  2 60801  47 46   39149568

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
NTFS at 50/254/63
filesystem size           819249
sectors_per_cluster       8
mft_lcn                   7288
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  4    50 254 63     819249
     NTFS found using backup sector!, 419 MB / 400 MiB
NTFS at 51/0/1
filesystem size           861375845
sectors_per_cluster       8
mft_lcn                   618618
mftmirr_lcn               8434343
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             51   0  1 53669  42 29  861375845
     NTFS, 441 GB / 410 GiB
NTFS at 56279/254/63
filesystem size           903318881
sectors_per_cluster       8
mft_lcn                   618618
mftmirr_lcn               8434343
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             51   0  5 56279 254 63  903318881
     NTFS found using backup sector!, 462 GB / 430 GiB
NTFS at 56280/0/1
filesystem size           33482128
sectors_per_cluster       8
mft_lcn                   769743
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]
     NTFS, 17 GB / 15 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=10/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58364  61  2 60801  47 46   39149568
     EXT4 Large file Sparse superblock, 20 GB / 18 GiB

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=10/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58642 135 54 61079 122 35   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
This partition ends after the disk limits. (start=942092288, size=39149568, end=981241855, disk end=976784130)

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=10/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58643 108 26 61080  95  7   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
This partition ends after the disk limits. (start=942106624, size=39149568, end=981256191, disk end=976784130)

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=10/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58648   0  1 61084 241 45   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
This partition ends after the disk limits. (start=942180120, size=39149568, end=981329687, disk end=976784130)

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=10/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58652  88 61 61089  75 42   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
This partition ends after the disk limits. (start=942249984, size=39149568, end=981399551, disk end=976784130)

recover_EXT2: s_block_group_nr=0/149, s_mnt_count=7/27, s_blocks_per_group=32768, s_inodes_per_group=8128
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 4893696
recover_EXT2: part_size 39149568
     Linux                58657  16 48 61094   3 29   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
This partition ends after the disk limits. (start=942325760, size=39149568, end=981475327, disk end=976784130)
check_FAT: Unusual media descriptor (0xf0!=0xf8)
FAT12 at 58805/18/30
FAT1 : 1-9
FAT2 : 10-18
start_rootdir : 19
Data : 33-2879
sectors : 2880
cluster_size : 1
no_of_cluster : 2847 (2 - 2848)
fat_length 9 calculated 9
heads/cylinder 2 (FAT) != 255 (HD)
sect/track 18 (FAT) != 63 (HD)

FAT12 at 58805/18/30
     FAT12                58805  18 30 58805  64 11       2880 [BOOTTEST]
     FAT12, 1474 KB / 1440 KiB
NTFS at 50/254/63
filesystem size           819249
sectors_per_cluster       8
mft_lcn                   7288
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 51/0/1
filesystem size           861375845
sectors_per_cluster       8
mft_lcn                   618618
mftmirr_lcn               8434343
clusters_per_mft_record   -10
clusters_per_index_record 1
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (500 GB / 465 GiB) seems too small! (< 502 GB / 468 GiB)
The following partitions can't be recovered:
     Linux                58642 135 54 61079 122 35   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
     Linux                58643 108 26 61080  95  7   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
     Linux                58648   0  1 61084 241 45   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
     Linux                58652  88 61 61089  75 42   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
     Linux                58657  16 48 61094   3 29   39149568
     EXT4 Large file Sparse superblock Recover, 20 GB / 18 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
     HPFS - NTFS              0   1  4    50 254 63     819249
     NTFS found using backup sector!, 419 MB / 400 MiB
     HPFS - NTFS             50 254 63   101 253 59     819249
     NTFS, 419 MB / 400 MiB
     HPFS - NTFS             51   0  1 53669  42 29  861375845
     NTFS, 441 GB / 410 GiB
     HPFS - NTFS             51   0  5 56279 254 63  903318881
     NTFS found using backup sector!, 462 GB / 430 GiB
   * HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]
     NTFS, 17 GB / 15 GiB
     Linux                58364  61  2 60801  47 46   39149568
     EXT4 Large file Sparse superblock, 20 GB / 18 GiB
     FAT12                58805  18 30 58805  64 11       2880 [BOOTTEST]
     FAT12, 1474 KB / 1440 KiB

interface_write()
 1 * HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]

-----------------------------------------------------------------------

I really want to get it all back.... WORST case senario i start the entire HDD from scratch... can someone please help me? 
At the end of the log "interface_write()
 1 * HPFS - NTFS          56280   0  1 58364  42 22   33482128 [iDisk]" i knew this had to be wrong so i didnt do anything and exit terminal.

I have never done this, and really need help from someone that has experience recovering a whole HDD from quick format.. I wait...


If it helps, im on a Momentus XT 500GB drive..


[IMG]http://img140.imageshack.us/img140/8882/screenshot2ax.png[/IMG]

[IMG]http://img405.imageshack.us/img405/9818/screenshot4le.png[/IMG]
[IMG]http://img191.imageshack.us/img191/1450/screenshot5mj.png[/IMG]
Quick Search findings ^

(Deep Search findings in later post, due to forum limitations)

---

### Post by Jakin on 2012-06-26
Nothing? Is it possible to save the NTFS partitions at the very least?

---

### Post by darkod on 2012-06-26
The log is not easy to understand like this. You don't actually need logging.

Open Testdisk again, do the quick search and then the deep search and post the screenshot of what it finds with the deep search. You should have internet in live mode so you can post that screenshot.

Testdisk should be able to bring back the original partitions.

---

### Post by Jakin on 2012-06-27
Okay, i shall append the screenshots of each step and testdisk' findings along with the log in my first post. (apologies for the way i had to post these)

[IMG]http://img842.imageshack.us/img842/3920/screenshot6ss.png[/IMG]
[IMG]http://img846.imageshack.us/img846/8451/screenshot7z.png[/IMG]
[IMG]http://img862.imageshack.us/img862/7917/screenshot8h.png[/IMG]
[IMG]http://img824.imageshack.us/img824/7015/screenshot9jq.png[/IMG]  ^ This is the correct listing of my partitions as they were; although iDisk was not my boot partition, so im not sure why the star aside it.

[IMG]http://img812.imageshack.us/img812/7189/screenshot10mb.png[/IMG]

then it finally asks to write to iDisk (which is the name i had given the win7 64bit recovery partition) writting to this partition wouldn't help i would think, so i just exit console.

---

### Post by darkod on 2012-06-27
OK. Post the deep search because the quick search doesn't look like it can help (and usually it doesn't in cases like this, so this is not strange).

---

### Post by darkod on 2012-06-27
OK. In the screen before the last you can see that all partitions except one have the letter D in front of the row. In the instructions on the bottom of the page it says clearly, D stands for Deleted.

If you hit Enter without changing the D on any partition that's why it suggested to write a partition table with only iDisk. You are right, it wouldn't have helped.

When you have the deep search listing, you can also try to list files on any partition by selecting it with up/down arrows and hitting P. That can help you decide which partition has files that can be read, and which doesn't.

By looking at the start/end numbers on the deep search, I would say you need to recover partitions number 1, 4 and 5 on the list. You can use the P to see if you can read them first.

As for partition 4, I am not sure if it should be 3 or 4. They have similar size but not identical. Can you tell by the size?

Also, one of them should be the bootable, but I am not sure if it should be 1 or 4 (or 3 if you decide to restore that one instead of 4, you can't restore both).

But don't worry too much about the boot flag, you can manipulate it later. The most important right now is writing the correct partition table.

Do you need to restore the linux partition on the deep search list also? If you don't have any important data in linux, I suggest you leave it as deleted (D).

For the windows partitions you want to restore, you will need to select them one by one using the up/down arrows and then using the left/right arrows to change the letter into * (for Primary with boot flag) and on the rest into P (Primary).

If you want to, you can even make all three of them P without worrying about the boot flag right now. You can manipulate it from ubuntu live mode later.

After you are happy with the changed letters, hit Enter and in the next screen Write to write the table.

---

### Post by Jakin on 2012-06-27
Well im something like 90% sure that (if you can understand this) based how i saw the partitions when i copied from old HDD when i upgraded to this momentus XT HDD; (no longer have that drive either, that was a year ago)

partition 1 was the boot (with something like 200mb also im sure grub2 is installed there)
partition 2 was my main win7 (which had 441 GB with all my important data- to which you had asked about important data on linux itself- not really, [i used linux far more than win7 though, and when i need to save something important i mount win7 and save it there)

partition3 i believe is win7 recovery iDisk (which was like 18gb)
 and then there was like 20gb of unallocated HDD space.. (reading that i don't understand the numbers enough to tell which is which.. unfortunatly.. 

obviously remaining partition is ubuntu linux, which i could easily recreate if i needed to do so, so losing it... well  its not as important as saving my main win7 partition (bootable of course)

---

### Post by darkod on 2012-06-27
OK, we are getting there. But you have to compare and understand that testdisk shows more possibilities. So there are more than 3 partitions in the deep search list. This helps you recover lost partitions but also sometimes it can create confusion because it might show some very old partitions you deleted on purpose. :)

For example, the first two in the deep search list have identical size, but are not on identical location on the disk and taking into account your last post, partition #1 in that list should be your win7 boot partition.

As for your main win7 partition, it looks like #4 is the one, because it's size is 903318881 sectors, and each sector is 512B. So that would make it 441GB or 430GiB (taken into account the 1000 vs 1024 difference). Does that sound about right?

Also, the best test is to do the deep search again, highlight the 903318881 partition and hit P. Do you see your win7 folders/files listed?

If this assumption is correct, in the deep search list you will need to set the * on the partition #1, the P on partition #4 and again P on partition #5 (iDisk partition).

That would write the partition table with the small partition as bootable, and the other two partitions as primary ntfs partitions.

---

### Post by Jakin on 2012-06-27
Okay, i shall rerun testdisk, it takes like an hour, so i wouldnt expect you to wait up :D now that i have abit of help, and not so much in panic mode, im in no hurry for you to reply back :D

---

### Post by Jakin on 2012-06-27
[IMG]http://img267.imageshack.us/img267/3830/screenshotec.png[/IMG]

I believe this is how you said it appears it should be listed, and it does look right- however using " p " to check any of these, testdisk says "cannot open filesystem seems to be damaged"

---

### Post by darkod on 2012-06-27
Yes, that's what I had in mind according to the info you provided. However I don't like it that it can't list files.

On the other hand, often a simple chkdsk from windows can help.

But if windows is unbootable you would have to use it from a win7 rescue cd or similar. Maybe from safe mode if it can open the advanced menu with F8.

---

### Post by Jakin on 2012-06-27
Im pretty sure that F8 does open chkdsk. 
But really what it tells me, is append the partition map and hope for the best; afterall chkdsk cant fix what it thinks isnt there... this laptop came with the infernal "recovery partition" rather than disk (whenever they started doing that im not sure, but dont like it) however i do have a win7 x64 installer disc as well........ so if it comes to that, it does.. right? 

If you have another idea, or other software, im all ears- or just bite the bullet :)

---

### Post by Jakin on 2012-06-27
Okay i decided to do it, copied the backup boot sector, and now they are identical.
[IMG]http://img171.imageshack.us/img171/2628/screenshotsfj.png[/IMG]

gparted shows this- and it is promising, large block (presumably the main win7 partition) is unknown though.. any ideas?

---

### Post by darkod on 2012-06-27
Wait a minute, what do you mean by copied the backup boot sector?

testdisk was recognizing the win7 partition as ntfs in all of the searches. When writing the partition table with testdisk it should have written sda2 as ntfs too.

Like this, I wonder if chkdsk can run a check on it since it's not reported as ntfs.

Is this what you got after writing it with testdisk?

---

### Post by Jakin on 2012-06-27
Yes, i just let it write partitions as it showed on the screenshot. Then i checked what gparted had to say.

It had said boot partition didnt match the backup boot partition, and then asked if i wanted to copy the backup onto the boot. and just hit enter... maybe i shouldnt have?

---

### Post by darkod on 2012-06-27
Oh, man.... Don't know what to say. You can try running chkdsk like this, but I don't think it will check sda2. But you need to check all of them anyway, that's why Gparted has the warning mark next to each partition.

The filesystem looks really messed up.

This link is about reinstalling bootloaders but among there it has the procedure how to open the command prompt from the win7 dvd. In that command prompt you should be able to run chkdsk on all partitions.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If it doesn't wanna run on sda2, I have one idea but can't give you any guarantees. You can boot ubuntu cd in live mode again, open terminal and try to write the sda2 as ntfs. You can do that for example with cfdisk, it has a text interface rather easy to follow. There is an option to change the partition type, and it will list all types and ask you to enter two letter code. The code for ntfs is 07, it will be in the list. As far as I know, that doesn't format it, it will just mark it as ntfs which can help chkdsk check it after that.

So, from live mode it would be like:
sudo cfdisk /dev/sda
Select sda2, select to change the type, change it to 07.
Write changes and exit.

On another note, programs like photorec can recover data reading the disk regardless whether the filesystem is OK or not. But it usually changes the filenames to random, plus it recovers bunch of intentionally deleted stuff, so you end up with quite a mess. It's sort of a last resort.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Jakin on 2012-06-27
i tried sudo cfdisk just to see (didnt change a thing)

[IMG]http://desmond.imageshack.us/Himg525/scaled.php?server=525&filename=screenshotuik.png&res=landing[/IMG]

isnt that strange, there it says it IS NTFS.

---

### Post by darkod on 2012-06-27
Hmm, testdisk said the same.

Give chkdsk from the win7 dvd a shot. Who knows, maybe somehow only Gparted is confused about the filesystem since obviously has errors on it.

Out of curiosity, two more tools can show the partition type, again from ubuntu live mode in terminal:
```
sudo fdisk -l
sudo parted /dev/sda print
```

If you feel like it, check what they say. But in any case try the win7 dvd booted into repair mode and chkdsk.

---

### Post by mwclark4453 on 2012-06-27
Good luck.

---

### Post by Jakin on 2012-06-27
[IMG]http://img715.imageshack.us/img715/6476/screenshot1lv.png[/IMG]

[IMG]http://img827.imageshack.us/img827/7682/screenshot2bv.png[/IMG]

good call, gparted, for some reason, just doesnt detect the FS type. 

I shall try win7 chkdsk and get back to you :)

---

### Post by Jakin on 2012-06-27
No luck friend, i went to command console and tried both " bootrec.exe /fixboot " then it said Operation completed successfully. I also tried " bootrec /fixmbr " which yields the same result.
Also typed " chkdsk " as well, and it said filesystem appears to be fine. However the flags still appears in gparted.

---

### Post by darkod on 2012-06-27
Hold on, that link was just an idea how to get to the command console from the dvd. My idea was to run something like:
chkdsk c: /r /f

or similar. And hope that it will know the correct C: (/dev/sda2).

---

### Post by darkod on 2012-06-27
OK, you edited your post.

So, now if you try to boot, how far does it go? Or nothing at all?

You see, that is one of the problems with windows. You can only type chkdsk c: and hope it knows where c: is.

In linux when you use fsck you can specify on which partition you want to run it, so it can't miss.

---

### Post by Jakin on 2012-06-27
I tried " CHKDSK C: " it said 

Filesystem is NTFS. Unable to determine volume or state. CHKDSK Aborted.


So.. nothing.. Booting the computer alone, says " disk error has occured" hit ctl alt del.

---

### Post by darkod on 2012-06-27
It doesn't know which volume (partition) it is. :(

I'm out of ideas.

You could try the Repair This Computer option when you boot with the dvd (not the console approach) and see if the automatic method can detect your win7 somehow.

But I don't have high hopes.

Except the Photorec already mentioned, I don't have other ideas. Sorry. The filesystem seems really messed up.

---

### Post by Jakin on 2012-06-27
You mean the Automatic fix common boot errors? Ill try it.

Anyway thanks alot for tryin to help me out regardless :) I appreciate it.

Shouldnt have any problems just clean blanking the HDD entire (low level) and putting my OS back on right?

---

### Post by darkod on 2012-06-27
If you mean low level format, no need for it. Any quick format will wipe the partition table and allow you to reinstall using your win7 dvd.

The point was saving the data. Formatting and reinstalling is not an issue.

---

### Post by Jakin on 2012-06-27
I would have low level format for the sake of win7, its fragmentational issues, just sticking crap where it fits :P I figure might as well do low level while im at it. Anyway, we nearly got it, kudos to you- and Thanks again :) 

Always wanted to upgrade to win Ultimate anyway. (been using premium all this time) Atleast i was smart enough to frequently backup settings (did alot of customization) for my linux setup.. If only i went to extra mile of mass file backup..

---

