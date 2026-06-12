---
title: "Query with partioner"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by klemencic on 2009-12-30
I am trying to reinstall Ubuntu 9.10 on my machine and have a query with the partioner
I have a dual boot system with xp and Ubuntu 9.10 but the current version of 9.10 broke when I upgraded from 9.04, thus I wish to reinstall
I have 2 HDD both with multiple partitions
When I boot from the install CD and come to the partitioning, the installer says
'This computer has several operating systems on it'
There are then three options
'Install them side by side choosing between them on each start up'
Erase the drive and use the whole drive for Ubuntu
Advanced - manually partition
I choose manual partitioning
For each partition I select 'change' and change the default 'Do Not Use This Partition' to what ever it currently is (NTFS or EXT3) and give it a mount point
So the only changes I am making is to give mount points to some of the partitions I didn't previously mount and format / and /usr - I am not changing to EXT4 or changing the size of the partitions
After I confirm this I am taken back to the previous screen at the start of the partioner which shows the current and new partitions, and it shows that it has halved the /usr partition and split this between the existing 9.10 and the new 9.10
After clicking on forward I receive the following message
'Before you can select a new partition size any previous operation changes have to be written to disk. You cannot undo this operation'
Before I hit the button, my question is will this partition the drive as shown, or as I requested in the manual partitioning screen
Also before this, the installer looks for existing OS and accounts to import and it says it cannot find anything - is this correct as I currently have an account in 9.10 and there is xp installed which grub currently sees
My main problem is with the partitioning and will worry about grub later if needed

---

### Post by howefield on 2009-12-30
Reinstall to the partitions that Ubuntu was previously on.

At the manual partitioning screen, only "change" those partiton(s) ie, / and /usr (and /home if you have a seperate /home partition). 

You don't need to mount swap, if it is there, the install will find and use it.

You could also boot to the Live cd desktop, and make/format the partitions as required from System > Administration > GParted, then go through the installer, telling the partitioner which to use.

Grub should take care of itself, with potential complications coming only if you upgrade grub after installing the system updates.

---

### Post by audiomick on 2009-12-30
> **klemencic said:**
> 
After clicking on forward I receive the following message
'Before you can select a new partition size any previous operation changes have to be written to disk. You cannot undo this operation'
Before I hit the button, my question is will this partition the drive as shown, or as I requested in the manual partitioning screen

If I have understood you correctly, you are doing things right and pushing the button will apply your changes.

> Also before this, the installer looks for existing OS and accounts to import and it says it cannot find anything - is this correct as I currently have an account in 9.10 and there is xp installed which grub currently sees
Don't  know, sorry.

---

