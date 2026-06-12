---
title: "Partition Setup Question"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by Lucrin on 2010-11-13
Hello everyone,
Let me start off with my hard drive configuration:

HDD1: 300 gigs total (windows 7 drive)
HDD2: 400 gigs total (currently empty)
HDD3: 750 gigs total (External drive for data storage)

Ok so I want to install ubuntu to the second hard drive but only use give it a 50gig partition. I plan to use the other 350 gigs for installing software and such on my windows 7 installation. My question is how do I set up custom partitions to fit that way? I don't know what typs I need (swap, fat, etc) and how big to make each one. Thanks for the help.

EDIT: Also how do I know what device to select to install the boot loader to?

---

### Post by Lucrin on 2010-11-13
Seriously no one has even viewed my post yet? Sorry I don't mean to be impatient but I am quite literally sitting here at a total standstill with no way to continue until someone can answer my question.

---

### Post by Dr. C on 2010-11-14
Before installing Ubuntu I would set the BIOS do that HD2 is set to boot before HD1. GRUB2 will then be installed on HD2 MBR and the Windows boot loader will be left alone.

I would create 3 partitions on HD2. One linux swap with twice the amount of RAM on your system. One ex4 for 50 GB less that amount of the swap partition and the balance as an NTFS partition. This can be done using the live CD. In the live CD go to System > Administration > GParted Partition Editor.

Then Click install and select the set partitions manually option when promoted. Right click on the ex4 partition, select change and Use as ex4 For mount point select: / Then proceed with the Ubuntu install

---

### Post by Lucrin on 2010-11-14
Ok, so with a combination of your advice and my own research I almost have things working how I want. I went ahead and set the second hard drive to have the boot loader. I created 4 partitions as follows:

boot: 100mb - primary
swap: 6000mb - primary
/: 20,000mb - primary
home: 30,000mb - logical

This left about 320 gigs left unallocated on the hard drive. So I went back into windows and tried to create a simple volume to add that 320 gigs as my D drive but it says I can't because the hard drive already has the max number of partitions aloud. I know the max is 4 but it was my understanding that only primary partitions count towards that number and logical partitions don't. How can I adjust my installation to allow me to use the left over space in windows? Thanks again.

---

### Post by Dr. C on 2010-11-14
I would expand the primary partition that contains the logical /home to into the all the free space and the create a second logical partition for the 320GB NTFS partition.

---

### Post by Lucrin on 2010-11-14
> **Dr. C said:**
> I would expand the primary partition that contains the logical /home to into the all the free space and the create a second logical partition for the 320GB NTFS partition.
Can you explain how I would do that? I don't know which partition the logical home is in. Will windows be able to use the partition if it is shared with linux?

---

### Post by Dr. C on 2010-11-14
The /home logical partition is in an extended partition. I would boot from the live CD, Launch GParted and expand the extended partition. In GParted select partition > Resize move after selecting the expanded partition. Then create a second logical partition in the extended partition and format it NTFS. 

Boot into Windows 7 and go to Control Panel\All Control Panel Items\Administrative Tools\Computer Management\Disk Management and you will be able to see the new NTFS partition and assign it a drive letter.

---

### Post by Lucrin on 2010-11-14
Thanks a ton! Everything is working like I wanted now :)

---

### Post by Dr. C on 2010-11-14
You are welcome. May I request you mark the thread solved. Thanks

---

