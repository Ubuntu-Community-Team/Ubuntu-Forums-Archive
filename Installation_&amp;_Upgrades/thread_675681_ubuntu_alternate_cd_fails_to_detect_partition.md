---
title: "ubuntu alternate cd fails to detect partition"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by rache1111 on 2008-01-22
Hi there,

I have windows vista installed and I am trying to create a dual boot system with ubuntu 7.10.
Before installing I created a ext3 primary partition and a linuxswap logical paritition using a tool called arconis disk director. 

Unfortunately the alternate installation cd did not correctly detect all the partitions that I currently have; instead, the installer simply displayed the whole disk during the partition step (not even the ntfs primary active partition used by windows vista is detected).

I did try to install before I used the arconis tool, the alternate cd installer did detect all the partititions without problems back then. After using the acronis tool, I checked the partitions created in windows vista using the computer manager and didn't really find any problems.

As for perior ubuntu experience, I did once install 7.04 on this system using the alternate disk on this system without problems. I can only use the alternate disk because my ati x1400 graphics card doesn't allow the live cd to run. Can someone point out what could have I done to cause this and how I can fix it?

If it helps, my system is a thinkpad T60 with core 2 duo and 2GB of memory.
Thank you for your help!

---

### Post by rache1111 on 2008-01-23
I think I have found out the problem... the maximum number of primary paritions allowed has been reached. Strange that windows nor arconis complained about this problem.

I already had three partitions installed on this system, one for vista and one for the recovery console, another for misc documents. The first two are primary paritions and the last one is logical extended *?l. Since I didn't have an extended partition setup, creating another two primary partitions would be over the 4 maximum limit... 

so my arconis created the ext3 as a primary partition and the linux swap as logical in the extended partition.

After the two partitions created for ubuntu were deleted, the alternate cd installer detected the partition properly, showing the free space available. Using the alternate cd installer built in partition tool, I created a ext3 partition, suddenly the remaining free space became "unusable". 

I really don't know why that has happened... does this mean that all of the logical parititions must be sequential (right next to each other)? There certainly wasn't this kind of limitation in acronis.

---

### Post by logos34 on 2008-01-23
> **rache1111 said:**
> I think I have found out the problem... the maximum number of primary paritions allowed has been reached. Strange that windows nor arconis complained about this problem.

I already had three partitions installed on this system, one for vista and one for the recovery console, another for misc documents. The first two are primary paritions and the last one is logical extended *?l. Since I didn't have an extended partition setup, creating another two primary partitions would be over the 4 maximum limit... 

so my arconis created the ext3 as a primary partition and the linux swap as logical in the extended partition.

After the two partitions created for ubuntu were deleted, the alternate cd installer detected the partition properly, showing the free space available. Using the alternate cd installer built in partition tool, I created a ext3 partition, suddenly the remaining free space became "unusable". 

I really don't know why that has happened... does this mean that all of the logical parititions must be sequential (right next to each other)? There certainly wasn't this kind of limitation in acronis.

They have to be contiguous, though not necessarily in strict sequential order--you can end up with sda5, 7, 6, for instance.  

Try the [Gparted Live CD]("http://gparted-livecd.tuxfamily.org/"), or gparted on the [Parted Magic]("http://partedmagic.com/") utility disc (using the vesa or 'Xvesa' driver).  Ideally, backup whatever you have on the misc docs partition and then wipe the whole extended partition and create a new one.  Then attempt the installation again.

---

### Post by rache1111 on 2008-01-23
thanks logos34,

what I ended up doing was just to delete the recovery console and expanded the extended partition. Installation then went without a hitch.

---

