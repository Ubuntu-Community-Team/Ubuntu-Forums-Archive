---
title: "problem with gparted"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by chpnp on 2014-05-31
Hello All, 

I have happily run this 12.04 system for 18 months and now want to do some partitions update on my secondary disk:
Gparted seemlingly never returns when invoked from command line (it says "looking for partitions on /dev/sdb and i can see the line going back and forth between right and left, at the bootom of the screen but that is all)
Any hint ?
Thanks
Christophe 
[EDIT it did return but seemed to taked forever maybe 10 minutes or more.... what is wrong ?]

Disk detail
$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00029a22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       203165696  3907028991  1851931648    5  Extended
/dev/sdb2            2048    61763583    30880768    7  HPFS/NTFS/exFAT
/dev/sdb5       203167744   818571263   307701760    7  HPFS/NTFS/exFAT
/dev/sdb6      2441883648  3907028991   732572672    7  HPFS/NTFS/exFAT
/dev/sdb7       818573312   839057407    10242048    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order
 $

---

### Post by TheFu on 2014-05-31
Slow access to drives means
a) poor connection - check the USB cable.
b) data corruption - run file system checking tools on the disk/partition (use Windows tools for Windows file systems!)
c) failing drive hardware - BACKUP!!!!!!!   ASAP!!!!!!
d) failing power - could be a PSU, brick, cable going bad.

Could be 1 or more of those issues or something I haven't though of.

---

### Post by LastDino on 2014-05-31
Just to eliminate the software end of suspecion, try to use live boot and use Gparted there and see if the trend is same.

---

### Post by gedakc on 2014-05-31
If the drive contains FAT16, FAT32, or NTFS file systems that are heavily fragmented, then it can take GParted an inordinate amount of time to scan the fragments to determine the space in use.  To prevent this problem, defragment the FAT16, FAT32, and NTFS file systems prior to using GParted.  A side benefit of defragmenting is that you should see improved access performance.

---

### Post by chpnp on 2014-06-03
Thanks all for the answers
gparted run from a (slitaz) live boot showed the same issues
The fragmentation issue might be it. More precisely I use backintime for my backups to that disk so it could well be the reason since that creates thousands of link ... 
I may just reconsider the way I use backintime (probably use a loop file inside the disk)
I am guessing everything is "normal" though I would have thought the read ahead feature of the disk to be more efficient at saving IOs...

---

### Post by TheFu on 2014-06-03
I thought that Back-In-Time required a Linux file system for the backup area so that hardlinking works in a POSIX way. Didn't think NTFS/FAT supported that.  Plus any permissions, group, owner would be lost in the backup areas. Not good.

So, if you think lots of links is the issue, **df -i** will show the inodes on a file system.

---

### Post by mike_f on 2014-06-04
To the OP,
I'm having a similar issue with gparted / parted and have been researching it. I first discovered it when trying (unsuccessfully) to install Xubuntu 14.04 and Mint 17.

So far, I've found that most but not all distros using parted 2.3 have similar symptoms - gparted scans 'forever' and parted (the underlying program) reports something different than expected (usually one big partition). Strangely, my Linux Mint 13 install with the same parted version detects my partitions properly. fdisk -l does not show any overlapping partitions or anything else suspicious.

Everything I've tried so far with parted 3.1 (parted magic 2012, puppy 5.7, tinycore) works OK. 

I can't duplicate the symptom in virtualbox so it may be a combo issue with a system BIOS, parted and ??

FYI my disk layout reported by parted (Linux Mint 13) is:
[FONT=Courier New]
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA SAMSUNG HD502HI (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**
Number  Start      End        Size       Type        File system     Flags
 1          32.3kB   538MB    538MB    primary    fat32             boot, lba
 2          538MB    2688MB  2150MB  primary    ext4
 3          2688MB  24.4GB   21.7GB   primary    ntfs               hidden
 4          24.4GB   500GB    476GB    extended                      lba
 5          24.4GB   209GB    185GB    logical      ntfs
 6          209GB    318GB    109GB    logical      ntfs
 7          318GB    463GB    145GB    logical      ntfs
 8          463GB    479GB    15.4GB   logical      ext4
 9          479GB    496GB    17.3GB   logical      ext4
10         496GB    500GB    4335MB   logical      linux-swap(v1)
[/FONT]

No, the 'hail mary' suggestion of defragging NTFS and FAT partitions did not make any difference for me.

IMO something in the OS environment that changed since 12.04 is the likely cause, but we haven't narrowed it down yet. :( I hope to report back ....

EDIT: under LM17 parted 2.3 reports the disk with **partition table: LOOP** ....... wth?
EDIT2: after backing up data, running fixparts, some minor partition resizing from LM13 parted the issue Still Remains. 
Also checked LM17 and Xubuntu 14.04 on another multiboot computer, no gparted problem! 
I'm not ruling out a bug with **this version of parted 2.3** yet, but the partition table of my 'regular use' computer may have some very subtle issue not liked by parted. I may have to live with it until a large hard drive is available to migrate to. Arrgh. Any other suggestions or ideas welcome.

---

### Post by mike_f on 2014-06-15
**Update** - finally **resolved** the mysterious partition table issue by running the **testdisk** utility *twice*. Testdisk did not produce any error messages and showed me the partitions as expected. After I wrote out the [non-existant] changes gparted would then work. During the whole investigation I did get some strange libparted errors on occasion but I did not record them - I suspect that there is some unusual condition that it doesn't anticipate. Oh, well.

Testdisk - highly recommended!

---

