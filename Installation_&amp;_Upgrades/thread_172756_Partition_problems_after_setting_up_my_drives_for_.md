---
title: "Partition problems after setting up my drives for Windows/Ubuntu dual boot. Help!"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by KillrBuckeye on 2006-05-09
I am having a problem managing partitions on my WD 320GB drive, which is connected as the 2nd SATA drive.  This all started when I decided to install Ubuntu Linux on the drive for a dual boot option (WinXP resides on my 74GB Raptor which is connected to SATA 1).  Originally, my WD320 drive had 3 primary partitions, formatted as NTFS for data storage:  200GB, 65GB, and 50GB.  When I decided to install Linux, I took the following steps after backing up my data on the 200GB partition.

**_Creating Partitions Using a Linux LiveCD_**
-	I booted with the Ubuntu Linux LiveCD and opened the GParted partitioning program
-	I deleted the 200GB primary partition on the WD320 drive.
-	In its place I created a 10 GB primary partition and a 190GB extended partition
-	The 10 GB primary partition was formatted as ext3 for the Linux root
-	Within the 190 GB extended partition, I created 4 logical partitions:  15 GB formatted as ext3 for the Linux home directories, 1.5 GB for the Linux swap, 30 GB formatted as FAT32 for data storage/transfer, and the remainder (~140 GB) formatted as NTFS for data storage accessible from Windows


**_Windows Disk Management  Sees All Partitions as "Unknown"_**
When I exited and booted back into Windows, I was surprised to find that the Windows Disk Management saw all the newly created partitions as "unknown".  The format of the NTFS and FAT32 partitions was recognized, but Disk Management would not allow me to assign these drives as volumes to be accessed by Windows.  So, to make my NTFS partition accessible, I deleted it and recreated it using Disk Management.  This seemed to work, as I was able to assign a drive letter to this partition and transfer data to it.


**_Ubuntu Linux Installs Successfully_**
Next, I installed Ubuntu Linux using the partitions I created using the GParted program.  This went smoothly, and the Grub boot loader was working fine allowing me to boot to Windows on the Raptor, or Linux on the WD320.


**_Problems Start when I try to get Windows to Mount the FAT32 Partition_**
Everything seemed to be going as planned *except* for the fact that Windows couldn't mount the FAT32 logical partition that I created using GParted.  So, I decided to employ the same process I used to mount the NTFS partition: delete the partition and recreate it using Disk Management.  Here is where things went terribly wrong.  When I selected the FAT32 partition and told Disk Management to delete it, multiple logical partitions disappeared!!!  The resulting partitions on the disk are shown in the image below.

[IMG]http://i7.photobucket.com/albums/y299/KillrBuckeye/Computer/DiskManagementReduced1.jpg[/IMG]

As you can see, this operation deleted 3 logical partitions within the extended partition:  the 140GB NTFS partition, the 30GB FAT32 partition, and the 1.5GB Linux swap partition!  The 15GB partition for the Linux home directories was spared by this operation, for some odd reason (however, now Ubuntu fails to mount this when I boot).

At this point, Disk Management does not let me create any logical partitions within the free space of the extended partition!  I can go through the steps to create a partition, but I click "Proceed", I get the following error:

[IMG]http://i7.photobucket.com/albums/y299/KillrBuckeye/Computer/error.jpg[/IMG]

What is going on?! (Unfortunately I was in a hurry to get to work and I didn't check the Event Log for details)

**_Many Questions_**
Based on this experience, I now have many questions:

1)	Why can't Windows mount NTFS or FAT32 partitions that I create using GParted from the Linux LiveCD?

2)	Why did Disk Management delete 3 of my logical partitions when I only requested that it delete one?

3)	Why won't Disk Management allow me to create any logical partitions in the free space within the extended partition?

4)	If these problems can be blamed on the pathetic excuse for a partitioning tool called Disk Management, what are my options for resolving this problem in terms of software (preferably free).

5)	Assuming I can recreate the lost partitions, how can I remount the swap space and home directories within my Linux installation?

Any help you could provide would be greatly appreciated!

---

