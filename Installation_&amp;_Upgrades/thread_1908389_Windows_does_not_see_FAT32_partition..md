---
title: "Windows does not see FAT32 partition."
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by Biopyro on 2012-01-13
I installed 11.10 to a USB, partitioning 2GB to 
FAT32. Although it can be seen (but not used?) in linux, windows does not see it at all. When I insert the USB it says I need to format it, and displays the size as [ext4 partition] instead of the size of the fat32 partition.

It's mounted on /windows if that makes a difference?

---

### Post by saneearth on 2012-01-13
It seems that for some reason the 2GB partition was not formated correctly as FAT32. I would just format it again. Have you checked it with gparted or another tool to see for sure that it says it is a FAT32 partition. It is odd that it shows as ext4 otherwise if it was indeed formated correctly as FAT32.

---

### Post by Biopyro on 2012-01-13
I don't think it's seeing the fat32 partition at all though, it just seems to be recognising that the USB stick is there and that it needs formatting to be used. 


If I right click on my computer and look at it with the "manage" option it says it's 28GB instead of the 32 it actually is (2GB FAT32, 200mb swap)

Edit: using the manage option in windows 7, it may have been seeing fat32 only after all.

---

### Post by oldfred on 2012-01-13
Windows only sees the first partition on a flash drive.  Is the FAT32 the first partition?

---

### Post by Biopyro on 2012-01-13
No, and I bet that's the problem. I tried to format only that partition with disk manager, and it formatted the entire USB stick.

---

### Post by ottosykora on 2012-01-13
>I tried to format only that partition with disk manager, and it formatted the entire USB stick.<

this is correct and can not be changed, windows will not handle it differently, perhaps you should complain to the authors of windows about it... ;-)

---

