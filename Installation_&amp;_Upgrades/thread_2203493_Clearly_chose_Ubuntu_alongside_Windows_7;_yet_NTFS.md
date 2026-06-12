---
title: "Clearly chose Ubuntu alongside Windows 7; yet NTFS partition not visible anywhere"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by Charging on 2014-02-03
Hi All,
      I installed Ubuntu 12.04 LTS yesterday and very clearly chose installation alongside Windows 7. Then I created swap partition and another 50GB partition for Ubuntu. There was an option 'Format drive' which was automatically checked, and I coudn't uncheck it. Plus, I thought that it will format those 50GBs where it's installing Ubuntu. Now it only boots from Ubuntu, there are no Windows 7, no data files to be seen. I have tried GParted, TestDisk, etc. but I can't find any NTFS file system anywhere.
  I'm particularly interested in recovering my data files, which were all in one folder. Any help please?

  Thanks in advance.

---

### Post by Charging on 2014-02-03
Also, sudo fdisk -l only shows 2 drives, sda1 (swap) and sda2 (linux), respectively. Any help will be deeply appreciated.

---

### Post by nothingspecial on 2014-02-03
It sounds like windows is gone. At this point the most important thing is to stop using the Ubuntu install. Use bootable media to try and recover. If you have written over windows and continued to use Ubuntu since then the chances of recovering are slim.

---

### Post by Charging on 2014-02-04
I think that I have cornered the main cause of this problem. When I was installing Ubuntu, I created new partition table, and a warning was that it will redefine the partition table on the drive since there was only 1 drive on the system. However, it also said, "Note that *you will* be able to *undo* this operation *later* if you wish". Is it possible to undo that, and how?

---

### Post by buzzingrobot on 2014-02-04
> **Charging said:**
> I think that I have cornered the main cause of this problem. When I was installing Ubuntu, I created new partition table, and a warning was that it will redefine the partition table on the drive since there was only 1 drive on the system. However, it also said, "Note that *you will* be able to *undo* this operation *later* if you wish". Is it possible to undo that, and how?

Yes, creating a new partition table impacts the entire drive. I.e., deletes all existing partitions and creates one or more new partitions.

i suspect the "undo' "later" bit meant later in the partitioning portion of the install. Once you commit your changes and move on in the install, the new partition table is created.

---

