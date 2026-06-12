---
title: "Problem with Windows/Ubuntu partitioning"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by RDProgrammer on 2007-01-25
Hi,

I am trying to install Ubuntu 6.06.1 on my computer. I have installed it sucessfully and don't have a problem with that series of events. What I *am* trying to do is create a system with 4 partitions on my 75 GB hard drive. I want to have:

1: Windows XP Programs Drive (22 GB)
2: Data Drive (42 GB)
3: Ubuntu Swap Partition (512 MB)
4: Ubuntu Installation Drive (The Rest (~10GB))

The problem arises with partition 2, the data drive. I store all my data here, serpatarted from any OS. I cannot seem to find a way to make this aprtition recognisable to both Ubuntu and Windows. Any suggestions?

Thanks,

RDP

---

### Post by budgie9 on 2007-01-25
> **RDProgrammer said:**
> Hi,

I am trying to install Ubuntu 6.06.1 on my computer. I have installed it sucessfully and don't have a problem with that series of events. What I *am* trying to do is create a system with 4 partitions on my 75 GB hard drive. I want to have:

1: Windows XP Programs Drive (22 GB)
2: Data Drive (42 GB)
3: Ubuntu Swap Partition (512 MB)
4: Ubuntu Installation Drive (The Rest (~10GB))

The problem arises with partition 2, the data drive. I store all my data here, serpatarted from any OS. I cannot seem to find a way to make this aprtition recognisable to both Ubuntu and Windows. Any suggestions?

Thanks,

RDP
You do not state how you have formatted that partition. If you format it as fat32 it will be seen by both OS's. If NTFS you will need to download  a file to enable Ubuntu to read it. There are posts here re the latter.

---

### Post by meng on 2007-01-25
FAT, NTFS should be recognized by both Ubuntu and Windows, although you may need some tweaking. ext3 can be recognized by Windows if you install fs-driver ([www.fs-driver.org](www.fs-driver.org)). Please show us the result of:
sudo fdisk -l
(l as in Larry, input your user password when prompted and press enter).

---

### Post by logos34 on 2007-01-25
Open a terminal and type in these commands:
> sudo fdisk -l

> cat /etc/fstab

post it.

---

