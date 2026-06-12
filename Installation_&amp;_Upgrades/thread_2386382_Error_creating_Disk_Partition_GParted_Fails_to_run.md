---
title: "Error creating Disk Partition: GParted Fails to run"
date: 2018-03-05
forum: Installation &amp; Upgrades
---

### Post by anspectrum on 2018-03-05
Hello,

Ive HP laptop with a traditional HDD and an SSD. The SSD is recent addition to hardware, earlier I had just HDD and I was using it with Ubuntu 16.04.1 (32-bit).

Now Ive installed Ubuntu 16.04.4 (64-bit) and Windows-7 (64-bit) in dual boot mode on SSD and things are working fine. I intend to use HDD as a data storage only with no OS on it.

The problem is that I've left over space ~190GB on SSD that I am unable to use due to failing in creating partition. Somehow my HDD does not let the GParted run and makes it crash. I've tried using "parted" as well to create partition (logical)  in unallocated space but it does not let me use the correct bytes.

Here is some of the relevant outputs:

```
sudo fdisk -l
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa11cac6d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 860162047 860160000 410.2G  7 HPFS/NTFS/exFAT
/dev/sda2       860164094 976771071 116606978  55.6G  5 Extended
/dev/sda3               0         0         0     0B  0 Empty
/dev/sda5       860164096 968959999 108795904  51.9G 83 Linux
/dev/sda6       968960000 976771071   7811072   3.7G 82 Linux swap / Solaris

[COLOR=#ff0000]Partition 2 does not start on physical sector boundary.                    ///// I think this is causing the issue for GParted to fail[/COLOR]
Partition table entries are not in disk order.


Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd7b0c43e

Device     Boot    Start       End  Sectors  Size Id Type
/dev/sdb1           2048  48828415 48826368 23.3G 83 Linux
/dev/sdb2       48830462  56641535  7811074  3.7G  5 Extended
/dev/sdb3  *    56641536  56846335   204800  100M  7 HPFS/NTFS/exFAT
/dev/sdb4       56846336 128321535 71475200 34.1G  7 HPFS/NTFS/exFAT
/dev/sdb5       48830464  56641535  7811072  3.7G 82 Linux swap / Solaris

Partition table entries are not in disk order.
```

And parted output:

```
sudo parted /dev/sdb
GNU Parted 3.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print free                                                       
Model: ATA NT-256 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
        32.3kB  1049kB  1016kB            Free Space
 1      1049kB  25.0GB  25.0GB  primary   ext4
        25.0GB  25.0GB  1048kB            Free Space
 2      25.0GB  29.0GB  3999MB  extended
 5      25.0GB  29.0GB  3999MB  logical   linux-swap(v1)
 3      29.0GB  29.1GB  105MB   primary   ntfs            boot
 4      29.1GB  65.7GB  36.6GB  primary   ntfs
        65.7GB  256GB   190GB             Free Space                           //// Free Space
```

One solution that I can think of as a last resort is backup all my data  on HDD and format it from Windows. Then come back to Ubuntu and try to  use Gparted to see if it works. But that would be last resort.

Please suggest how can I create partition to use that unallocated space.

---

### Post by oldfred on 2018-03-05
I think the issue is sdb3's partition is inside the extended partition. That cannot be as all logical partitions inside an extened must start with sda5 or higher.
And sda1 thru 4 must be primary partitions with extended partition as any one of the primary partitions.

That extended partition does not start on sector boundary is a standard warning that should be ignored. You do not directly write into an extended partition, but into the logical partitions inside it. And with new 4K drives you need the partitions your write into on 4K boundary. But you have 515 drives anyway.

You may be able to use fdisk and w command to write fixes.
Or perhaps fixparts.

       sudo fdisk /dev/sda
Press "w". That rewrites the partition table.

---

### Post by anspectrum on 2018-03-05
Thanks @oldfred, given your extensive experience I was waiting for your suggestion :)

I am not sure I quite understood what you are implying. But here is the output from fixparts:

```
sudo fixparts /dev/sdb
FixParts 1.0.1

Loading MBR data from /dev/sdb

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 500118192 sectors (238.5 GiB)
MBR disk identifier: 0xD7B0C43E
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                  2048     48828415   primary     Y        Y      0x83
   3      *       56641536     56846335   primary              Y      0x07
   4              56846336    128321535   primary              Y      0x07
   5              48830464     56641535   logical     Y        Y      0x82

```

When I exited the menu I did write the changes to the MBR but I dont think it changed anything becuase when I went to "disks" utility from the Menu and tried to cretae partition it says that cant create anymore partition because there are already four primary partition, although we can see there are only three :D

