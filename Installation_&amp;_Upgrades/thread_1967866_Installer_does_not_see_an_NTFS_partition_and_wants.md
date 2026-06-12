---
title: "Installer does not see an NTFS partition and wants to clear the whole disk"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by zelena on 2012-04-28
I prepared a USB flash drive with Ubuntu 12.04 x64. Then I want to install Ubuntu on HDD. At the beginning of HDD I have 90 Gb of unallocated space and want to install Ubuntu there. But after that space there is an NTFS volume that I do not want to erase. Ubuntu instaler doesn't see the NTFS volume and suggests to use the whole disk, as if there were no NTFS partition. When I start Ubuntu from the flash and examine the HDD with GPartEd, it does not see the NTFS partition. When I start Windows (from another HDD), Windows sees the NTFS partition fine and reports no problems there. So, how can I install Ubuntu to the unallocated space, preserving the NTFS partition?

---

### Post by darkod on 2012-04-28
There might be some error in the partition table so it is not seeing the partitions correctly. Boot into live mode and post the output in terminal of:
sudo parted /dev/sda print

That will print the list of partitions.

---

### Post by jadtech on 2012-04-28
you dont by chance already have 4 primary partition set up ??

---

### Post by zelena on 2012-04-28
sudo parted /dev/sda print
says only:
Error: Can't have a partition outside the disk!

When I start GPartEd, it says "Scanning all devices..." in the status bar, but it cannot finish the operation. 
The Ubuntu installer shows active the "New partition table..."-button under /dev/sda. But I do not want to create NEW partition table. When I choose to exit the installer, it pops up a message that the installer has internal error or something like that. 

The disk contains only one NTFS partition, and there are no other partitions now. There are only 90 Gb unallocated space at the beginning of the disk (this space appeared because another NTFS partition was deleted there).

---

### Post by darkod on 2012-04-28
Well, there is your error. Somehow you ended up with a partition outside the disk.
You can fix that with fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Run it from live mode. Download the .deb, right click it and install it. Then in terminal use it with:
sudo fixparts /dev/sda

I don't know what it will say exactly but it should offer to fix the partition outside the disk problem for you.

---

### Post by zelena on 2012-04-28
Thank you for the suggestions.
The problem resolved. Though there was only one partition on the disk, due to long history it was logical, not primary. I changed the status of the partition to primary (in Windows). After that Ubuntu installer successfully found it. In the free space I created a new ext4 partition and a swap. Then Ubuntu was successfully installed.
I feel somewhat disappointed that Linux can't work properly with logical partitions. What can we do to fix this?

---

### Post by darkod on 2012-04-28
Linux works much better with logical partitions than windows does. There is nothing to fix. The problem was that somehow the start/end sectors of the partition ended up outside the disk, probably this was done by some windows tool.

When you changed the partition I guess it recalculated the correct start/end sectors and rectified the error in the partition table. After that ubuntu could read the table correctly.

If you had run a tool showing the start/end sectors you would have seen yourself why does it say that it's outside of the disk.

Anyway, you have it sorted now. Please mark the thread as Solved in Thread Tools above the first post.

---

