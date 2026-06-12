---
title: "Dual Boot Partitioning Assistance"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by garyt53 on 2013-07-11
Hi Folks -

Screwed up my UbuntuPrecise logical partition pretty good. ha

Am in a win7/Ubuntu12.04 64bit desktop environment and while resizing my logical Ubuntu partition I must have deleted the [5GB?] logical MBR/Grub as entire logical partition now registers unallocated.  win7 untouched so far and functions fine and need to be careful not to destroy it while recovering Ubuntu logical partition.  Ran BootRepair once and have attached the BootRepair log which you can use to guide me thru Ubuntu partition recovery.

Thank You in advance, many times I'm sure. ha

gt

love your cooperative product and really prefer to be there but win required for workware

---

### Post by oldfred on 2013-07-11
Welcome to the forums.

You do show some space between sda3 the extended (and sda5 which currently uses all of the extended, and sda4 at end of drive.
If you had a Linux partition the extended must have included the unallocated after the sda5 and been another logical partition. If it was on sdb, then the current three NTFS now include it.

I might backup current partition table.
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt
sudo sfdisk -d /dev/sdb > PTsdb.txt 

Then use testdisk to see what it says.
      
 [URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]https://help.ubuntu.com/community/DataRecovery#Lost%20Partition
[/URL]
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk

      [/URL]
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

    [URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

[URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]
[/URL]

---

### Post by garyt53 on 2013-07-12
Hi OldFred !

Will proceed to collect testdisk info for you to evaluate using my LiveCD....no reply OK  

You are quite right as I created a new quick formatted ntfs partition at the top of the now unallocated 166.50GB Ubuntu space, right after deleting an important 5GB ext4 from that logical 64.47GB ext4 space right after the 356GB win7 partition.

It's really going to hurt if it cannot be restored as I did a whole lotta customization to Precise and have only a way dated tar backup.  But worst case you will be able to guide me in retrieving 30GB of files from the now unallocated UbuntuSpace before I recreate Ubuntu from CD.  I know because not only was your response really fast but it was so pro it made me think without totally going over my head.  Besides, you're a mod....so as long as you still have some patience left.....(hehe)

Hey OldFred ! [I'm 60 myself]

I have attached the....well, they are self-explanatory.  The 3 TestDisk screenshots are coming in additional reply.  Hopefully, I have provided too much info but just ask and will develop more.  A TestDisk deep scan will take hours but looks unnecessary.  Oh yeah, sdb is a seperate internal terrabyte HDD.

I can read the GUI pics allright! ha  The "FromPrecise" partition structure GUI shows a green logical that used to encompass the 166GB once Ubuntu now unallocated partition.  I have not written anything to these partitions since I screwed up and quick formatted the now-logical green bordered 64.5GB partition, apparently unaddressing a 5GB partition needed for Ubuntu to boot.....maybe. ha

gt

Hey OldFred ! [I'm 60 myself]

I have attached the....well, they are self-explanatory.  The 3 TestDisk screenshots are coming in additional reply.  Hopefully, I have provided too much info but just ask and will develop more.  A TestDisk deep scan will take hours but looks unnecessary.  Oh yeah, sdb is a seperate internal terrabyte HDD.

I can read the GUI pics allright! ha  The "FromPrecise" partition structure GUI shows a green logical that used to encompass the 166GB once Ubuntu now unallocated partition.  I have not written anything to these partitions since I screwed up and quick formatted the now-logical green bordered 64.5GB partition, apparently unaddressing a 5GB partition needed for Ubuntu to boot.....maybe. ha

gt

just more ref files attached

gt

apparently the attachments didn't take somehow so here they are I hope

gt

one more....ironically the one you asked for (ha)

aah gotta paste the teskdisk log, developed from win7:

```
Sun Jul 14 23:12:03 2013
Command line: TestDisk

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Windows 7 (7601) SP1
Compiler: GCC 4.3, Cygwin 1007.7
Compilation date: 2011-11-15T08:36:54
ext2fs lib: 1.41.8, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20100226
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(/dev/sda)=640135028736
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(/dev/sdb)=1000204886016
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(/dev/sdg)=2017459712
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\PhysicalDrive0)=640135028736
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\PhysicalDrive1)=1000204886016
filewin32_getfilesize(\\.\PhysicalDrive2) GetFileSize err Incorrect function.

filewin32_setfilepointer(\\.\PhysicalDrive2) SetFilePointer err Incorrect function.

Warning: can't get size for \\.\PhysicalDrive2
filewin32_getfilesize(\\.\PhysicalDrive3) GetFileSize err Incorrect function.

filewin32_setfilepointer(\\.\PhysicalDrive3) SetFilePointer err Incorrect function.

Warning: can't get size for \\.\PhysicalDrive3
filewin32_getfilesize(\\.\PhysicalDrive4) GetFileSize err Incorrect function.

filewin32_setfilepointer(\\.\PhysicalDrive4) SetFilePointer err Incorrect function.

Warning: can't get size for \\.\PhysicalDrive4
filewin32_getfilesize(\\.\PhysicalDrive5) GetFileSize err Incorrect function.

filewin32_setfilepointer(\\.\PhysicalDrive5) SetFilePointer err Incorrect function.

Warning: can't get size for \\.\PhysicalDrive5
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\PhysicalDrive6)=2017459712
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\C:)=382527864832
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\D:)=11647582208
filewin32_getfilesize(\\.\E:) GetFileSize err Incorrect function.

filewin32_setfilepointer(\\.\E:) SetFilePointer err Incorrect function.

Warning: can't get size for \\.\E:
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\F:)=104857600
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\G:)=0
Warning: can't get size for \\.\G:
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\H:)=0
Warning: can't get size for \\.\H:
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\I:)=0
Warning: can't get size for \\.\I:
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\J:)=503299702784
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\K:)=392043692032
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\L:)=104857600000
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\M:)=0
Warning: can't get size for \\.\M:
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\X:)=67075152384
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\Y:)=11647582208
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\Z:)=2015193600
file_pread(4,1,buffer,1250274689(77825/254/63)) lseek err Invalid argument
file_pread(5,1,buffer,1953536129(121601/254/63)) lseek err Invalid argument
file_pread(6,1,buffer,3951989(245/254/63)) lseek err Invalid argument
Hard disk list
Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63, sector size=512 - WDC WD64 00AAKS-65A7B, S/N:WD-WCASYC179613, FW:01.0
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - Hitachi HDS721010CLA, S/N:JP2940HD0M0GTC, FW:JP4O
Disk /dev/sdg - 2017 MB / 1923 MiB - CHS 245 255 63, sector size=512 - SanDisk Cruzer, FW:7.01

Partition table type (auto): Intel
Disk /dev/sda - 640 GB / 596 GiB - WDC WD64 00AAKS-65A7B
Partition table type: Intel
file_pread(4,1,buffer,1250274689(77825/254/63)) lseek err Invalid argument

Analyse Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/32/33
NTFS at 12/223/20
Info: size boot_sector 747124721, partition 747124736
NTFS at 76409/19/27
BAD_RS LBA=747331647 63
NTFS at 46519/62/7
Info: size boot_sector 131006153, partition 131006157
Current partition structure:
 1 P HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
 2 * HPFS - NTFS             12 223 20 46519  61  6  747124736 [HP]
 3 E extended LBA         46519  61  7 54673 254 57  131006220
 4 P HPFS - NTFS          76409  19 27 77825  37 36   22749184 [FACTORY_IMAGE]
 5 L HPFS - NTFS          46519  62  7 54673 254 57  131006157 [ISOLATION]

Bad relative sector.
Computes LBA from CHS for Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
NTFS at 0/32/33
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
     NTFS, 104 MB / 100 MiB
NTFS at 12/223/20
filesystem size           747124721
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             12 223 20 46519  60 54  747124721 [HP]
     NTFS, 382 GB / 356 GiB
BAD_RS LBA=747331647 63
NTFS at 46519/62/7
filesystem size           131006153
sectors_per_cluster       8
mft_lcn                   3788777
mftmirr_lcn               8188648
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          46519  62  7 54673 254 53  131006153 [ISOLATION]
     NTFS, 67 GB / 62 GiB

recover_EXT2: s_block_group_nr=0/59, s_mnt_count=7/4294967295, s_blocks_per_group=8192, s_inodes_per_group=2032
recover_EXT2: s_blocksize=1024
recover_EXT2: s_blocks_count 487424
recover_EXT2: part_size 974848
     Linux                54674  68 51 54734 242 36     974848
     EXT4 Sparse superblock, 499 MB / 476 MiB

recover_EXT2: s_block_group_nr=0/111, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3643647
recover_EXT2: part_size 29149176
     Linux                54735  20  6 56549 135 26   29149176
     EXT4 Large file Sparse superblock, 14 GB / 13 GiB

recover_EXT2: s_block_group_nr=0/1202, s_mnt_count=11/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 39391743
recover_EXT2: part_size 315133944
     Linux                56549 168  4 76165 214  9  315133944
     EXT4 Large file Sparse superblock, 161 GB / 150 GiB
     Linux Swap           76165 246 50 76408 241 41    3903472
     SWAP2 version 1, 1998 MB / 1905 MiB
NTFS at 76409/19/27
filesystem size           22749184
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          76409  19 27 77825  37 36   22749184 [FACTORY_IMAGE]
     NTFS, 11 GB / 10 GiB
file_pread(4,2,buffer,1250265088(77825/102/38)) lseek err Invalid argument
file_pread(4,1,buffer,1250265088(77825/102/38)) lseek err Invalid argument
file_pread(4,8,buffer,1250263808(77825/82/18)) lseek err Invalid argument
file_pread(4,1,buffer,1250263808(77825/82/18)) lseek err Invalid argument
file_pread(4,8,buffer,1250263936(77825/84/20)) lseek err Invalid argument
file_pread(4,8,buffer,1250264064(77825/86/22)) lseek err Invalid argument
file_pread(4,8,buffer,1250264192(77825/88/24)) lseek err Invalid argument
file_pread(4,8,buffer,1250264320(77825/90/26)) lseek err Invalid argument
file_pread(4,8,buffer,1250264448(77825/92/28)) lseek err Invalid argument
file_pread(4,8,buffer,1250264576(77825/94/30)) lseek err Invalid argument
file_pread(4,8,buffer,1250264704(77825/96/32)) lseek err Invalid argument
file_pread(4,8,buffer,1250264832(77825/98/34)) lseek err Invalid argument
file_pread(4,8,buffer,1250264960(77825/100/36)) lseek err Invalid argument
file_pread(4,7,buffer,1250265089(77825/102/39)) lseek err Invalid argument
file_pread(4,8,buffer,1250265088(77825/102/38)) lseek err Invalid argument
file_pread(4,8,buffer,1250265096(77825/102/46)) lseek err Invalid argument
file_pread(4,3,buffer,1250265104(77825/102/54)) lseek err Invalid argument
file_pread(4,3,buffer,1250265151(77825/103/38)) lseek err Invalid argument
file_pread(4,8,buffer,1250265167(77825/103/54)) lseek err Invalid argument
file_pread(4,11,buffer,1250265214(77825/104/38)) lseek err Invalid argument
file_pread(4,2,buffer,1250267136(77825/135/7)) lseek err Invalid argument

Results
   * HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
     NTFS, 104 MB / 100 MiB
   P HPFS - NTFS             12 223 20 46519  60 54  747124721 [HP]
     NTFS, 382 GB / 356 GiB
   P HPFS - NTFS          46519  62  7 54673 254 53  131006153 [ISOLATION]
     NTFS, 67 GB / 62 GiB
   L Linux                54674  68 51 54734 242 36     974848
     EXT4 Sparse superblock, 499 MB / 476 MiB
   L Linux                54735  20  6 56549 135 26   29149176
     EXT4 Large file Sparse superblock, 14 GB / 13 GiB
   L Linux                56549 168  4 76165 214  9  315133944
     EXT4 Large file Sparse superblock, 161 GB / 150 GiB
   L Linux Swap           76165 246 50 76408 241 41    3903472
     SWAP2 version 1, 1998 MB / 1905 MiB
   L HPFS - NTFS          76409  19 27 77825  37 36   22749184 [FACTORY_IMAGE]
     NTFS, 11 GB / 10 GiB

interface_write()
 1 * HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
 2 P HPFS - NTFS             12 223 20 46519  60 54  747124721 [HP]
 3 P HPFS - NTFS          46519  62  7 54673 254 53  131006153 [ISOLATION]
 4 E extended LBA         54674   0  1 77825 254 63  371936880
 5 L Linux                54674  68 51 54734 242 36     974848
 6 L Linux                54735  20  6 56549 135 26   29149176
 7 L Linux                56549 168  4 76165 214  9  315133944
 8 L Linux Swap           76165 246 50 76408 241 41    3903472
 9 L HPFS - NTFS          76409  19 27 77825  37 36   22749184 [FACTORY_IMAGE]

search_part()
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
NTFS at 0/32/33
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
     NTFS, 104 MB / 100 MiB
NTFS at 12/223/19
filesystem size           204800
sectors_per_cluster       8
mft_lcn                   8533
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
     NTFS found using backup sector!, 104 MB / 100 MiB
NTFS at 12/223/20
filesystem size           747124721
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             12 223 20 46519  60 54  747124721 [HP]
     NTFS, 382 GB / 356 GiB
Search for partition aborted

Results
   * HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
     NTFS, 104 MB / 100 MiB
   P HPFS - NTFS             12 223 20 46519  60 54  747124721 [HP]
     NTFS, 382 GB / 356 GiB

interface_write()
 1 * HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]
 2 P HPFS - NTFS             12 223 20 46519  60 54  747124721 [HP]
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
```

---

### Post by oldfred on 2013-07-15
Please use code tags for long script output.

Your one screen shot does show a Linux partition. Did you try changing to undelete it? It shows it three times so you must have changed the size a couple of times. You have to know or guess which is the correct one. Generally the largest that does not overlap with your existing partitions.

---

### Post by garyt53 on 2013-07-15
changing to undelete?  using TestDisk?  could you clarify? 

again you're very correct as I did reduce the size of the 166GB unallocated space while moving it to the right to eventually create new tailspace for win7.....it was after this first step in repartitioning that I believe I screwed up by deleting a 5GB ext4 partition that was preventing extending win7

my goal here is to restore the once Ubuntu logical by combining the 62GB and 166GB partitions comprising the once Ubuntu logical (recovering from my partitioning errors) then expanding win7 C: into newly created freespace....so like ya said the first step is recovering the 62GB quickreformatted part huh - will await your step-by-step to compensate for my apprehension (based on HDD ignorance)

[I think my problems arose from my being a newby and reading up beforehand determining that ext4 parts must be modified by GParted and ntfs, specifically NT parts, must be addressed with a win-specific tool....pref the DiskManagement tool]

again, your response time is great!.....and your response concise - painfully actually, but I understand you are trying to teach me the 'mysteries' of dual-boot HDD physics, ha

gt

---

### Post by oldfred on 2013-07-15
Screenshot 1 of 5 in post #7 shows testdisk with 3 Linux logical partitions. Usually a deleted partition has the D not the L? That would be saying it is there.

---

### Post by garyt53 on 2013-07-18
Hi Fred -

Can you step-by-step clarify "Did you try changing to undelete it?".....using TestDisk?  I am quite apprehensive making MBR/MFT changes without knowledgeable guidance.

gt

---

### Post by oldfred on 2013-07-18
I cannot do any better than this:
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Boab1993 on 2013-07-18
Hello garyt53

I have a dual boot system on my dektop between xubuntu and win7.
To maintain good practise the windows partition should always be installed as the primary and the linux as secondary, in the short the explaination for this is windows is 'pissy'.
As for deleting the ubuntu MBR, easy way out would be to just re-install ubuntu. During the live cd setup you can custom edit existing partitions of both OS's aswell, as nothing is mounted at this time, it allows for free editing of all areas of your hardrive, id take your time though, it can go wrong very easily if you dont know what your doing.
Something you should remember is when re-sizing partitions if you want it done quickly you are most likely going to have to format that partition this means you would lose all data on that area, my advise would be to save anything important.

Hope this helps

---

### Post by garyt53 on 2013-07-30
Hi Folks -

Wow, I would have thought they would have targeted Wall Street to destroy all the evidence myself. ha

So, it was the Ubuntu MBR I deleted....and that I merely need to undelete it in TestDisk.

Will go to TestDisk instructions, reread and attempt undeleting that 5GB.

Hi Folks -

Been away for a bit.  And if I knew this would be getting so many views, I would have been more concise.  Pretty hard to have a concise thread though when you're holding somebody's hand. ha

So, reviewed the instruct, quick reformatted the partition I "deleted", and chose to just recover the 40GB of important stuff and reformat/reinstall/andouch:reconfigure but another distro.

So all I need from you now is how do I best recover my data from a partition marked unallocated?

---

### Post by oldfred on 2013-08-12
If testdisk deep scan does not show any files, you can use photorec which is also part of testdisk. I have used photorec and it is a long slow process. It takes a long time as all it can do is scan drive for anything that looks like a file. It cannot recover file name, but just extension. So a lot more time to sort thru files and figure out what they are. Photos and music have internal metadata to help rename.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)


 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by garyt53 on 2013-08-12
OK Fred & Bo........

Restored Ubuntu effectively, but now Windows is gone!  [SIZE=1]just kidding hehe[/SIZE]

Thank you both for your uncomfortably concise handholding on this issue.  Was way easy, but way scary.  Just clicked on the sliver of a boot part and rewrote it's handles, restoring the partition!  Hey, it even would have been scary if I took it in to a shop and watched. haha  So Bo....Thanks to you for sending me back to Fred's solution by making file recovery from unallocated space seem impractically difficult and iffy.  And thanks for the "be careful" that stopped me from doing the unintended, that I almost did.

Part of us will always be that jungle native that caught the coke bottle tossed from a plane, huh.  Nobody really even knows where it's at to be the best cause there will always be more to learn....about most things.

Conclusion: don't know about file recovery, but TestDisk is a powerful and safe data structure recovery tool for mistakes made 2 levels deep.  And be careful, not afraid. ha

Thread closed.  Thanks for being here.....again. ha

gt

Oops......GParted indicates all 575GB of the HDD as unallocated......BUT 12.04 LTS CRUISES ALONG GREAT!

Windows Disk Management indicates all partitions present but no logical green bar eclosing the ext4 Ubuntu parts,   And when pressuring the OS with Nexwiz, the sys monitor indicates no swap file.

Any advice?

---

### Post by oldfred on 2013-08-13
There may be some issue somewhere. Sometimes gparted does not show partitions if chkdsk on NTFS or fsck needed on ext4 partitions. Usually now it shows partition with a red or yellow flag.

I might try fsck on all ext4 partitions otherwise post partition table.
 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Do either of these give any errors?
      
 sudo parted /dev/sda unit s print
      
 sudo fdisk -lu /dev/sda

---

### Post by garyt53 on 2013-08-26
Hi Folks -

GParted indicates HDD unallocated.
win7 indicates as intact parts less original logical encapsulation.
fsck ran on ext4 OK, on individual parts after trying and failing with other fsck switches.  See attached.

Need another TestDisk log?

gt

Attachment wouldn't take so had to disassemble to send individually.

OK now.....sheeesh.

---

### Post by Bucky Ball on 2013-08-26
*Thread moved to **Installation & Upgrades**.*

---

### Post by garyt53 on 2013-08-31
Hi Folks -

So.....do I somehow wrap an extended partition around all the ext4 parts so GParted sees the partitions?  I have found a similar incident online but it has yet to be resolved also.  Have pulled all irreplaceable data off both OSs so if I have to reinstall am now prepared to.....except all the custom setups.  Is this missing extended partition wrap even an issue?  I guess cause cannot modify the parts with GParted anymore huh.  And told it's not advisable to do so from win7.  Or to modify win7 parts with any third party utilities either.  Was told to modify Linux with GParted only and win7 with Disk Management Utility only.

gt

---

### Post by Bucky Ball on 2013-08-31
> **garyt53 said:**
> So.....do I somehow wrap an extended partition around all the ext4 parts so GParted sees the partitions?

That is an impossibility. You need to delete the EXT4 partitions, create an extended in the free space you've created, create four logical partitions in there, transfer original data back to the logical partitions that was originally on your primaries. 

> **garyt53 said:**
> Have pulled all irreplaceable data off both OSs so if I have to reinstall am now prepared to.....

Then you could do what I suggest without issue. 

> **garyt53 said:**
> Was told to modify Linux with GParted only and win7 with Disk Management Utility only.

Always.

---

### Post by garyt53 on 2013-08-31
Hey wow thanks.  Seems pretty straightforward: move my existing ext4 data offdisk in folders corresponding to ext4 partitions indicated in win7, recreate parts in GParted inside newly recreated extended part, then just move the ext4 part data back into newly created extended parts.  Wish TestDisk could restore the extended though.

So I guess this thread is really closed now huh.  Unless you have any warnings for me when recreating original part structure on a disk that reads entirely unallocated in GParted or regarding accessing the individual existing partition data to move it offdisk before recreating the original partition structure to move the data back on to.

Will check back in  a coupla days in case you have any headsup for me.  Otherwise I have concluded my input on this issue and will do as you suggest at the top of your last post.  Uncharted territory for me but you make it sound pretty easy.

Thanks, and goodbye probably.

gt
tiredofalltheliesfromthemoneyjunkieparasitesthatcauseallhumanmiseryforprofitandcontrolhuh

Have not yet had the opportunity to exercise the repartitioning and data transfer you suggested in order to restore the extended ext4 partition encapsulation that was originally created on Precise install.....but curiously Precise12.04 is working great without it.  Grub too.

When I do, I will post my results and close this issue.  Maybe a week.

gt

---

