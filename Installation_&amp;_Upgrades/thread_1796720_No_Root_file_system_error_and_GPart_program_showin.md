---
title: "No Root file system error and GPart program showing Blank HDD"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by rahulkale on 2011-07-04
**Hi guys, I am new to Ubuntu**:) and just saw a version on the net 11.04 and decided to try it out.

Ok let me tell u in short *what i did before I got a Problem* with the installation.

1..I have a 80 gigs drive, divided into 4 partitions.
2..I decided to try ubuntu on G Drive which had 3gigs free using WUBI. Well it worked and was installed succesfully. Worked good, so I decided to make a separate partition for ubuntu system.
3.. I uninstalled ubuntu first then with the PArtiotion Master resized the G drive(18gb) to 12 gb and 6 gb(for Ubuntu)  
4.. Tried installing uding WUBI again, now there's a catch now, I am getting 2 main problems.

**1 Prob:** If I try installing using a dvd and select the option Try and Install, I get an ERROR : No Root file system is defined.

I checked on the forum and saw that we need to define the root file drive as "/", but i cant, since i get this Image  




[IMG]http://i54.tinypic.com/6glk7q.jpg

**2 Prob :** I Decided to partition the drive using the Gpart in ubuntu, but this is the problem i get..

My HDD is of 80gb, and completely partiotioned but using Partition MAster i Get this data 


[IMG]http://i56.tinypic.com/xbda0y.gif[/IMG]

using Windows Disk mahagement I get this Image


[IMG]http://i54.tinypic.com/11klb41.jpg[/IMG]

and using UBUNTU Gpart i get this image


[IMG]http://i53.tinypic.com/2zrl2d1.png[/IMG]


I am also Inserting the "sudo fdisk -l" command result


[IMG]http://i52.tinypic.com/wqygqt.png[/IMG]

well in all this can be briefed as the HDD is showing unwanted extra space as "Free space 19GB"
Image as in DIsk Utility in Ubuntu  


[IMG]http://i55.tinypic.com/141ocuf.png


> PS:
Picture speak more than words... 
I hope I have completely defined my Problem ... 

I know that UBuntu Community Is known for response to all questions
:)

---

### Post by coffeecat on 2011-07-04
I suspect that Easus Partition Master has put an illegal entry in your partition table. The commonest cause of Gparted showing "unallocated" when there are clearly partitions present is an extended partition end boundary beyond the end of the physical drive -  which is clearly an impossibility. Unfortunately I cannot see whether this is so, because you have run fdisk with the -l option which gives you partition start and end figures in cylinders. We need sector figures. Run fdisk from an Ubuntu terminal again but this time run:

```
sudo fdisk -lu
```

Please post the output between [noparse]```
 and 
```[/noparse] tags for clarity, not as a screenshot. You can highlight the terminal output with your mouse and then right-click -> copy to copy it into the clipboard before pasting it into your post.

If my theory is correct, then this is very easily fixed.

---

### Post by rahulkale on 2011-07-04
Here is the output 

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x049d049d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    43006005    80774819    18884407+   c  W95 FAT32 (LBA)
/dev/sda2        80774820   118543634    18884407+   c  W95 FAT32 (LBA)
/dev/sda3           16126   156296384    78140129+   f  W95 Ext'd (LBA)
/dev/sda5           16128    13333949     6658911    b  W95 FAT32
/dev/sda6        13334013    43006004    14835996    7  HPFS/NTFS
/dev/sda7       118543699   156296384    18876343    b  W95 FAT32

Partition table entries are not in disk order
ubuntu@ubuntu:~$ [/QUOTE]



also the output of boot info script

[QUOTE]
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 16128. "63" and "2048" are quite 
                       common values for the starting sector of a logical 
                       partition and they only need to be fixed when you want 
                       to boot Windows from a logical partition.
    Operating System:  Windows XP
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda7 starts at sector 118543699. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda7/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     43,006,005    80,774,819    37,768,815   c W95 FAT32 (LBA)
/dev/sda2          80,774,820   118,543,634    37,768,815   c W95 FAT32 (LBA)
/dev/sda3              16,126   156,296,384   156,280,259   f W95 Extended (LBA)
/dev/sda5              16,128    13,333,949    13,317,822   b W95 FAT32
/dev/sda6          13,334,013    43,006,004    29,671,992   7 NTFS / exFAT / HPFS
/dev/sda7         118,543,699   156,296,384    37,752,686   b W95 FAT32

