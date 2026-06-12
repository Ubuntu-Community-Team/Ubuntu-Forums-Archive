---
title: "Botched Partition"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by brent16 on 2014-12-22
Hello, I did a search to see if anyone had asked a similar question but didn't find anything I fould helpful. My problem is that I installed ubuntu and changed my mind. I would like to reinstall windows 7 (I have a windows 7 and loader disk) but when I was going through the boot process and it said that my hard drive is the wrong format. I searched how to fix this and I found that I was supposed to partition a section of the hard drive for windows using gparted. The problem is that I think I've messed something up. I can't seem to create a new partition or change the size of the one I have. There is an attached file that shows my gparted, so hopefully that helps. Thanks!

---

### Post by grahammechanical on 2014-12-22
The only experience I have of installing Microsoft Windows is when I installed a Windows 8 preview edition. I got the same kind of message. I had to use the Windows installer disk to format the partition to the Windows format - NTFS, I think. Then when I ran the windows installer it did not have any problem installing.

Regards.

---

### Post by Bucky Ball on 2014-12-22
Boot from Live media (disk or USB), launch Gparted, delete the EXT4 partition, install Windows. Just leave unallocated (free space) then boot from the Win disk. The install process will let you create an NTFS partition of whatever size to install it to.

You can't resize or delete the Ubuntu partition from a running Ubuntu system installed in that partition. You have an odd setup, BTW. One large partition taking up the entire drive, no /swap. :-k

Doesn't really matter at this point I guess. Try the above instructions. 

We can help you get rid of the EXT partition (which is what Win is complaining about), but we probably really give you much of a hand with Windows issues in this forum section. You don't need to partition a section of the hard drive with Gparted. Just wipe the EXT partition and boot from the Win disk.

---

### Post by brent16 on 2014-12-22
I tried that but it wouldn't let me format from the windows install screen.

---

### Post by brent16 on 2014-12-22
okay, attempting now.

---

