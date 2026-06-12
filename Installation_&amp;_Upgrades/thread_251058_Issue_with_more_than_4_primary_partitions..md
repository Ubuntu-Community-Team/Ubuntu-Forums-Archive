---
title: "Issue with more than 4 primary partitions."
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by brajan on 2006-09-04
Hi,

I am relatively new to Linux. I have been using Windows and other flavors of unix for quite some time though :)

The issue I have is as follows:
1. I have a dell Inspiron laptop partitioned in the following manner:

(Attaching the screenshot of partitions from the 'Gparted' tool below:)

I have 4 partitions already ie.
1. NTFS for Windows boot
2. NTFS for Windows backup
3. FAT32 - which is for dell system restore i believe
4. FAT16 - For dell windows diagnostics

2. Now I need to install Ubuntu on the system. Using GParted tool, I was tried to put in proper partitions.

After going through various documentation, I figured that I would be need a root(/) primary partition for Ubuntu, and another primary partition for swap.

For that I would need to merge the two NTFS partitions together and remove the FAT32 partition.
My questions are following:
1. Can I create an additional extended partition without removing the primary partitions existing now?
2. What would be the best way to go around the limitation of these 4 primary partitions?

Please let me know the best way around, till I'll play around with the live CD. :)

Cheers, Biju

---

### Post by brajan on 2006-09-04
I forgot to mention, I have Windows XP Prof version now. And I need to dual-boot with Windows and Ubuntu. I plan to put in some 16 gb for Ubuntu which I have already deallocated from my primary partion.

---

### Post by randell6564 on 2006-09-04
Hi!
You will probably get more help if you post your problem in the appropriate forum.

'Laptop Support'.

---

### Post by brajan on 2006-09-04
Hi,

I have posted on Laptop support thread also. Waiting for a reply though.

Cheers,
Biju.

---

### Post by confused57 on 2006-09-04
Maybe you could backup the FAT16, dell diagnostics partition to a external drive or usb pen drive...then delete the partition and make an extended partition.  You can the create as many logical partitions as you want within the extended partition. Ubuntu root and swap can be installed on a logical partition.

I've had my Dell for 4 years and have never had to use the diagnostics tool, although I may have to use it tomorrow.

I'm just a beginner, so you might want to wait for someone else who's more experienced with partitioning.

---

