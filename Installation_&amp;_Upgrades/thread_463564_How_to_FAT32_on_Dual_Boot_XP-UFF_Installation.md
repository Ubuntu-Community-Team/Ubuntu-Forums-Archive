---
title: "How to FAT32 on Dual Boot XP-UFF Installation?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by bettyhills on 2007-06-03
My questions are on how to create a FAT32 partition for access by both OS on a Dual Boot XP-UFF Installation?

One blog says during the partitioning stage on installation to mount the FAT32 logical partition at **/windows**.  Why?  Will the data files on that partition then be accessible to both WinXP and UFF?

What happens if you instead called it /data?  Could both OS read and write to it?

How does WinXP see the FAT32 partition, since it is not a "lettered" drive, e.g. C:, D:, E:, etc?

---

### Post by bettyhills on 2007-06-03
I found this advice through a forum link [http://www.geocities.com/epark/linux/partition-share-HOWTO.html]("http://www.geocities.com/epark/linux/partition-share-HOWTO.html")

I recommend creating a separate partition that is accessible to both Windows and Linux. I'll refer to this as a "share" partition. It must be of type FAT32 (same as vfat) or FAT to be accessible and writable by both OSs (NTFS is not yet an option as Linux does not support writing to NTFS partitions). To make the share partition visible and writable by both OSs, do the following: 

Create a FAT32 partition that you want to be visible by both OSs. I don't explain how to do that here. I believe you can create the FAT32 partition in Windows using Start->Run->Administrative Tools->Computer Management->Disk Management. Many Linux installation programs (e.g. Red Hat) allow you to create FAT32 partitions during the installation process. 
For Windows, you don't have to do anything to make the FAT32 partition accessible. The OS will automatically detect it and assign it a drive letter (e.g. E:) 
For Linux, do the following steps to make the FAT32 partition accessible: 
Create the directory that serves as the mount point (e.g. mkdir /osshare). The mount point is the location in the filesystem where you want this FAT32 partition to appear. 
Put an entry in the /etc/fstab file for the share partition. Be very careful in editing this file, as it's used at system startup! For an example, check out the /osshare entry in my /etc/fstab file. The umask option determines the permissions for all filesystems on the partition. 
Upon your next reboot into Linux, the share partition should get mounted automatically. If you wish to mount the FAT32 partition immediately, use the mount command, e.g.: mount /osshare 
Once you've set up your share partition, you can use it for transferring files between the OSs. For example, I found this invaluable for downloading RPMs while logged into Windows before I managed to get the Winmodem working for Linux. 

Things to keep in mind for your share partition: 

It's of type FAT32, so Linux functionality such as symbolic links won't work on it

---

### Post by merlinus on 2007-06-03
The good news is that you can have a partition formatted as NTFS or ext3, and by installing two drivers -- one for linux (ntfs-3g) and one for windows (ifs) you can read and write to either format from both sides of the block.

ntfs-3g is available from Applications/Add Remove.

ifs from fs-driver.org

I prefer ext3 for security and easy restore because of the journaling.

-merlin

---

