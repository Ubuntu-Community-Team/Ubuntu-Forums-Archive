---
title: "Problem with partitioning"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by dperry112 on 2006-02-22
I installed ubuntu linux on an HP computer with 2 hard drives. After some problems, I finally got both formatted for linux with the first hard drive as the boot drive. The second one I use the disk utility to mount the partition in a subdirectory of the /home directory: /home/disk.  I created another subdirectory /home/data1 that is not mapped to a partition. Both subdirectories were shared using samba. That works ok but every time the system is rebooted, it loses the mount point and I have to reassign it. I am using the system for file backup from our windows computers. When I look in the windows xp network neighborhood, I see the linux system and clicking on it I see the two shared directories. When I click on the directory I see, again, both subdirectories and a single user directory. Clicking on the directory finally gets me to the data.  It looks as though the structure is:

data\data
data\data1
data1\data
data1\data1

This is not really a problem since I can map to what looks like a lower level directory. The real problem is having the partition mount point disappear. Any help or explanation appreciated.

---

