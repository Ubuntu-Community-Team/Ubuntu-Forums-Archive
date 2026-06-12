---
title: "Can't see volumes in installation process"
date: 2019-10-27
forum: Installation &amp; Upgrades
---

### Post by mikelodeon72 on 2019-10-27
Ok.
I have an HP Pavilion dv7
Quad core, 750 GB HD and 8 GB RAM
Running on Windows 7.
I am trying to install Ubuntu 18.04 in this notebook (two OS in the same computer, dual boot)
I made another partition (120 GB and NTFS)
using windows, unused and clean.
Now, starting from CD and installing linux but
when I have to pick the partition to install I have problems, I can't see the new partition,  the details linux shows the disk info is totally different to win 7. Even the factor 1024 seems not to make sense.
I have pictures or both views but can't post them here.
I just need to identify the right partition for this new OS.
I would appreciate any help regarding this matter.
Thank you

---

### Post by TheFu on 2019-10-27
Linux cannot be installed into NTFS.  Linux uses other file system types.  Delete the empty NTFS partition and leave that storage unallocated.  That should allow the Ubuntu Desktop installer to suggest something like "install next to existing operating systems".

I don't dual boot, so can't say what you should select from the install options. I always choose **do something else** since I want complete control over my storage layouts.

Before you do anything like installing a new OS, please, please, please, make a know-you-can restore, full backup of everything you don't want to lose.  You've been warned.

---

