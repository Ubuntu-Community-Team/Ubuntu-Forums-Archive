---
title: "Question about 4k hard disk setup"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by KillerKelvUK on 2013-01-13
Building my very first Ubuntu Server (12.04.1) and have a question about my disk prep that I'm struggling to find a confirmation on with my good friend google.

Basically I have 2TB Seagate ST2000DM0001 which I believe is a 4k sector drive.  I've read quite a few posts now on the appropriate formatting needed for these drives so I'm partitioning the sectors at the 1MiB boundard (2048).

When I do a 'sudo fdisk /dev/sda -l' I get the following output...

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x332662e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907029167  1953513560   83  Linux


I'm confused with the above because I was expecting the logical sector size to report 4096 bytes which would then align/match the physical sector size.  This is further compounded when I issue a 'sudo fdisk /dev/sda' again as the following is output...

"The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted."

I've formatted the partition using 'sudo mkfs.ext4 -b 4096 /dev/sda1'

Can someone point me in the right direction please as I'm pretty fraught with this now :-(

Thanks,

K

---

### Post by oldfred on 2013-01-13
Are you mixing bytes & sectors which may be either 512 bytes or 4K? Or you really need 8 sectors.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by darkod on 2013-01-13
The logical size of 512B is for compatibility. While the physical size had to be enlarged to 4096B so that bigger capacity can fit on the plate(s). So, that is normal and don't worry about it.

Also, your first partition starts at sector 2048 which makes it aligned. That's why that message is confusing. You might have gotten yourself into trouble by using -b 4096 when formatting and that might produce that message, although I can't be 100% sure about that.

I recently added two 2TB disks to my home server, and I simply formatted without specifying any -b options.

If there is stil no data on the partition, I would reformat it without that option and see if the message about the alignment goes away.

---

### Post by darkod on 2013-01-13
PS. Also, that fdisk message might be normal, just information. It never says your partitions are not aligned, it only says the logical size is smaller than the physical, which is true and how it should work, and further it says it's better to align the partitions for optimal performance, which you have aligned to 2048 sector.

I don't know how fdisk acts and whether that message is normal since I never use 'sudo fdisk /dev/sda'. For all disk management in the terminal I use either sudo or cfdisk, not fdisk. I have even seen threads that sometimes it doesn't even create good partitions if you use it for partitioning.

---

### Post by KillerKelvUK on 2013-01-13
Thanks for the feedback and links, so to test that my understanding is correct...

The logical/physical sector sizes of 512/4096 is okay, just an output of fdisk to inform you and thus I'm compliant with the 4k sector format as the partition starts at 2048 which divisible by 8.

(I guess I got confused as there are a lot of other posts about this where the fdisk output shows logical sector sizes of 4096, so I'm assuming this is just because the disk geometry for those drives based on capacity made it so?)

I'm still in dev mode with the box so had the opportunity to play around...formatting without the -b option delivers the same message/result in fdisk so I guess that must just be a "feature" :-).

My ultimate intention is to create a RAID 10 out of 4 such disks and then apply LVM.  I believe there are some further points to observe with 4k sectors and LVM so I'll do some more reading on that shortly.

---

