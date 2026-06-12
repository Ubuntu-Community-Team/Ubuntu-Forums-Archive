---
title: "Need help recovering partitions with Test Disk"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by kopo88 on 2006-08-08
My Win XP Home SP 2 PC has a 160 GB hard drive (might be Maxtor, but I'm not sure).
There are supposed to be 2 partitions:
1. HP_RECOVERY (Drive D) - FAT32 - about 5.8 GB
2. HP_PAVILION (Drive C) - NTFS - the rest of the drive

I recently made an unsuccessful attempt to shrink my NTFS partition with QT Parted to install Ubuntu 6.06. Since then, the NTFS partition started showing up as Unknown or Unformatted in various Linux programs (which I'm running off Live CDs, including GParted in Ubuntu).

I tried installing and using TestDisk ([www.cgsecurity.org](www.cgsecurity.org)) in Ubuntu (live CD), but it couldn't see my hard drive for some reason.
Instead, I downloaded an Ultimate Boot CD ([www.ultimatebootcd.com](www.ultimatebootcd.com)) and used the DOS version of TestDisk that's included.

Here's what it showed:
[http://img340.imageshack.us/img340/5846/img0075ta4.jpg](http://img340.imageshack.us/img340/5846/img0075ta4.jpg)
[http://img340.imageshack.us/img340/6841/img0076zk1.jpg](http://img340.imageshack.us/img340/6841/img0076zk1.jpg)
[http://img530.imageshack.us/img530/6503/img0077ka0.jpg](http://img530.imageshack.us/img530/6503/img0077ka0.jpg)

In the screen shown in the 3rd image, I found I was able to make one of the 2 partitions not Deleted.

These images, and a helpful email from TestDisk's author, suggest 2 things:
1) The hard drive's geometry is damaged (I don't know how, or what this means, exactly).
2) The two partitions might be overlapping each other somehow - hence only one can supposedly be restored.

I don't really care about the HP_RECOVERY partition (I can order a recovery DVD from HP), but I desperately need the files on the HP_PAVILION partition.

If I change the status of the HP_PAVILION partition to [Primary & Bootable] in TestDisk, will it start working normally again? At the very least, I need to be able to save the files, with complete filenames and directories, to another hard drive (external, preferably).

Any other ideas?

---

### Post by teasum on 2006-08-08
I'm a noob in here, so others probably have more/better advice.  However, I had a partition problem that I fixed not too long ago.  Basically, after re-installing XP, my partition table got screwed up.  Long story short, I used testdisk, parted, fdisk, gpart, and other programs to figure out what was going on, and how to fix it.

1) If you want to know if you have overlapping partitions, parted should tell you that.  I ran parted from the command line, and it was unable to display my partition table.  But the error message it spit out was "cannot have overlapping partitions."

2) No partition tool could recognize my partitions, except DiskDrake. Once I knew I had overlapping partitions, I found out which ones they were, and simply deleted the non-critical one.  Check out this link for info on DiskDrake: [http://www.ubuntuforums.org/archive/index.php/t-114142.html](http://www.ubuntuforums.org/archive/index.php/t-114142.html).

3) What's your output from sudo fdisk -l?  Perhaps this could also confirm whether the problem is HD geometry or overlapping partitions.

EDIT: Also, try changing the geometry from 255 to 240 in testdisk and then scan your drive... it will most likely result in a more accurate partition table. 

That's my 2 cents.  Good luck.

---

