---
title: "Strange partition problems in Fiesty 7.04 Installation"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by iminj on 2007-04-19
I'm struggling with installing ubuntu 7.04 from the liveCD to dual-boot with WinXP on my laptop. 

I have a 100GB SATA drive. Curently, the drive is partitioned as follows:

/dev/sda1   ntfs   70507 MB   (My primary XP partition)
free space            21064 MB   (Where I want to put ubuntu)
/dev/sda2              3668 MB    (TrueCrypt archive)
/dev/sda3              4784 MB    (Lenovo recovery partition)

**Here's the problem I'm having ....**. When the ubuntu installer gets to the partioning process, I selected "manual", as I didn't want any existing partitions to be overwritten. When I select the 21GB of free space, the fiesty installer allows me to make 1 partition (for example, the SWAP partition), but then it identifies the remaining free space as "unusable", and won't permit me to create the root (/) partition.

If I reverse the order and create the root partition first, the remaining free space is labelled "unusable", and I can't create the SWAP partition. 

**I can only create 1 partition, and I need 2 !!  What am I doing wrong?**

Thanks -iminj

---

### Post by Eagle117 on 2007-04-19
I am a Windows person mostly but watching this forum today for hints to get Ubuntu installed on VirtualPC.  I know there is a limit with some file systems for 4 active partitions on a drive.  I don't know how the other partitions on your drive are created but I wonder if you are hitting this limit and that it why it is "unstable" after you try to create more than 4...

---

### Post by Eagle117 on 2007-04-19
This thread seems to confirm this: [http://ubuntuforums.org/showthread.php?t=414014](http://ubuntuforums.org/showthread.php?t=414014)

---

### Post by sisco311 on 2007-04-19
make the swap partition logical
(you can have max. 4 primary partitions)

---

### Post by bulldog on 2007-04-19
Make the free space an extended partition,in this extended partition you can create logical partitions.

Create a 1GB swap
Create a 10GB / root
Create a /home from the rest.

---

### Post by bulldog on 2007-04-19
> **sisco311 said:**
> make the swap partition logical
(you can have max. 4 primary partitions)

Won't work,I'm afraid,you need to make an extended first,so you'll have three primary's,one extended and logicals at your need.

---

### Post by iminj on 2007-04-19
Thanks everyone! Your advice was terrific.

Turns out, I was trying to create 5 primary partitions, one more than the limit.

I started with 3 partitions, and successfully installed Feisty (7.04) by creating the following partitions in the ubuntu installation process:

I made the 4th partition (SWAP) a logical partition.
I made the 5th partition (/) a primary partition.

This worked .... and the installation completed. So far ... so good .... Thanks.
-iminj

---

### Post by stealth17 on 2007-04-20
I'm not sure if it's a bug or not, but I noticed that if the drive is mounted when running the installer from a LiveCD, the partitioner was all screwed up when I tried to manually set my new partitions.

I have a 500gb Sata2 drive and I made a 2gb primary swap, then a 10gb primary root, then the rest I make into a primary on /home. When I add the partitions it shows some 400gb free and the /home partition would only go upto around 60gb.

This is on a Seagate 7200.10 and a DFI NF4 Ultra-D.

---

