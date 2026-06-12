---
title: "Ubuntu 10.04 on flash drive WITH NTFS partition"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dpmanthei on 2010-04-11
Hello all,

I like to run Ubuntu 10.04 from a flash drive on a variety of computers in various locations.  BUT, I would really like a 4GB NTFS partition on my 16GB flash drive so I can still use it for Windows storage occasionally.  Despite my attempts, I cannot get a Windows 7 or XP machine to see the partition.  What am I doing wrong?

What I've tried:

**1**
Formatted first 4gb to NTFS (or FAT32)
Went back with Gparted and marked NTFS/FAT32 drive as "boot"
Install Ubuntu at 'end' of drive, followed by 512mb of swap

**2**
Ubuntu first, Swap second, NTFS 3rd on drive.
Again, marked NTFS as "boot".

**3**
Also tried 1 & 2 without "boot" flag on NTFS drive.



*I am assuming "boot" is equivalent to "active" in MS terms, is that correct?

In each case, Ubuntu boots fine, but windows always says "drive not formatted, do you want to format now?" when I try to access it.  I have googled the problem and checked here but haven't found anything...I may not be using the right search terms, it's kinda hard to sum up this question into a few words.

You guys rock, thanks for any help, and all the help in the past!
Dylan

---

### Post by labinnsw on 2010-04-17
I would format the 4 Gb to NTFS in Windows. There seems to be some difference between the NTFS formatting of Gparted and Windows.

I don't remember what term Windows uses to flag a partition as bootable.
That is what the "boot" flag does in Linux. This is not to be confused with mountable, which is what I think "active" does in Windows. (I could be wrong)

---