/dev/sda1 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda3

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 11.04 i386
/dev/loop1                                              squashfs   
/dev/sda1        DC62-FD37                              vfat       GAME
/dev/sda2        2C6D-6DFF                              vfat       STUDY DATA
/dev/sda5        C8A7-B4D8                              vfat       MAIN DRIVE
/dev/sda6        7E54FD9E54FD597B                       ntfs       MOVIES
/dev/sda7        CC7B-44C1                              vfat       SONG MOVIE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/MOVIES            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  01 cf 0a 00 02 cf 0a 00  03 cf 0a 00 04 cf 0a 00  |................|
00000010  05 cf 0a 00 06 cf 0a 00  07 cf 0a 00 08 cf 0a 00  |................|
00000020  09 cf 0a 00 0a cf 0a 00  0b cf 0a 00 0c cf 0a 00  |................|
00000030  0d cf 0a 00 0e cf 0a 00  0f cf 0a 00 10 cf 0a 00  |................|
00000040  11 cf 0a 00 12 cf 0a 00  13 cf 0a 00 14 cf 0a 00  |................|
00000050  15 cf 0a 00 16 cf 0a 00  17 cf 0a 00 18 cf 0a 00  |................|
00000060  19 cf 0a 00 1a cf 0a 00  1b cf 0a 00 1c cf 0a 00  |................|
00000070  1d cf 0a 00 1e cf 0a 00  1f cf 0a 00 20 cf 0a 00  |............ ...|
00000080  21 cf 0a 00 22 cf 0a 00  23 cf 0a 00 24 cf 0a 00  |!..."...#...$...|
00000090  25 cf 0a 00 26 cf 0a 00  27 cf 0a 00 28 cf 0a 00  |%...&...'...(...|
000000a0  29 cf 0a 00 2a cf 0a 00  2b cf 0a 00 2c cf 0a 00  |)...*...+...,...|
000000b0  2d cf 0a 00 2e cf 0a 00  2f cf 0a 00 30 cf 0a 00  |-......./...0...|
000000c0  31 cf 0a 00 32 cf 0a 00  33 cf 0a 00 34 cf 0a 00  |1...2...3...4...|
000000d0  35 cf 0a 00 36 cf 0a 00  37 cf 0a 00 38 cf 0a 00  |5...6...7...8...|
000000e0  39 cf 0a 00 3a cf 0a 00  3b cf 0a 00 3c cf 0a 00  |9...:...;...<...|
000000f0  3d cf 0a 00 3e cf 0a 00  3f cf 0a 00 40 cf 0a 00  |=...>...?...@...|
00000100  41 cf 0a 00 42 cf 0a 00  43 cf 0a 00 44 cf 0a 00  |A...B...C...D...|
00000110  45 cf 0a 00 46 cf 0a 00  47 cf 0a 00 48 cf 0a 00  |E...F...G...H...|
00000120  49 cf 0a 00 4a cf 0a 00  4b cf 0a 00 4c cf 0a 00  |I...J...K...L...|
00000130  4d cf 0a 00 4e cf 0a 00  4f cf 0a 00 50 cf 0a 00  |M...N...O...P...|
00000140  51 cf 0a 00 52 cf 0a 00  53 cf 0a 00 54 cf 0a 00  |Q...R...S...T...|
00000150  55 cf 0a 00 56 cf 0a 00  57 cf 0a 00 58 cf 0a 00  |U...V...W...X...|
00000160  59 cf 0a 00 5a cf 0a 00  5b cf 0a 00 5c cf 0a 00  |Y...Z...[...\...|
00000170  5d cf 0a 00 5e cf 0a 00  5f cf 0a 00 60 cf 0a 00  |]...^..._...`...|
00000180  61 cf 0a 00 62 cf 0a 00  63 cf 0a 00 64 cf 0a 00  |a...b...c...d...|
00000190  65 cf 0a 00 66 cf 0a 00  67 cf 0a 00 68 cf 0a 00  |e...f...g...h...|
000001a0  69 cf 0a 00 6a cf 0a 00  6b cf 0a 00 6c cf 0a 00  |i...j...k...l...|
000001b0  6d cf 0a 00 6e cf 0a 00  6f cf 0a 00 70 cf 00 01  |m...n...o...p...|
000001c0  01 01 0b fe ff 3d 02 00  00 00 be 36 cb 00 00 00  |.....=.....6....|
000001d0  c1 3e 05 fe ff ff c0 36  cb 00 77 c2 c4 01 00 00  |.>.....6..w.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda7/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=============================== StdErr Messages: ===============================

umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---

### Post by psusi on 2011-07-04
Your partition table is corrupt because the extended partition overlaps the first two primary partitions.

---

### Post by coffeecat on 2011-07-04
The corruption to your partition table is far worse than I expected. The two primary partitions are "inside" the extended partition, which is impossible. **Edit** In fact this was clear from your earlier fdisk output, so apologies for missing that. **End edit** Did you run the Windows XP installer? It has been known to do nonsense like this on ocassion. Or did you use any partitioning software other than Easus? 

It's too late here and I'm too tired to post anything really coherent, but I'll have a look in the morning to see what I can suggest to repair the damage. Unless someone else does so first.

---

### Post by rahulkale on 2011-07-04
@coffeecat Yes I did try to repair XP with a bootable Cd 3 4 days back, I thought it may be a temp problem. Please let me know what are the possibilities to work this out. 
   A warm thanks for giving your time to me... :)

---

### Post by YesWeCan on 2011-07-05
The partition tables in each partition boot record can be found using
[COLOR=Navy]sudo sfdisk -d --force /dev/sdn[/COLOR]  (where n=partition number)

---

### Post by rahulkale on 2011-07-05
How can I use the "sudo sfdisk -d --force /dev/sdn " command to solve my problem ??

---

### Post by rahulkale on 2011-07-05
In the worst case if I decide to format the drive, i.e after taking a back up of my data but keeping the XP working and only formating the other remaining Drives ... Will that solve the Problem ???

---

### Post by coffeecat on 2011-07-05
> **rahulkale said:**
> How can I use the "sudo sfdisk -d --force /dev/sdn " command to solve my problem ??

No. You can use sfdisk to edit a partition table, but a simple edit will not do. See below.

> **rahulkale said:**
> In the worst case if I decide to format the drive, i.e after taking a back up of my data but keeping the XP working and only formating the other remaining Drives ... Will that solve the Problem ???

Well - I have now had a chance to look at your data properly. The bad news first: your partition table is a mess. It is theoretically fixable but if this was my machine I would start over. Making new partitions for XP and re-installing XP as well. There are too many problems which I outline below.

First, a preamble. With the mbr type partition table, which is what your hard drive has, you are limited to four primary partitions, which in Linux are numbered 1,2,3 or 4. To get around this limitation, one primary partition may be an extended partition, also numbered 1,2,3 or 4. An extended partition is merely a special type of primary partition whose sole purpose is to act as a container for logical partitions. Logical partitions in Linux are numbered 5 and upwards. In your case sda1 and sda2 are your two primary partitions, sda3 your extended, and sda5, sda6 and sda7 the logical partitions. The main problem is that sda1 and sda2 are "inside" your extended partition, sda3. This is impossible. It would normally have been a fairly easy task to edit the partition table to correct this illegality but for the next problem. You have logical partitions physically either side of the primaries. One or more would have to be converted to primary partitions.

Below is a table representing the partitions as they appear in order on your hard drive:

```
Partition	"Drive"		Label		Size (GiB)	Type

sda5		D:		MAIN DRIVE	6.35		Logical
sda6		E:		MOVIES		14.15		Logical
sda1		C:		GAME		18.01		Primary
sda2		F:		STUDY DATA	18.01		Primary
sda7		G:		SONG MOVIE	18.00		Logical
```

Your Wubi installation is on sda7, your "G:" drive in Windows parlance. Your "C:" drive is formatted FAT32 which is unusual for Windows XP and oddly has the partition label "GAME". Finally, the start sector for the first physical partition is 16126, which is very odd. Normally it would be 63 or 2048. None of these latter points are problematic singly, but add up to a partition layout which needs a thorough rethink and clearout.

A useful link for you:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Have a think about all that and post back if you need any help.

---

### Post by rahulkale on 2011-07-05
@Coffeecat : Considering all the mixed up partitions and also that i Really want to be a Ubuntu user I am going to Backup an Format the entire disk.

I just need one last help as to which partition format should i use 
Fat32 or Ntfs ??

I am thinking as 
10gb -- Xp
10gb -- Ubuntu
remaining as required. Going to install Xp first.

---

### Post by coffeecat on 2011-07-05
> **rahulkale said:**
> I just need one last help as to which partition format should i use 
Fat32 or Ntfs ??

I am thinking as 
10gb -- Xp
10gb -- Ubuntu
remaining as required. Going to install Xp first.

Use NTFS for Windows XP. XP will run in FAT32, but NTFS is a journalled filesystem and more robust. Will 10GB be enough for XP? Seems a little small to me. 10GB will be enough for Ubuntu so long as you have your personal files in another partition, either a separate home partition or a shared Data drive.

Yes install XP first. With a 80GB drive for a dual-boot Windows/Ubuntu system what I would choose is an NTFS partition for Windows C:, ext4 for Ubuntu and a shared Data partition formatted NTFS which both Ubuntu and Windows will be able to read and write to. Forget about FAT32 for internal partitions. Ubuntu can read and write NTFS reliably. You will also need a separate swap partition for Ubuntu - Linux uses a swap partition.

Have a read of the link I posted - follow all the links in it as well. That should answer most of your questions about partitioning for dual-booting Windows and Ubuntu. Once you've absorbed all that, post again if you need anything clarifying. And good luck!

---

### Post by YesWeCan on 2011-07-05
As long as the actual partition sector ranges are correct, it ought to be possible to correct the PT entries.
The sda numbers are out of correct order now but will correct themselves.

 ```

