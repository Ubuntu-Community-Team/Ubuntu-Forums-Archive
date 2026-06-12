---
title: "Disk Partition Questions"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by ChrisSmith on 2006-09-02
Hi, at the momment Im running windows and I have my hard disk partitioned into a 60gb partition and a 9gb partition (no idea why). Is it possible to install ubuntu onto the 9gb partition without affecting my current windows installation? Would it do anything to the data on 60gb partition?

Thanks, Chris

---

### Post by catlett on 2006-09-02
Yes you can choose the 9gb partition and it will not affect windows. Just go to My Computer and double click the icon for the 9gb partition to make sure there isn't any data there. Alot of newer computers are shipped with a recovery partition. It will be a small partition with the original factory install onit that can be used to restore th other partition to the factory install.
As long as it is empty, you can select that partition when installing.Just select "manually edit the partition table"
Here is a guide for the live cd install [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) It is part of a larger site that Aysiu maintains. It has alot of useful ubuntu information [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by ChrisSmith on 2006-09-02
hmmm well the 9gb partition is not empty as I was using it to store photos and stuff. But im planning on moving the data on it to the 60gb partition, will this still be okay?

thanks for replying :D

**PS: I also forgot to mentioned the 9gb partition is named C on windows. Will this have an affect as I know how much windows loves the C.. :(**

---

### Post by catlett on 2006-09-02
The thing is, any data on the 9gb partition will be lost. That portion of your hard drive will be formatted to a linux file system and any data will be erased during format. The rest of your hard drive will not be touched. Just move any pictures, etc to the other partition before install.

---

