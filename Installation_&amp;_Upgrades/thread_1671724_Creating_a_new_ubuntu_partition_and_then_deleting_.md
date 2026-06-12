---
title: "Creating a new ubuntu partition and then deleting it"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by pauldinu on 2011-01-20
Hi guys!
I have two 500gb hdd. One of them crashed (the one which i used windows on) and its now getting sent to the warranty people.
On my other hdd i do not have any OS installed, it's just one 500gb NTFS partition, i have there just some personal important stuff.
I want to install ubuntu 10.10 x64 on it. I understood that when i will do this, from the available free space it will be created a new partition.
I have tryed to get along with linux a few years ago and i failed... Can you tell me if i will be able to delete the partition ubuntu is creating and merge the unpartitioned space back to NTFS without formating the drive? Also how big are the risks of losing my data when i try to install ubuntu and when i will try to go back to one big NTFS?
Thank you!

---

### Post by zvacet on 2011-01-20
It is always good to backup ( on some external drive or something else) before you go with Ubuntu install.First shrink existing partition and on that unallocated space install Ubuntu.You will have to mark that partition as root / and format it as ext4.

---

### Post by zvacet on 2011-01-20
It is always good to backup ( on some external drive or something else) before you go with Ubuntu install.First shrink existing partition and on that unallocated space install Ubuntu.You will have to mark that partition as root / and format it as ext4.

---

### Post by zvacet on 2011-01-20
It is always good to backup ( on some external drive or something else) before you go with Ubuntu install.First shrink existing partition and on that unallocated space install Ubuntu.You will have to mark that partition as root / and format it as ext4.

---

