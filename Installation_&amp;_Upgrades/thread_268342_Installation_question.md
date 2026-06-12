---
title: "Installation question"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by unquenchablefire on 2006-09-30
I am installing Ubuntu now, to my desktop (it is the newest version, got the cd's via mail). I have two harddrives- a 200 gig harddrive with windows and all of my games and major programs. I have a second 100 gig harddrive that has two partitions: 75 gigs for media and freeware programs (kinda like a quarintine drive), and 15 gigs left open on purpose for linux. As I said, i'm trying to install ubuntu on the 15 gig partition of the second drive:
[IMG]http://www.maj.com/gallery/unquenchable/PhotoshopPhun/screenshot-part1.png[/IMG]
I believe i have it picked out.

I stopped instalation when i got to this screen:
[IMG]http://www.maj.com/gallery/unquenchable/PhotoshopPhun/screenshot-part.png[/IMG]
Because it had all my drives marked for editing. I was wondering if someone could clarify what would happen if i left these default settings and continued. I just want to make sure i don't loose Windows or any of my other data. I don't mind if the 15 gig partition is reformatted. Thank you in advance.

PS: Should this have been in the beginner forum?

---

### Post by BoneKracker on 2006-09-30
1. Stop

2. Go back, delete the NTFS partition that's currently at sdb1.  Apply that change.

3. Select "Guided Partitioning" and "Use the largest unallocated space".  (Or alternatively, in the space where sdb1 used to be, create a new partition (of type "swap") about twice the size of your computer's RAM, and then allocate the rest to a new partition (of type "ext3").

4.  If you find yourself back at the screen you pasted in here, make the mount points for your partitions on sda blank, and make the mount point for the NTFS partition on sdb "/media/quarantine" or something.  Make sure "format" is NOT checked next to any of them except the new partitions (ext3 and swap on sdb).  The mount point next your new ext3 partition should be "/" (not /media/something) -- this is where you said you wanted to put Linux (on the 15 GB partition).

---

### Post by unquenchablefire on 2006-09-30
Just to clarify, i made the partition without using ubuntu (i did it when i got the drive.) Also, what is the best way to remove a partition?

---

### Post by BoneKracker on 2006-10-01
Boot the live CD

```
fdisk /dev/sdb
?
```

Also, when you run the installation, and the "partioner" is running, you can select and delete partitions, create partitions, etc.

---

