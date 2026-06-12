---
title: "N'help &quot;just&quot; &quot;formatting&quot; a primary XP partition basic, empty, raw, drive"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-07-02
Started a new thread pertaining to my current situation. Previos problem was posted in [Linux partitioner question pertaining to winXP](http://ubuntuforums.org/showthread.php?t=45605)  
 
 Excuse the sort of double post but sometimes its the only way to get help with a specific problem. 

 Spend most of the day resizing my main ntfs drive partition with Qtparted (Gparted didnt work!). Then I managed to get it partitioned as a primary partion with a drive letter. The partition is 54G and XP can only format up to 32G so im looking to do something within Linux but trying to stay closest to the XP Vfat format. Anyways my G: drive partion is sitting there raw and empty and is described as simple. 

 I was thinking of using Qtparted but I read there is some difficulties with fat32. My main concern is having the partition labeled as Linux and there for not be acceessable by WinXP also read of that happening. I kind of want to stay away from Gparted as it couldn't resize my partition and read of someones fet getting dorked but he actualy created the partition with it though. 

 Any suggestions would be greatly appreciated.

---

### Post by tread on 2005-07-02
You cannot run Linux off a Fat32 partition, you need to create an ext3/reiserfs partition. Those will not be accessible from windows, though there are tools that will let you copy data from these partitions while in windows.

---

### Post by Omnios on 2005-07-02
Actual I have a 120G drive partioned to C: 59G ntfs  :G 54G simple raw unformated (this will be my fet 32, My Documents drive for XP and Linux.)
 And also another 40G Linux drive that I have linux installed on.

---

### Post by Omnios on 2005-07-02
problem solved used terminal with "  sudo mkfs.vfat -F 32 /dev/hda2  " command which makes a fat -F 32 makes it fat 32 and /dev/hda2 is the partioned hard drive which I used Gparted to make shure of the address. Checked and it all works in Xp and Linux

---