partition        start sector         end sector          total sectors          used for                              
sda3                 16126             156296384            156280259             Ext'd              
sda5                 16128              13333949             13317822             FAT32                              
sda6              13334013              43006004             29671992             NTFS                              
sda1              43006005              80774819             37768815             FAT32                              
sda2              80774820             118543634             37768815             FAT32                              
sda7             118543699             156296384             37752686             FAT32                              

total sectors: 156301488         
```It looks as if sda5 (XP OS) is supposed to be the first primary partition because its boot sector expects it to be at sector 63. It could be adjusted in the MBR PT to start at 63. Its sector size is correct for 6.35GiB. So I think this one is fixable.
[edit] No that's not quite right. Assuming the XP partition has been moved and really does start at 16126 (which is what bootinfoscript seems to think) then either make sda5  back into a primary by fixing the ext'd PT and then make it bootable. XP might boot even though it is in the wrong location. OR move the XP data to start at 63 and adjust the PT accordingly.

The MBR PT entry for the ext'd partition sd3 needs to have its start end end sectors reset. It may be possible to deduce what they are meant to be from the PTs in each partitions boot sector. Then they can be corrected. It's a fiddly operation but doable.

To show all the current PTs, post the output of:
sudo sfdisk -d --force /dev/sdaN  (for each N=1,2,3,5,6,7)

---

### Post by YesWeCan on 2011-07-05
The more I think about this the easier I think it is (famous last words?). The MBR PT needs to be seen to determine which of these partitions is primary and which is logical. And the start of the Ext'd partition needs to be changed accordingly - the problem now (one of them) is that it starts at 16126 which is bogus - it probably ought to start at where sda1 or sda2 is now). The PT contents of MBR and the partitions should show how to unscramble it.

To show the MBR PT:
sudo sfdisk -d /dev/sda

---

### Post by coffeecat on 2011-07-05
> **YesWeCan said:**
> The MBR PT needs to be seen to determine which of these partitions is primary and which is logical.

We already know which are primary and which are logical. The output of sfdisk will tell us nothing that fdisk has already told us.

> **YesWeCan said:**
>  And the start of the Ext'd partition needs to be changed accordingly - the problem now (one of them) is that it starts at 16126 which is bogus - it probably ought to start at where sda1 or sda2 is now).

The extended partition starts at sector 16126, at the moment. One of the problems is that sda5 and sda6 think that they start at sector 63. This is not uncommon when Windows partitions put their boot files into another partition which does start at sector 63. But there is now no partition beginning at sector 63 - there must once have been. What worries me is that if there is essential code at sector 63 and the following few sectors, it is now in unpartitioned space and in danger of being overwritten by partitioning software.

> **YesWeCan said:**
>   The PT contents of MBR and the partitions should show how to unscramble it.

What you haven't yet mentioned is the fact that the primary partitions are surrounded by logical ones, which makes the unscrambling that much more difficult.

Nevertheless, if you can help the OP unscramble this mess I'll take my hat off to you! :) Good luck!


**EDIT**: by the way, a useful tip. Why not direct the output of this command...

> **YesWeCan said:**
> ```
sudo sfdisk -d /dev/sda
```

... to a text file? Thus:

```
sudo sfdisk -d /dev/sda > PT.txt
```

You then have something that can be edited and written back to the partition table using sfdisk again. You also have a permanent record of the partition table as it is now, in case of further problems.

---

### Post by YesWeCan on 2011-07-05
> **coffeecat said:**
> We already know which are primary and which are logical. The output of sfdisk will tell us nothing that fdisk has already told us.
Well I'm not so sure. ;) I would like to see what is actually on the disk in each PT. fdisk gives us its interpretation of what's on the disk but it may be getting conflicting info, eg: the Ext'd primary partition address range is bogus. So do the actual primary partition entries conflict with the Ext'd entry?
Anyway, it's up to the OP to decide whether to fix it or reformat it. Whatever.

---

### Post by coffeecat on 2011-07-05
> **YesWeCan said:**
> fdisk gives us its interpretation of what's on the disk but it may be getting conflicting info, eg: the Ext'd primary partition address range is bogus. So do the actual primary partition entries conflict with the Ext'd entry?

In fact fdisk does not "interpret" what's on the disk. With the -l option it simply:

[quote="man fdisk"] -l

List the partition tables for the  specified  devices  and  then exit.  [/quote]

The format of the output provided by fdisk -l (-u) and that provided by sfdisk -d is a little different, but it is essentially the same information.

---

### Post by srs5694 on 2011-07-05
This problem is easily fixed by my [FixParts](http://www.rodsbooks.com/fixparts/) program. FixParts might or might not reassign the partitions' statuses automatically; you might need to fiddle with primary/logical assignments a bit. You can, however, make the current partitions 5 and 6 logicals (which they are) and 1, 2, and 7 primaries (1 and 2 are already primaries, but 7 is currently logical). In other words, you just need to reassign 7 from logical to primary, unless I'm missing something. Read the FixParts Web site for a description of how to use it.

[quote=YesWeCan][quote=coffeecat]We already know which are primary and which are logical. The output of sfdisk will tell us nothing that fdisk has already told us.
[/quote]Well I'm not so sure. :wink:  I would like to see what is actually on the disk in each PT. fdisk  gives us its interpretation of what's on the disk but it may be getting  conflicting info, eg: the Ext'd primary partition address range is  bogus. So do the actual primary partition entries conflict with the  Ext'd entry?[/quote]

Coffeecat is absolutely correct about this. Neither fdisk nor sfdisk does much in the way of "interpretation" of the data, except that fdisk reports partition end points when in fact they're recorded as lengths, at least in the LBA coding that's important these days. (They're recorded as end points in the CHS coding, but that maxes out at about 8 GB, and so is useless for most disks and partitions these days.) If fdisk says that a primary partition resides inside the range of an extended partition, then that's what the partition table records, even though it's illegal. I've created such configurations on my own system several times and I've seen numerous reports of this type of problem on this forum. The Windows XP installer is known to create such bogus partition tables under certain circumstances, and probably other utilities do, too. I designed FixParts specifically to fix this problem, along with some other common partition table problems.

---

### Post by psusi on 2011-07-05
> **coffeecat said:**
> But there is now no partition beginning at sector 63 - there must once have been. What worries me is that if there is essential code at sector 63 and the following few sectors, it is now in unpartitioned space and in danger of being overwritten by partitioning software.

Huh?  If the windows partition has been moved, then it has been moved -- what was at sector 63 is now at the new location, so who cares what goes on at the original location?

Of course, Windows is unable to boot when it has been moved and the boot sector not been fixed to point to the new location.

---

### Post by YesWeCan on 2011-07-05
@srs5694: I am not interested in point scoring. You trust what you want. My experience is not as rosy as yours seems to be.

fdisk does not just report what is in the MBR PT. If it sees an extended primary partition it will go and look for PTs in the EBR of the extended partition, where it may find correct or incorrect information. Now if the EBR information, or any info that is daisy-chained in other PBRs, conflicts with what is in another PT then what does it report? Does it report a conflict? Does it report the last thing it saw? This is what I mean by interpretation.

I personally would not trust the output of fdisk or GParted at this point. I would want to be absolutely sure about what is actually going on on a corrupted disk.

Take it or leave it.

[edit]
It would be really useful if fdisk had an option to display the actual PT contents of all the PTs on the disk. :)

---

### Post by YesWeCan on 2011-07-05
> **psusi said:**
> Huh?  If the windows partition has been moved, then it has been moved -- what was at sector 63 is now at the new location, so who cares what goes on at the original location?

Of course, Windows is unable to boot when it has been moved and the boot sector not been fixed to point to the new location.
Right. I'm guessing that once the XP OS partition's MBR PT entry is fixed and set to active and if it won't boot, it can either have its boot sector fixed by the XP CD or the whole partition can (not trivial to do) be moved back to start at 63.

---

### Post by srs5694 on 2011-07-05
> **YesWeCan said:**
> @srs5694: I am not interested in point scoring. You trust what you want. My experience is not as rosy as yours seems to be.

Please elaborate. Give an example of when fdisk has been wrong and in what ways.

> fdisk does not just report what is in the MBR PT. If it sees an extended primary partition it will go and look for PTs in the EBR of the extended partition, where it may find correct or incorrect information.

True, although in this context, what is "correct" vs. "incorrect" information is murky. By definition, the MBR and EBRs collectively define the partitions on the disk; that is, they are the authoritative information for what the partitions are. Of course, this information can become damaged in various ways, as has happened in this thread; but the point is that if fdisk is reporting a particular configuration, such as a primary partition being inside an extended partition, that is what is recorded on the disk. fdisk doesn't, in my experience, misrepresent such problems; if fdisk says that something illegal like that is going on, then that's what's recorded in the partition table. I've confirmed this many times with sector editors.

GParted, by contrast, *does* misrepresent such problems: It shows the disk as being completely empty when it runs into illegal configurations.

> Now if the EBR information, or any info that is daisy-chained in other PBRs, conflicts with what is in another PT then what does it report? Does it report a conflict? Does it report the last thing it saw? This is what I mean by interpretation.

It's not clear what you mean by this. First, "PBR" means "partition boot record" -- that is, the first sector of a partition, where boot loader information resides. This is part of a *filesystem* data structure, not a partition table data structure. I'll assume you meant "EBRs" (extended boot records), where logical partitions are defined....

Data in different EBRs can certainly be inconsistent, in the sense that they report overlapping partitions, partitions that end before they begin, etc. If so, fdisk will show the inconsistent data as it's recorded on the disk, and in some cases it'll display a message to the effect that there's a problem -- although it doesn't in the specific case under discussion in this thread. That's not interpretation -- it's reporting the data as they exist.

> I personally would not trust the output of fdisk or GParted at this point. I would want to be absolutely sure about what is actually going on on a corrupted disk.

The only way to get information that's less interpreted than that shown by fdisk's standard "p" display is to dig into the data structures with a sector editor or the "d" option on fdisk's experts' menu (see below). Furthermore, this type of problem has been reported here many times, and has been investigated by myself and by others enough to know of at least one specific cause -- namely, that the Windows XP installer, when faced with fewer than four primary partitions (counting the extended partition as a primary partition) and logical partitions that are not in strictly ascending order, will convert one of the logical partitions into a primary partition without adjusting the size of the extended partition as necessary.

This problem is *well understood*, at least by the few people who've studied it, including me. I understand it well enough that it was relatively easy for me to adapt some of my existing code to fix the problem. The result is FixParts. The fact that you don't understand the problem as well as I do is certainly no crime, but please don't mistake your own lack of understanding for a problem with fdisk.

> 
It would be really useful if fdisk had an option to display the actual PT contents of all the PTs on the disk. :)

You mean like this?:

```
$ sudo fdisk /dev/sdc

