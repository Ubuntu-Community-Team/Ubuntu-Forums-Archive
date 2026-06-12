---
title: "Windows 7 dual boot"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by jman340 on 2010-06-14
Hello,
I'm new to the forms and somewhat new to Linux. I just purchased a new HP lap top with Windows 7 already installed. I've read several tutorials on installing ubuntu along with windows, but cannot get past the partitioning.

So far, I've booted into Windows, pulled up device manager, and can see the current partitions of my drive. I shrunk the C drive, cutting it in half. I've tried several combinations with no luck being able to see them during the ubuntu install. I've tried just shrinking the drive, leaving the unformatted space, formatting the space without assigning it a drive letter as ntfs, formatting them without assigning a drive letter and not as ntfs, but still cannot see the space for the ubuntu install. All the tutorials I've read state that I should see the space as unallocated. I don't see it when I start ubuntu from the disc and use gparted. 

Any ideas? I don't want to lose windows 7. I've got a back up disc that I can use if I have trouble. Also, I'm using the 10.04 lts.

Thanks
John

---

### Post by kansasnoob on 2010-06-14
First choose to just "try Ubuntu without installing" when presented with the choice. Then from the Live Desktop go to System > Administration > Gparted. 

Next take a screenshot of Gparted using the tool in Accessories. You can then attach the screenshot using the "paperclip" thingy at the top of these reply boxes.

And never resize a Windows partition with anything but it's own tools!

---

### Post by jman340 on 2010-06-14
I'd take a screen shot, but have no obvious way to save it while running ubuntu on a disc. In Gparted, there are four partitions, they are as follows:

Partition/File System/Label/Size
sda1/unknown/SYSTEM/992.50KiB
sda2/ntfs/ /199MiB
sda3/ntfs/ 158.3GiB
sda4/unknown/RECOVERY/139.6GiB

I know better than to resize the partition outside windows.
The above is with the c drive partition downsized by 126.26 GB using the Disk Management tool from windows.

It shows it as RAW Healthy space.

Thanks
John

---

### Post by wilee-nilee on 2010-06-14
> **jman340 said:**
> I'd take a screen shot, but have no obvious way to save it while running ubuntu on a disc. In Gparted, there are four partitions, they are as follows:

Partition/File System/Label/Size
sda1/unknown/SYSTEM/992.50KiB
sda2/ntfs/ /199MiB
sda3/ntfs/ 158.3GiB
sda4/unknown/RECOVERY/139.6GiB

I know better than to resize the partition outside windows.
The above is with the c drive partition downsized by 126.26 GB using the Disk Management tool from windows.

It shows it as RAW Healthy space.

Thanks
John

You save it to the desktop come to the forum, with the live cd upload it with the paperclip icon in reply and post it. The size of the recovery would not be 139 gigs so a screenshot, would be helpful. It looks though from what you have posted that you have 4 primary partitions so the screen shot will confirm this.

The easiest way to take a screen shot is to open the program from menu-accessories-take screenshot, then choose select area to grab which turns the cursor inti a + which is then run corner to corner diagonally from top to bottom across what you want to save, then save it to the desktop

---

### Post by jman340 on 2010-06-14
Screen shot....

---

### Post by wilee-nilee on 2010-06-14
So the large recovery sad4 was what you built is this correct? If that is the case I don't see a built in recovery partition, I see sda1 seems like hp stuff sda2 looks in size to be a boot partition usually if installed with a dvd it is 1/2 the size 100mb sda3 the main OS is sda3.

Did this computer come with backup discs? As it either has the recovery for the OS built into sda3 or was sda4 or it's been removed, can you elaborate. Also the model would be helpful if this information or some is not known by you.

---

### Post by oldfred on 2010-06-14
Your entire issue with partitions is you have used all 4 as primary partitions. I think windows does this intentionally to prevent other systems from being installed. You have a "system", the 100mb windows boot partition (that is usually hidden), your main partition, & the recovery partition. If your recovery or system allow writing CD or DVDs to make recovery backups and repairs disks you must do that. You may need them. Often the recovery CD is really just an image of the hard drive as installed and if used deletes everything and makes it like new including all the stuff you do not want. And you lose any changes you have made.

You will have to decide what you want to do. You can delete either the system or recovery partitions but you lose whatever they are. You may be able to back them up and put back into a logical partition but then they may not work. If you really want you can move the boot into the main partition, but the boot is also the live version of you recovery software.

Another option is another drive. Some run even from 16GB flash drives for a while.

---

### Post by jman340 on 2010-06-14
The partition I built does not show. See the attachment from device manager in windows. The model is G62-140US. It did not come with backup discs, but I did create them before I embarked on this adventure.
sda1 looks like the HP Tools partition
sda2 looks like the SYSTEM partition
sda3 I believe was the c drive that I shrunk
sda4 is marked recovery, but I see the partition in windows for recovery is only 12.54 gig, not 139. Could that be the partition that I created? It only shows 126 gig in windows.

---

### Post by oldfred on 2010-06-15
You did not create a partition just empty space that, if you did not use all 4 primary you could use to create another partition.

Windows does not show partitions in same order. 
The 100mb system(sda2) is the windows boot. The C: (sda3) is your main partition and the other two are HP tools (sda1) & recovery(sda4)

---

### Post by wilee-nilee on 2010-06-15
> **jman340 said:**
> The partition I built does not show. See the attachment from device manager in windows. The model is G62-140US. It did not come with backup discs, but I did create them before I embarked on this adventure.
sda1 looks like the HP Tools partition
sda2 looks like the SYSTEM partition
sda3 I believe was the c drive that I shrunk
sda4 is marked recovery, but I see the partition in windows for recovery is only 12.54 gig, not 139. Could that be the partition that I created? It only shows 126 gig in windows.

Interestingly the 12 gig recovery and the 126 gig before it in MS add up basically the amount in sda4 on gparted. 

If it was me besides having the backup you made I would see if HP has a straight install oem disc set, so you have all your ducks in a row, and can just remove the recovery listed in gparted which seems to show both as one unidentified. oldfred knows much more about this so I would defer to him.

---

### Post by oldfred on 2010-06-15
I do not know about HP and its recovery. Every mfg seems to do it a little different but I think it was Microsoft not wanting them to include disks.
You will have to decide what to backup and delete or another drive.

---

### Post by Mark Phelps on 2010-06-15
I've worked with HP over the years and they NEVER provided recovery disks by default, at least, not on any of the systems I purchased.  They used to be willing to sell you a set of disks, and for a while, they would even let you download the images (for a fee), but recently, they stopped doing even that -- at least when I tried to get a set out of them.

Yeah, I know it's easy to blame MS on this (and that MAY be true!), but I would bet more on HP saving money than on MS telling them not to provide disks.

---

