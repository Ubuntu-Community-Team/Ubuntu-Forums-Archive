---
title: "[SOLVED] resize operation failure"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by bogdan_mbe on 2008-10-17
Hello to you all!

I need some help over here about installing Ubuntu. 

I have a Sony Vaio with Windows Vista Business SP1 installed (by me, free of any crapware), and I want to install Ubuntu 8.04 LTS .

There is a 149.05 GB hdd, being split as follows:
•	C:\ ntfs partition of 30 GB System, Boot
•	D:\ ntfs partition of 3 GB Page file
•	E:\ ntfs partition of 70 GB 
•	F:\ ntfs partition of 30 GB
•	Unallocated space of 16.05 GB.
This is exactly what Disk Management from Computer Management shows me. I left the 16.05 GB of unallocated space on purpose, I want to install this ubuntu there.

So, I insert the ubuntu 8.04 LTS cd, restart the notebook, and the installation process starts.
Step 4 is about Preparing the disk space. And it shows me the following options:
•	Guided - resize SCSI1(0,0,0), partition #3 (sda) and use free space (right bellow a slider for adjusting the new partition size)
•	Guided - use entire disk
•	Manual.
If I select first option (Guided - resize ...) and I move the slider in order to make a 16GB partition for ubuntu, a warning pops out about not being able to undo this operation, I click continue, and then, after a please wait message, it tells me: Resize operation failure - an error occurred while writing the changes to the storage devices. The resize operation has been aborted.
So back to step 4.
If I select the third operation - Manual, and this is what it shows me:
/dev/sda
	/dev/sda1			Size: 1 MB, 		Used: Unknown
	/dev/sda2	ntfs		Size 32212 MB, 	Used: 0 MB
	/dev/sda3	ntfs		Size 127827 MB, 	Used: 0 MB

And this looks nothing like the information shown in Disk Management back in Vista. Anyway, If I try to select one of the above, click Edit partition, and I enter a size for a new ext3 partition for Ubuntu (also I select the mount point), click OK, Forward, but again - Resize operation failure - an error occurred while writing the changes to the storage devices. The resize operation has been aborted.

To sum up: 
-	Why can’t I see all the partitions as shown in Disk Management, in order to select the one with unallocated space to install ubuntu on it.
-	How can I fix the “resize operation failure” issue ?


sorry for this long post, i hope that if i state the problem clear enough, somebody will answer me quickly.

---

### Post by Fire_Chief on 2008-10-17
Are the existing partitions all primaries? Most BIOSes have a limit of 4 primary partitions on a drive. If you want to have 5 partitions, then try creating the 4th as an extended partition using the rest of the disk space. Then inside the extended partition, you can create a logical partition for your F: drive and one or more logicals for your Ubuntu installation. Also, I'd suggest using a third party tool such as the GParted Live CD to make the changes.

Cheers!

*EDIT*  Ah...after re-reading your drive layout it looks like the D, E, and F drives are all logicals within Windows instead of actual partitions (all on /dev/sda3). You would need to complete redo the physical partition layout for those drive letters. That means pulling all the data off, destroying the /dev/sda3 partition, building it as individual partitions as I described above, then moving all of your data back once you reassign the drive letters to the new partitions in Windows.

---

### Post by bogdan_mbe on 2008-10-17
thanks fire_chief for the quick reply. 

i guess i will redo the physical partition layout of /dev/sda3 as you said. hope it works.

anyone who has a better ideea, feel free to bug in

---

### Post by bogdan_mbe on 2008-10-17
indeed, just as fire_chief suggested, gparted live saved the day. thank you. 

(right now i am looking for a way to close this thread, and for a thank you button)

---