Command (m for help): p

Disk /dev/sdc: 2038 MB, 2038431744 bytes
63 heads, 62 sectors/track, 1019 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     2099199     1048576   83  Linux
/dev/sdc2         2101247     3981278      940016    f  W95 Ext'd (LBA)
/dev/sdc5         2101248     3981278      940015+   7  HPFS/NTFS/exFAT

Command (m for help): x

Expert command (m for help): d
Device: /dev/sdc
0x000: FA B8 00 10 8E D0 BC 00 B0 B8 00 00 8E D8 8E C0
0x010: FB BE 00 7C BF 00 06 B9 00 02 F3 A4 EA 21 06 00
0x020: 00 BE BE 07 38 04 75 0B 83 C6 10 81 FE FE 07 75
0x030: F3 EB 16 B4 02 B0 01 BB 00 7C B2 80 8A 74 01 8B
0x040: 4C 02 CD 13 EA 00 7C 00 00 EB FE 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 21
0x1C0: 03 00 83 1B 84 19 00 08 00 00 00 00 20 00 00 3C
0x1D0: 86 19 0F 11 CB FB FF 0F 20 00 E0 AF 1C 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

0x000: FA B8 00 10 8E D0 BC 00 B0 B8 00 00 8E D8 8E C0
0x010: FB BE 00 7C BF 00 06 B9 00 02 F3 A4 EA 21 06 00
0x020: 00 BE BE 07 38 04 75 0B 83 C6 10 81 FE FE 07 75
0x030: F3 EB 16 B4 02 B0 01 BB 00 7C B2 80 8A 74 01 8B
0x040: 4C 02 CD 13 EA 00 7C 00 00 EB FE 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3C
0x1C0: 87 19 07 11 CB FB 01 00 00 00 DF AF 1C 00 00 3C
0x1D0: 86 19 00 11 CB FB 00 00 00 00 00 00 00 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA


Expert command (m for help):

```

---

### Post by YesWeCan on 2011-07-05
> **srs5694 said:**
> This problem is easily fixed by my [FixParts]("http://www.rodsbooks.com/fixparts/") program. FixParts might or might not reassign the partitions' statuses automatically; you might need to fiddle with primary/logical assignments a bit. You can, however, make the current partitions 5 and 6 logicals (which they are) and 1, 2, and 7 primaries (1 and 2 are already primaries, but 7 is currently logical). In other words, you just need to reassign 7 from logical to primary, unless I'm missing something. Read the FixParts Web site for a description of how to use it.
Well, sda5 is the XP OS - it has to be a primary partition, and sda7 is the last partition on the disk so it should be part of the logical group. If you are so expert why are you recommending that sda5 be logical and sda7 be primary?

If the OP actually wants to do this, which I doubt (probably lost the will to live by now :P), the PTs need to be examined expertly so they can be intelligently corrected, by hand. I wouldn't let automated tools anywhere near it.

---

### Post by srs5694 on 2011-07-06
> **YesWeCan said:**
> [quote=srs5694]This problem is easily fixed by my [FixParts]("http://www.rodsbooks.com/fixparts/")  program. FixParts might or might not reassign the partitions' statuses  automatically; you might need to fiddle with primary/logical assignments  a bit. You can, however, make the current partitions 5 and 6 logicals  (which they are) and 1, 2, and 7 primaries (1 and 2 are already  primaries, but 7 is currently logical). In other words, you just need to  reassign 7 from logical to primary, unless I'm missing something. Read  the FixParts Web site for a description of how to use it.Well, sda5 is the XP OS - it has to be a primary partition,[/quote]

Look again:

> **rahulkale]```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x049d049d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    43006005    80774819    18884407+   c  W95 FAT32 (LBA)
/dev/sda2        80774820   118543634    18884407+   c  W95 FAT32 (LBA)
/dev/sda3           16126   156296384    78140129+   f  W95 Ext'd (LBA)
/dev/sda5           16128    13333949     6658911    b  W95 FAT32
/dev/sda6        13334013    43006004    14835996    7  HPFS/NTFS
/dev/sda7       118543699   156296384    18876343    b  W95 FAT32

