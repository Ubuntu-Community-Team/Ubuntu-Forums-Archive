---
title: "Partitioning the Disk"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by Deadpool on 2008-09-02
I'm attempting to install Ubuntu from the live CD onto my Macbook, but I have trouble with the partitioning of the disk. I want to do it manually, and when I look at the disk partitions I see a partition of free space with 0 MB. Then a partition with 209 MB. Then I see the main one, with 59967 MB or something like that. Then at the end is another free partition with 306 MB or something close to that of free space in it. What is the step by step process to do the following:

1. Make the existing partition (Macintosh OS X) 30 GB
2. Make a new partition for Ubuntu, with 25 GB
3. Make a swap partition, with 1 GB in it (I have 512 RAM)

Thanks for any help, as I'm really looking forward to using Ubuntu

---

### Post by falcon61102 on 2008-09-03
To make this a little easier, could you boot up from the LiveCD and run the following command in the terminal:
```
sudo fdisk -l
```
-l is a lower case L

This will display your entire partition table as well as their types which may help in getting this setup for you.

As a guess, some of those smaller partitions may be bootloaders or backup partitions.

---

