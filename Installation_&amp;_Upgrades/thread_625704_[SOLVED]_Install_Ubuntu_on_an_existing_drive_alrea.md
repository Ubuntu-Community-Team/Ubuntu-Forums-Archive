---
title: "[SOLVED] Install Ubuntu on an existing drive already partitioned"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by gasport on 2007-11-28
I just reinstalled XP on my PC.  During the install, I partitioned the Hard Drive into a C and D partition.  I thought I would use the D partition to install Ubuntu.   I went through the install process until I got to the point of choosing which drive to install Ubuntu on.  I only saw the Hard Disk and not the D partition.   There were too many messages about overwriting information on the Hard Disk if I were to continue with the format.  I already have a second Hard Disk that is already being used so it is not an option to install Ubuntu there.

Is there a simple way of getting Ubuntu to install on the D partiton or do I have to unpartition the drive and start from scratch?    

Will the install of Ubuntu leave my existing XP installation there?   

Several years ago I did install Sues Linux on an older PC with XP installed and had no problems.  The install was very simple and I am hoping Ubuntu is the same.

---

### Post by meindian523 on 2007-11-28
If you can recognize your C and D drives by size,great.

What you have to do is to delete your D partition or format it as ext3 to allow you to install Ubuntu there...you don't need to unpartition your drive or anything.....how much space do you have as D partition?

---

### Post by gasport on 2007-11-28
Thanks for the quick reply.

I have 37.4 GB on that partition.  I figured that would be enough for Ubuntu.

Dumb question, but how would I format it as ext3?

---

### Post by meindian523 on 2007-11-28
37.4 GB is more than enough.:)

edit:

To format as ext3:
Use Partition Editor from the System>>Administration menu.Select your D: partition .Partition>>Format To>>ext3

But this creates a big ext3 partition.Instead,it's better that you delete the D: partition and create an extended partition and within it create a logical partition(10GB,file system:ext3,mount point /),a swap partition(2*RAM,file system:linux swap) and rest of the space,file system:ext3 and mount point /home.....

---

### Post by gasport on 2007-11-28
Thanks, I will delete the D partition and go that way.

---

### Post by meindian523 on 2007-11-29
Please mark thread solved.

Thread Tools>>Mark as Solved.

---