```[/quote]

Note that /dev/sda1 is marked as bootable. It also contains the Windows boot loader files, according to the Boot Info Script output, and with the Windows boot loader installed in the MBR (also as revealed by Boot Info Script), the boot process is being directed through /dev/sda1. It's conceivable that the bulk of the Windows installation is on /dev/sda5, but that's OK so long as those critical boot files are on a primary partition.

Also, unless I've overlooked something, the computer currently boots Windows XP just fine. Since the current configuration is for /dev/sda5 to be logical and since my suggested change *doesn't alter that assignment,* that change won't alter the bootability of the computer -- at least, not for that reason. (If there were something about /dev/sda7 that required it to be a logical, that would be another matter.)

What /dev/sda7 *does* contain is WUBI files, according to the Boot Info Script. This is essentially irrelevant since, according to post #1, the WUBI installation is currently broken and an attempt is being made to re-install. Thus, we don't need to worry about breaking any OS installation on /dev/sda7.

[quote=YesWeCan]and sda7 is the last partition on the disk so it should be part of the logical group.[/quote]

Although it's conventional to place primary partitions early on the disk and to have an extended partition that reaches from some point to the end of the disk, there's no rule that requires this configuration. I've got at least two disks with primary partitions at the end of the disk and they work just fine. This arrangement is admittedly confusing and I wouldn't recommend creating a configuration this way "from scratch," but that's not the exercise at hand. The goal is to *recover rahulkale's system to a legal state* so that Ubuntu can be re-installed. Converting /dev/sda7 from a logical partition to a primary partition and resizing the extended partition appropritely *will do this* and this is one of the tasks that FixParts was *designed to do.*

> If you are so expert why are you recommending that sda5 be logical and sda7 be primary?

Because I know what I'm doing.

To be sure, there are other ways to reconfigure those partitions said:**
> If the OP actually wants to do this, which I doubt (probably lost the will to live by now :P), the PTs need to be examined expertly so they can be intelligently corrected, by hand. I wouldn't let automated tools anywhere near it.

I am an expert on partition tables, I have examined the data, and I have offered my recommendation. A few months ago, I'd have recommended doing it by rewriting the sfdisk entries, and in fact I wrote a [Web page](http://www.rodsbooks.com/missing-parts/index.html) describing how to do so for a problem that's not quite identical to this one. This approach is difficult to explain to non-experts, though, and it's easy to mess it up -- a simple mis-typed value and you'll be worse off than you were to start. That's why I wrote FixParts; it makes it much easier for non-experts (or those who worry about their ability to handle arithmetic on 10-digit numbers) to solve these sorts of problems.

It's unclear to me what you're offering as a recommendation, beyond examining the data at a lower level -- and I'm not even sure what you mean by that, since as I've said, the only "lower level" you're going to get than an fdisk analysis is using a sector editor, and that's something few people could manage. You've ignored my questions about ways in which you think the fdisk output is likely to be flawed.

That said, I don't recommend proceeding recklessly. My [FixParts Web page](http://www.rodsbooks.com/fixparts/) recommends backing up partition tables before proceeding with rescue operations such as this one, and I'll reiterate that advice here. I can't offer a 100% guarantee that there won't be problems; there could be some issue that's not apparent in the output that's been presented, or I might have overlooked some critical detail. If you do back up your current partition table, though, you should be able to restore it (warts and all) should something go wrong.

---

### Post by rahulkale on 2011-07-06
Guys thanks for the responses to Help me out, but I just noticed one thing that i should have done earlier itself. 

this is my drive info as given: 

```
Partition	"Drive"		Label		Size (GiB)	Type

sda5		D:		MAIN DRIVE	6.35		Logical
sda6		E:		MOVIES		14.15		Logical
sda1		C:		GAME		18.01		Primary
sda2		F:		STUDY DATA	18.01		Primary
sda7		G:		SONG MOVIE	18.00		Logical
```



As Seen from the Table, I know that my system Drive is 

```
sda5		D:		MAIN DRIVE	6.35		Logical
```

_**and NOT**_

```
sda1		C:		GAME		18.01		Primary
```

This is in Response to the folowing text

Logical partitions in Linux are numbered 5 and upwards. In your case sda1 and sda2 are your two primary partitions, sda3 your extended, and sda5, sda6 and sda7 the logical partitions. The main problem is that sda1 and sda2 are "inside" your extended partition, sda3. This is impossible. It would normally have been a fairly easy task to edit the partition table to correct this illegality but for the next problem. You have logical partitions physically either side of the primaries. One or more would have to be converted to primary partitions.

Your Wubi installation is on sda7, your "G:" drive in Windows parlance.Your "C:" drive is formatted FAT32 which is unusual for Windows XP and oddly has the partition label "GAME". Finally, the start sector for the first physical partition is 16126, which is very odd. Normally it would be 63 or 2048. None of these latter points are problematic singly, but add up to a partition layout which needs a thorough rethink and clearout.


If I am not wrong this may help me out

---

### Post by srs5694 on 2011-07-06
Rahulkale,

Your new information doesn't really change anything. Although D: (/dev/sda5) is your "system drive" in Windows, the way the computer boots is via C: (/dev/sda1). That partition probably just has a few key files (the Boot Info Script detected some of them -- boot.ini, ntldr, and NTDETECT.COM) that load the rest of the system from D: (/dev/sda5). That configuration is valid, but a little bit unusual, and I fear it's confused some of the people posting to this thread.

This whole primary/logical thing can be confusing, but there are really only a few rules that govern whether a partition may be primary or logical:


[list]
[*]All logical partitions must be contained within a single extended partition. In other words, when you list the partitions in on-disk order (as you did in your latest poast), there can be no primary partitions sitting in-between your logical partitions. Something (probably the Partition Master software you mentioned) has created an illegal configuration on your disk that violates this fundamental rule.
[*]There must be at least one free sector between each logical partition and the partition that precedes it (or the MBR, if the partition is the first one on the disk). This sector is used to store the logical partition's EBR, which a data structure that defines the logical partition. Currently, free sectors exist before your /dev/sda5, /dev/sda6, and /dev/sda7, but not before your /dev/sda1 or /dev/sda2. Thus, those two partitions, which are currently primary partitions, cannot be converted into logical partitions without resizing them or the partitions that come before them.
[*]A disk can have a maximum of four primary partitions *or* three primary partitions and as many logical partitions as you like, so long as they follow the other rules. Your disk currently has two primary partitions, so you can create one more primary or convert one logical partition into a primary.
[/list]


Given your current setup, the only way I can see to make it legal without resizing or deleting partitions is to convert /dev/sda7 from a logical partition to a primary partition. This can be done easily with FixParts, or with more difficulty with sfdisk. There are probably Windows tools that can do it, but I'm not familiar with them (except for the Windows version of FixParts) so I can't make any specific recommendations about them. Given the illegal configuration, resizing partitions is inadvisable unless you're positive that the tool you're using can do it safely. Thus, I can see just two courses of action that are reasonably safe:


[list]
[*]Back up everything, wipe the disk clean, and restore to a new set of partitions. This is tedious and time-consuming, but you can get a less confusing configuration out of it.
[*]Convert /dev/sda7 from logical to primary. As noted in an earlier message, backing up the partition table before such an operation is advisable.
[/list]

---

### Post by psusi on 2011-07-06
You know I think windows will boot just fine out of a logical partition -- if you use grub to chain load it.  AFAIK, the only reason windows can't boot from a logical partition normally is because it does not install any boot code to the EBR.  Chain loading the PBR with grub eliminates that problem.  It would be an interesting experiment to try.

---

### Post by oldfred on 2011-07-06
I think both Herman and meierfra. have posted ways to make XP boot from a logical. Windows of course does not support it. meierfra. likes the lilo boot loader to boot windows as it does not have the logic to restrict booting to just primary partitions (as windows does), so it will boot windows directly from the MBR to a logical partition.

Way to boot windows in extended logical partition with lilo's MBR post#5
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)

---

### Post by srs5694 on 2011-07-06
Given that Windows *is already booting correctly* on rahulkale's disk, I don't think there's a need to find a solution to the problem of getting Windows to boot from a logical partition, unless the solution to the real problem (the illegal overlap of the extended partition with two primaries in order to store logical partitions on both sides of the two primaries) alters the identities of /dev/sda1 and /dev/sda5, which are the two partitions that are currently involved in booting Windows. Of course, if I've missed something and Windows is *not* currently booting correctly, somebody please correct me.

---

### Post by rahulkale on 2011-07-10
Sorry for a Late Reply, since I had some travelling to do...

I am posting the output of the following code, required to check the partition tables...

first is the output of 
 sudo fdisk -lu, i had posted it earlier but just for refrence....

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x049d049d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    43006005    80774819    18884407+   c  W95 FAT32 (LBA)
/dev/sda2        80774820   118543634    18884407+   c  W95 FAT32 (LBA)
/dev/sda3           16126   156296384    78140129+   f  W95 Ext'd (LBA)
/dev/sda5           16128    13333949     6658911    b  W95 FAT32
/dev/sda6        13334013    43006004    14835996    7  HPFS/NTFS
/dev/sda7       118543699   156296384    18876343    b  W95 FAT32
```