[https://ufile.io/nioch](https://ufile.io/nioch)

P.S: I had given this suggestion earlier as well that editing options are different when you are posting a new thread as compared to when you are replying to a thread. In replying to a thread there are very less options which ofc does not make much sense. Like this time I can not upload the image. Please forward my suggestion to the relevant platform.

---

### Post by oldfred on 2018-03-05
fixparts did not show logical partitions?
Perhaps it converted all the partitions to primary?
If you lost partitions that you need we need to fix that first.

Post this:
sudo fdisk -lu

I normally use quick reply. 
But all the options as in the Forum's Advanced editor - Go Advanced. And then you can use paperclip icon to attach screenshots.
But if output from terminal better to just copy & paste and use code tags or # in Advanced editor. I usually just use quote icon in Quick Reply and manually change quote to code.

---

### Post by anspectrum on 2018-03-05
I was kinda impatient and had deduced that probably primary partitions should be in sequence followed by logical partitions. So I removed Swap , Windows Reserved, Windows Partitions and recreated them in order. Now my MBR looks like this
```

sudo fdisk -lu /dev/sdb
Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd7b0c43e

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1            2048  48828415  48826368 23.3G 83 Linux
/dev/sdb2  *     48828416  49033215    204800  100M  7 HPFS/NTFS/exFAT
/dev/sdb3        49033216 120508415  71475200 34.1G  7 HPFS/NTFS/exFAT
/dev/sdb4       120510463 491604213 371093751  177G  f W95 Ext'd (LBA)
/dev/sdb5       120510464 491604213 371093750  177G  7 HPFS/NTFS/exFAT
```

And parted output
```

sudo parted /dev/sdb
GNU Parted 3.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print free                                                       
Model: ATA NT-256 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
        32.3kB  1049kB  1016kB            Free Space
 1      1049kB  25.0GB  25.0GB  primary   ext4
 2      25.0GB  25.1GB  105MB   primary   ntfs         boot
 3      25.1GB  61.7GB  36.6GB  primary   ntfs
        61.7GB  61.7GB  1048kB            Free Space
 4      61.7GB  252GB   190GB   extended               lba
 5      61.7GB  252GB   190GB   logical
        252GB   256GB   4359MB            Free Space
```

Now problem comes again to the same point how to create swap partition of this remaining 4GB Free space :mad: . I don't wanna create swap on HDD.

Also have a look at this:
```

(parted) unit                                                             
Unit?  [compact]? s                                                       
(parted)                                                                  
(parted)                                                                  
(parted) print free                                                       
Model: ATA NT-256 (scsi)
Disk /dev/sdb: 500118192s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system  Flags
        63s         2047s       1985s                 Free Space
 1      2048s       48828415s   48826368s   primary   ext4
 2      48828416s   49033215s   204800s     primary   ntfs         boot
 3      49033216s   120508415s  71475200s   primary   ntfs
        120508416s  120510462s  2047s                 Free Space
 4      120510463s  491604213s  371093751s  extended               lba
 5      120510464s  491604213s  371093750s  logical
        491604214s  500118191s  8513978s              Free Space
```


And when I try to create swap

```
(parted) unit s                                                           
(parted) mkpart                                                        
Partition type?  [logical]?                                               
File system type?  [ext2]? linux-swap                                     
Start? 491604150
End? 500118191                                                            
Error: Can't have overlapping partitions.
Ignore/Cancel? c                                                          
(parted) 
```



(Thanks for the tip of Advanced Editing)

---

### Post by oldfred on 2018-03-05
Your start is before the end of sda5.
You have to have at least one sector between partitions.
And start must be after end (+1) of previous sector.

 491604213s  
491604150 needs to be 491604215?

---

### Post by anspectrum on 2018-03-05
Oh, I kinda stumbled upon the solution. I used cfdisk utility, its menu based. I deleted the Extended logical partitions. And then create one Extended Partition. Then I sliced that extended partition into two pieces, one for swap and other one for storage. (My bad :D). Now my MBR looks like this:

```
sudo fdisk -l /dev/sdb
Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd7b0c43e

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1            2048  48828415  48826368 23.3G 83 Linux
/dev/sdb2  *     48828416  49033215    204800  100M  7 HPFS/NTFS/exFAT
/dev/sdb3        49033216 120508415  71475200 34.1G  7 HPFS/NTFS/exFAT
/dev/sdb4       120508416 500118191 379609776  181G  5 Extended
/dev/sdb5       120510464 491706367 371195904  177G  7 HPFS/NTFS/exFAT
/dev/sdb6       491708416 500118191   8409776    4G 82 Linux swap / Solaris
```

And 

```
sudo parted /dev/sdb
GNU Parted 3.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA NT-256 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  25.0GB  25.0GB  primary   ext4
 2      25.0GB  25.1GB  105MB   primary   ntfs         boot
 3      25.1GB  61.7GB  36.6GB  primary   ntfs
 4      61.7GB  256GB   194GB   extended
 5      61.7GB  252GB   190GB   logical   ntfs
 6      252GB   256GB   4306MB  logical
```

Suddenly world seems to be a better place. xD

Thank you for the prompt responses oldfred, you have always been very helpful.

---

### Post by oldfred on 2018-03-05
Glad to offer what help I can, but seems like you solved most of it yourself. :)

---

