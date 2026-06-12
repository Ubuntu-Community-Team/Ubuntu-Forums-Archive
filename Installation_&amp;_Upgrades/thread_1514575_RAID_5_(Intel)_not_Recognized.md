---
title: "RAID 5 (Intel) not Recognized"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by moravia on 2010-06-21
I have a system with:
 - 1 SSD "boot" drive
 - 3 HDDs in RAID 5

I created my RAID 5 set in BIOS
 - P6X58D motherboard/Intel Software RAID
 - Looks and works fine in Windows 7 (Ultimate) [B]64-bit

[/B]I installed Ubuntu 10.04 using **wubi**
 - both Windows 7 and Ubuntu systems are on the SSD

_THE PROBLEM_[B]
Ubuntu does not appear to recognize my RAID 5 set[/B]
 - when it loads I see a "/dev/sd_ 10 failed" error (sd_=sda, sdb or sdc) along with "no such file or directory"
 - I can see my 3 HDDs in 'Disk Utility,' but the space/partition information is incorrect
 - I reinstalled all packages related to RAID (dmraid, etc.), but none of it helped

Any suggestions are much appreciated!

Thanks,

~Amanda

---

### Post by dino99 on 2010-06-21
[http://www.google.fr/search?as_q=raid%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=raid%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by moravia on 2010-06-21
dino99,

The first and several other google results which you linked are unresolved/unrelated  issues.  After reading through them I am still not entirely clear I understand... 

As far as I can see, this:

[http://swiss.ubuntuforums.org/showthread.php?t=1497230](http://swiss.ubuntuforums.org/showthread.php?t=1497230)

is the closest replication of my issue with a solution, but does this mean that there is no way for me to fix this issue without installing a different version?  I was hoping that i could resolve it somehow from within the **wubi** installation.

Thanks,

~Amanda

---

### Post by ronparent on 2010-06-22
For a short list of dmraid command parameters type in a terminal:  dmraid --help (which you are probably familiar with)

Among the more useful are:

To verify that dmraid supports your chipset type:   dmraid -l
If your raid type is listed you should be supported.

To find the raid devices already active: sudo dmraid -r

If nothing shows up try: sudo dmraid -ay

You will find that at this stage gparted will not see your raid sets and Disk Utility won't see them unless they have been activated. I am unfamiliar on how raid may be handled in wubi, but, in general fakeraid behavior has differed between different Ubuntu releases and nothing would surprise me. Dmraid is consistent and if your chipset is supported you should be able to see and use the your raids. One last thought, verify (with -l) whether raid5 is supported for your chipset.

---

### Post by moravia on 2010-06-22
Thanks so much, ronparent

So my RAID is definitely supported ('isw' Intel Software RAID 5) and the RAID devices showed up without requiring any activation...

/dev/sdc: isw, "isw_cicfhjahea", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_cicfhjahea", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_cicfhjahea", GROUP, ok, 1953525166 sectors, data@ 0

In 'Disk Utility' I can see all 3 drives, but not as a RAID set.  Each drive is 1TB in size, so with RAID 5 I effectively have 1.84TB, but ubuntu seems to be confused by the configuration...

under SATA Host Adapter my drives show up as
sda:
 - Partitioning: "Unknown Scheme"
 - 2.0TB 'RAID' component (/dev/sda1)
 - 1.84TB unallocated space (/dev/sda)

sdb
 - Partitioning: "Not Partitioned"
 - 1.0TB 'RAID' component (dev/sdb)

sdc:
 - Partitioning: "Unknown Scheme"
 - 2.0TB 'RAID' component (/dev/sdc1)
 - 1.84TB unallocated space (/dev/sdc)

under Peripheral Devices, however, I also see a 2.0TB Hard Disk, which appears to be my RAID set (I named it Volume0)

/dev/mapper/isw_cicfhjahea_Volume0:
 - Partitioning: "Master Boot Record"
 - SMART Status: "Not supported"
 - 2.0TB unallocated space

I can't seem to do anything with Volume0, however, and it does not appear on as a drive under 'Computer'

Is there something I can do within 'Disk Utility' or using dmraid to clarify my RAID configuration for ubuntu?

~Amanda


> **ronparent said:**
> For a short list of dmraid command parameters type in a terminal:  dmraid --help (which you are probably familiar with)

Among the more useful are:

To verify that dmraid supports your chipset type:   dmraid -l
If your raid type is listed you should be supported.

To find the raid devices already active: sudo dmraid -r

If nothing shows up try: sudo dmraid -ay

You will find that at this stage gparted will not see your raid sets and Disk Utility won't see them unless they have been activated. I am unfamiliar on how raid may be handled in wubi, but, in general fakeraid behavior has differed between different Ubuntu releases and nothing would surprise me. Dmraid is consistent and if your chipset is supported you should be able to see and use the your raids. One last thought, verify (with -l) whether raid5 is supported for your chipset.

---

### Post by ronparent on 2010-06-22
Do raid drives show in nautilus - under my pc? If the arrays are active, in 10.04 they should show. Also try: sudo dmraid -b    ....with this command you should see the individual partitions. 

Ignore the sda, sdb, sdc under 'Disk Utility'. Trying to work with these would destroy the integrity of the array. The partitions should appear under peripheral devices. What else appear under /dev/mapper/? That should list all of the individual partitions as well as the whole raid5 array (ie 'ls /dev/mapper/). If everything appears here you are in business.

Because Disk Utility and gparted do not now appear to useful with raid under 10.04, I personally keep an earlier version (9.04) separately installed (with dmraid as well) to create or resize raid partitions. Unless the functioning of isw has changed you indeed should be able to access your raid5 partitions in 10.04.

---

### Post by moravia on 2010-06-23
This is my output from [FONT=Courier New]/dev/mapper$ sudo fdisk -l[/FONT]

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac40d56b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953516544    7  HPFS/NTFS
/dev/sda2               1           1        1023+  83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac40d56b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953516544    7  HPFS/NTFS
/dev/sdc2               1           1        1023+  83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7756deaf

I also tried[FONT=Courier New] sudo fdisk isw_cicfhjahea_Volume0[/FONT] which produces a similar result

Disk isw_cicfhjahea_Volume0: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac40d56b

                         Device Boot      Start         End      Blocks   Id  System
isw_cicfhjahea_SAMSUNG_HD103SJ1               1      243202  1953516544    7  HPFS/NTFS
isw_cicfhjahea_SAMSUNG_HD103SJ2               1           1        1023+  83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

So, what do I do about the linux partition (Partition 2)?  How do I reset and/or delete it so that this error doesnt occur?

Thanks again!

~Amanda


> **ronparent said:**
> Do raid drives show in nautilus - under my pc? If the arrays are active, in 10.04 they should show. Also try: sudo dmraid -b    ....with this command you should see the individual partitions. 

Ignore the sda, sdb, sdc under 'Disk Utility'. Trying to work with these would destroy the integrity of the array. The partitions should appear under peripheral devices. What else appear under /dev/mapper/? That should list all of the individual partitions as well as the whole raid5 array (ie 'ls /dev/mapper/). If everything appears here you are in business.

Because Disk Utility and gparted do not now appear to useful with raid under 10.04, I personally keep an earlier version (9.04) separately installed (with dmraid as well) to create or resize raid partitions. Unless the functioning of isw has changed you indeed should be able to access your raid5 partitions in 10.04.

---

### Post by ronparent on 2010-06-23
>  also tried sudo fdisk isw_cicfhjahea_Volume0 which produces a similar result

Disk isw_cicfhjahea_Volume0: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac40d56b

Device Boot Start End Blocks Id System
isw_cicfhjahea_SAMSUNG_HD103SJ1 1 243202 1953516544 7 HPFS/NTFS
isw_cicfhjahea_SAMSUNG_HD103SJ2 1 1 1023+ 83 Linux
Partition 2 does not end on cylinder boundary.


I see no errors of concern in the above quote - this would be the only relevant data on the raid5 array. You haven't explicitly answered what shows up in the locations I mentioned. Also, from what I see so far the raid partitions should show under  >Places>Computer and be mountable?

---

### Post by Ed1000 on 2012-11-18
My raid 5 was not recognized. 
After typing sudo dmraid -r  and sudo dmraid -ay (just to be sure)
I saw the disk in my ' places' and could access it.
Great
checked under dev/mapper, saw the individual disks there too albeit is ' locked files'  I just left that as i now could access them.
Thanks

---