Following is the output of 

sudo sfdisk -d --force /dev/sdaN   N = 1,2,3,5,6,7.... respectively


```
ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda1
# partition table of /dev/sda1
unit: sectors

/dev/sda1p1 : start=1869771365, size=168689522, Id=69
/dev/sda1p2 : start=1701519481, size=1869881465, Id=73
/dev/sda1p3 : start=     2573, size=        0, Id=74
/dev/sda1p4 : start=2885681152, size=    52415, Id= 0

---------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda2
# partition table of /dev/sda2
unit: sectors

/dev/sda2p1 : start=778135908, size=1141509631, Id=72
/dev/sda2p2 : start=168689522, size=1936028240, Id=65
/dev/sda2p3 : start=1869881465, size=1936028192, Id=79
/dev/sda2p4 : start=2885681152, size=    55499, Id= d

---------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda3
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
lseek: Invalid argument

sfdisk: seek error on /dev/sda3 - cannot seek to 13317824
# partition table of /dev/sda3
unit: sectors

/dev/sda3p1 : start=        2, size= 13317822, Id= b
/dev/sda3p2 : start= 13317824, size= 29672055, Id= 5
/dev/sda3p3 : start=        0, size=        0, Id= 0
/dev/sda3p4 : start=        0, size=        0, Id= 0

---------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda5
# partition table of /dev/sda5
unit: sectors

/dev/sda5p1 : start=778135908, size=1141509631, Id=72
/dev/sda5p2 : start=168689522, size=1936028240, Id=65
/dev/sda5p3 : start=1869881465, size=1936028192, Id=79
/dev/sda5p4 : start=2885681152, size=    55499, Id= d

---------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda6
# partition table of /dev/sda6
unit: sectors

/dev/sda6p1 : start=218129509, size=1701990410, Id=72
/dev/sda6p2 : start=729050177, size=543974724, Id=74
/dev/sda6p3 : start=168653938, size=        0, Id=65
/dev/sda6p4 : start=2692939776, size=    51635, Id= 0

---------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda7
# partition table of /dev/sda7
unit: sectors

/dev/sda7p1 : start=778135908, size=1141509631, Id=72
/dev/sda7p2 : start=168689522, size=1936028240, Id=65
/dev/sda7p3 : start=1869881465, size=1936028192, Id=79
/dev/sda7p4 : start=2885681152, size=    55499, Id= d
```

---

### Post by rahulkale on 2011-07-10
Sorry for a Late Reply, since I had some travelling to do...

I am posting the output of the following code, required to check the partition tables...

first is the output of 
 sudo fdisk -lu, i had posted it earlier but just for refrence....

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x049d049d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    43006005    80774819    18884407+   c  W95 FAT32 (LBA)
/dev/sda2        80774820   118543634    18884407+   c  W95 FAT32 (LBA)
/dev/sda3           16126   156296384    78140129+   f  W95 Ext'd (LBA)
/dev/sda5           16128    13333949     6658911    b  W95 FAT32
/dev/sda6        13334013    43006004    14835996    7  HPFS/NTFS
/dev/sda7       118543699   156296384    18876343    b  W95 FAT32
```


Following is the output of 

sudo sfdisk -d --force /dev/sdaN   N = 1,2,3,5,6,7.... respectively


```
ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda1
# partition table of /dev/sda1
unit: sectors

/dev/sda1p1 : start=1869771365, size=168689522, Id=69
/dev/sda1p2 : start=1701519481, size=1869881465, Id=73
/dev/sda1p3 : start=     2573, size=        0, Id=74
/dev/sda1p4 : start=2885681152, size=    52415, Id= 0

---------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda2
# partition table of /dev/sda2
unit: sectors

/dev/sda2p1 : start=778135908, size=1141509631, Id=72
/dev/sda2p2 : start=168689522, size=1936028240, Id=65
/dev/sda2p3 : start=1869881465, size=1936028192, Id=79
/dev/sda2p4 : start=2885681152, size=    55499, Id= d

---------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda3
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
lseek: Invalid argument

sfdisk: seek error on /dev/sda3 - cannot seek to 13317824
# partition table of /dev/sda3
unit: sectors

/dev/sda3p1 : start=        2, size= 13317822, Id= b
/dev/sda3p2 : start= 13317824, size= 29672055, Id= 5
/dev/sda3p3 : start=        0, size=        0, Id= 0
/dev/sda3p4 : start=        0, size=        0, Id= 0

---------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda5
# partition table of /dev/sda5
unit: sectors

/dev/sda5p1 : start=778135908, size=1141509631, Id=72
/dev/sda5p2 : start=168689522, size=1936028240, Id=65
/dev/sda5p3 : start=1869881465, size=1936028192, Id=79
/dev/sda5p4 : start=2885681152, size=    55499, Id= d

---------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda6
# partition table of /dev/sda6
unit: sectors

/dev/sda6p1 : start=218129509, size=1701990410, Id=72
/dev/sda6p2 : start=729050177, size=543974724, Id=74
/dev/sda6p3 : start=168653938, size=        0, Id=65
/dev/sda6p4 : start=2692939776, size=    51635, Id= 0

---------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo sfdisk -d --force /dev/sda7
# partition table of /dev/sda7
unit: sectors

/dev/sda7p1 : start=778135908, size=1141509631, Id=72
/dev/sda7p2 : start=168689522, size=1936028240, Id=65
/dev/sda7p3 : start=1869881465, size=1936028192, Id=79
/dev/sda7p4 : start=2885681152, size=    55499, Id= d
```

---

### Post by YesWeCan on 2011-07-10
Hi rahulkale, would you mind also posting the outputs of:
sudo dd if=/dev/sda bs=512 count=1  | hexdump -C
sudo dd if=/dev/sda bs=512 count=1 skip=13333950 | hexdump -C

---

### Post by YesWeCan on 2011-07-10
I think your disk contents look like this:
```
partition  allocation   start sector     end sector     total sectors    label        PT contents               other
              MBR                0              0                 1                   EPBR 1,p3 (active),p4 
             unused              1             62                62   
             unused             63          16125             16063   
             EPBR 1          16126          16126                 1                   p1, EPBR 2 
             unused          16127          16127                 1   
     p1      FAT32           16128       13333949          13317822     MAIN DRIVE                             XP OS
             EPBR 2       13333950       13333950                 1                   p2, EPBR 3 
             unused       13333951       13334012                62   
     p2      NTFS         13334013       43006004          29671992     MOVIES  
     p3      FAT32        43006005       80774819          37768815     GAME                                   Boot.ini, Wubi
     p4      FAT32        80774820      118543634          37768815     STUDY DATA  
             EPBR 3      118543635      118543635                 1                   p5 
             unused      118543636      118543698                63   
     p5      FAT32       118543699      156296384          37752686     SONG MOVIE                             Wubi boot files
             unused      156296385      156301487              5103   
```The sector address of EPBR 3 is a guess...need to check against the dd output of EPBR 2.

---

### Post by YesWeCan on 2011-07-10
So there are many ways to skin a cat, this is what I would consider doing:

Normally, your primary partitions come first followed by logical partitions. What you have is 1 primary (extended), 2 logicals, 2 primaries, 1 logical. This is probably why GParted is upset and is refusing to function. So I would want to get things into a normal ordering. If I could wave a wand I'd make p1, p2, p3 primary and the fourth slot Extended with p4 and p5 logical.

BUT, every logical partition has to have a gap of at least 1 sector in front of it (FYI: I think linux normally uses 2 and it ought to be 62 to mimick the MBR cylinder) for the EPBR. That means p3 and p4 have to be primary at the moment. p3 is fine but I'd want p4 to be logical. So a gap must be made.

Once a gap is made, I'd set up p1, p2, p3 as primaries and p4 & p5 logical in an extended partition.  After this, GParted should come back to life and you can start resizing things to make room for a Ubuntu install.

So how do you do this?
a) This is probably where srs5694 shouts "Use only my tool!" and if his tool will do this then that is one method.

b) Find a partitioner that doesn't care about the positions of the logical partitions and will let you move things around and reassign from logical to primary and vice versa.

c) You can hack it to get it working by stealing a sector from the end of p3. This is probably safe as I doubt the p3 partition is full to the brim. But you should first back up any vital data, particularly in GAMES drive. Then:
- alter the MBR partition table to have entries for p1, p2, p3 (minus 1 sector) and an extended partition starting at 80774819.
- add the new EPBR at sector 80774819 (pointing to p4 and EPBR 3).

d) Like c) but back up p4 STUDY DATA and then remove its entry from the MBR PT, then you only need EPBR 3 so no need to steal from p3. Restore STUDY DATA later. For that matter, if you can back up SONG MOVIE too then that makes it much simpler as no extended partition is needed at all.

If you wish to try c) or d) I'll test it in VirtualBox first and then give you the detailed instructions.

---

### Post by srs5694 on 2011-07-10
> **YesWeCan said:**
> Normally, your primary partitions come first followed by logical partitions.

This is conventionally true, but it's not a *necessary* feature, as I've said before. Attempting to get the disk to conform to this unnecessary rule just complicates the process of recovering data.

> What you have is 1 primary (extended), 2 logicals, 2 primaries, 1 logical. This is probably why GParted is upset and is refusing to function.

Essentially, yes. Put another way, and the extended partition (which houses the logical partitions) overlaps with the two primary partitions. I've stated this before in this thread.

> So I would want to get things into a normal ordering. If I could wave a wand I'd make p1, p2, p3 primary and the fourth slot Extended with p4 and p5 logical.

BUT, every logical partition has to have a gap of at least 1 sector in front of it (FYI: I think linux normally uses 2 and it ought to be 62 to mimick the MBR cylinder) for the EPBR. That means p3 and p4 have to be primary at the moment. p3 is fine but I'd want p4 to be logical. So a gap must be made.

Once a gap is made, I'd set up p1, p2, p3 as primaries and p4 & p5 logical in an extended partition.  After this, GParted should come back to life and you can start resizing things to make room for a Ubuntu install.

A much simpler solution is to convert /dev/sda7 (what you're calling "p5") into a primary partition. This is perfectly valid, it's the least disruptive solution, and it's the only solution I can see that doesn't involve resizing partitions (which is risky at best under the current cirucmstances).

> So how do you do this?
a) This is probably where srs5694 shouts "Use only my tool!" and if his tool will do this then that is one method.

I've *never* said "use only my tool!" I have recommended FixParts because it is, to the best of my knowledge, the only Linux tool that's designed for reassigning primary/logical status or for fixing the sort of problems the OP has. There are Windows tools that can do this, but I know little enough about them that I can't make any specific recommendations. It's also possible to do this by manually editing files in sfdisk, by careful use of fdisk, or even by using a sector editor; however, these approaches are all more difficult than using FixParts and they all have a greater chance of user error causing serious problems.

> b) Find a partitioner that doesn't care about the positions of the logical partitions and will let you move things around and reassign from logical to primary and vice versa.

You mean, like FixParts? (Except that it *does* care about the rules, so it only lets you set up legal primary/logical assignments -- but since the goal is to create a legal configuration, this isn't a problem.)

> c) You can hack it to get it working by stealing a sector from the end of p3. This is probably safe as I doubt the p3 partition is full to the brim. But you should first back up any vital data, particularly in GAMES drive. Then:
- alter the MBR partition table to have entries for p1, p2, p3 (minus 1 sector) and an extended partition starting at 80774819.
- add the new EPBR at sector 80774819 (pointing to p4 and EPBR 3).

The way you're describing it sounds like you're recommending use of a disk sector editor to repair the problem, although perhaps you're thinking of doing it with sfdisk. Using a sector editor is something for I wouldn't recommend except for a disk expert (who wouldn't be posting with this problem to begin with), and even with sfdisk, there's a significant risk of getting it badly wrong.

Although your assumption that /dev/sda1 (what you're calling "p3") is not "full to the brim" is probably correct, that *is* an assumption. I wouldn't want to lose some critical piece of data because of a false assumption.

All told, this seems like an inadvisable solution to me.

> d) Like c) but back up p4 STUDY DATA and then remove its entry from the MBR PT, then you only need EPBR 3 so no need to steal from p3. Restore STUDY DATA later. For that matter, if you can back up SONG MOVIE too then that makes it much simpler as no extended partition is needed at all.

Removing and then restoring partitions is certainly an option. Personally, if I were to go this route, I'd be tempted to back up the whole disk and restore everything with a more conventional and optimized partition layout.

---

### Post by srs5694 on 2011-07-10
> **rahulkale said:**
> Following is the output of 

sudo sfdisk -d --force /dev/sdaN   N = 1,2,3,5,6,7.... respectively

I realize you're just posting what YesWeCan asked you to post, but this information is mostly useless. The sfdisk program is a partitioning tool that should be called on an entire disk, such as /dev/sda or /dev/sdb. By calling it on a partition, you're forcing it to interpret the partition's contents as if it were a partition table. The result is gibberish. There is one partial exception, though, and that is /dev/sda3. This is an extended partition, so it begins with an EBR, which is a data structure related to an MBR. The data in /dev/sda3 therefore do have meaning, although you get almost nothing from this entry that's not already present in the main fdisk output, just the location of the next EBR in the chain -- but *its* data already appear in the sfdisk output.

[quote=YesWeCan]If I could wave a wand I'd make p1, p2, p3 primary and the fourth slot Extended with p4 and p5 logical.[/quote]

Even aside from the difficulty of creating that layout, one possible complication is that /dev/sda5 (what you're calling "p1"), which is currently logical, contains the main Windows installation. It currently boots fine because the Windows boot loader files are on /dev/sda1 (what you call "p3"). This is an unusual, but valid, configuration. I don't know offhand how Windows will react if its logical system partition is suddenly transformed into a primary partition. Perhaps it'll be OK with that, but perhaps not. I'd want to consult an expert on how Windows boots before making such a change.

Note that converting /dev/sda7 to a primary partition does not alter either /dev/sda1 or /dev/sda5, so this particular risk is sidestepped if this solution is used.

---

### Post by YesWeCan on 2011-07-10
@srs5694:
Note that what the OP wants is to be able to install Ubuntu to his disk without conflicts with Windows. So whatever solution you prescribe has to be one that both the Ubuntu installer can work with and GParted and other standard Ubuntu tools can function with so he can easily adjust partitions now and in the future. Windows also needs to be happy now and in the future.

I believe what I am describing will achieve that. If your solution will achieve that more effectively then great.

Several pages ago you arrived announcing "This problem is easily fixed by my FixParts program." AFAIK the OP has not chosen to or has not been able to implement that yet. So maybe it isn't so easy? That's not my fault. Maybe you need to be clearer about what you wish him to do and why it will give a satisfactory result. Why not focus on that?

Now, don't reply to me! I'm not important, I am just a penguin. Address the OP and help get this problem to "solved" status. :)

---

### Post by srs5694 on 2011-07-10
> **YesWeCan said:**
> @srs5694:
Note that what the OP wants is to be able to install Ubuntu to his disk without conflicts with Windows. So whatever solution you prescribe has to be one that both the Ubuntu installer can work with and GParted and other standard Ubuntu tools can function with so he can easily adjust partitions now and in the future. Windows also needs to be happy now and in the future.

I believe what I am describing will achieve that. If your solution will achieve that more effectively then great.

The first step to this goal is to get a valid partition table. Once the partition table is valid (no matter what solution is chosen), partitions can be resized and/or moved to make room for Ubuntu. It might even be desirable to make further primary/logical changes at that point. Such changes become safer when you can rely on resizing tools (such as in GParted or the Windows partitioner) to resize partitions to create the gaps between partitions that are necessary for logical partitions.

One complication to this ultimate goal is in the layout of the current partitions, which has the partition with the Windows boot loader files (/dev/sda1) in the middle of the disk. This partition must be primary -- at least, when using conventional Windows booting methods. (I've heard of hacks to enable Windows to boot more directly from logical partitions, but I don't know much about them, and I don't know if they apply to Windows XP or just to more recent Windows versions.) With most of Windows stored on a logical partition (/dev/sda5) that comes before the primary boot partition, this begs the question of how Windows would respond to that partition becoming primary, should this be desirable from a partitioning perspective. I honestly don't know the answer to that question. I can't recommend that rahulkale test it unless he's willing to re-install Windows should the test fail badly enough.

In other words, the current partition table is not an easy one for Linux installation, no matter what solution is chosen. It *can* be done, no matter what solution is chosen for the first problem, but it may involve resizing at least one partition and probably either moving several of them or taking a gamble about what happens if /dev/sda5 is converted to a primary.

It might be helpful to know from what partition(s) rahulkale intends to take space to create Linux partition(s), or if rahulkale can completely convert any partition into a Linux partition. If possible, such a complete conversion to Linux might well simplify the installation task, since less repartitioning would be required. If it's possible to completely delete any partition(s), that might simplify matters, too.

---

### Post by rahulkale on 2011-07-11
@srs5694:


with refrence to 

> It might be helpful to know from what partition(s) rahulkale intends to take space to create Linux partition(s), or if rahulkale can completely convert any partition into a Linux partition. If possible, such a complete conversion to Linux might well simplify the installation task, since less repartitioning would be required. If it's possible to completely delete any partition(s), that might simplify matters, too.

This is my partiton table:

```
Partition	"Drive"		Label		Size (GiB)	Type

sda5		D:		MAIN DRIVE	6.35		Logical
sda6		E:		MOVIES		14.15		Logical
sda1		C:		GAME		18.01		Primary
sda2		F:		STUDY DATA	18.01		Primary
sda7		G:		SONG MOVIE	18.00		Logical
```



Since my _G: Drive_ is one where i Install all the softwares, hence i cannot dare to move it...

The simplest I can possibly do is to move and backup the data from E: Drive...

If needed i can also partition the E: Drive.
Will I be able to use E: drive in windows Xp because I know that we neew the "extd" Partition for Linux. So will it be readable in Windows Xp??? 

I am ready to do as required...

---

### Post by srs5694 on 2011-07-11
If you want to create new partitions for Linux, and if you go with my recommendation to turn /dev/sda7 [noparse](G:)[/noparse] into a primary partition, then it will be relatively straightforward after that to shrink /dev/sda6 [noparse](E:)[/noparse] to make room for as many logical Linux partitions as you want. (The default is two -- root (/) and swap; but many people, myself included, generally recommend using a separate /home partition. OTOH, it sounds like yours will be a fairly small installation, so separating /home might not be advisable.) If you shrink /dev/sda6 from its end, which is the safest and quickest way to do that sort of thing, neither its partition number nor that of /dev/sda5 will change, so Windows shouldn't be bothered by this.

Bear in mind, though, that any partition resizing operation poses some risk. (It sounds like a partition resizing or splitting operation using Partition Master in Windows may have created this problem to begin with.) If at all possible, you should back up any partition before resizing it. The risk is greatest if you change the partition's start point, so for best safety you should shrink by moving the end point if that's practical.

---

### Post by rahulkale on 2011-07-18
Thanks Guys.. I decided to Backup and repartition my HardDisk...

I have Created 3 partions "/boot" "/swap" "/(root)"

well i just cant get a option to select ubuntu or Xp, just boots automatically into Xp.. please help

here is the link to the post: 

[http://ubuntuforums.org/showthread.php?t=1806831]("http://ubuntuforums.org/showthread.php?t=1806831")

---

