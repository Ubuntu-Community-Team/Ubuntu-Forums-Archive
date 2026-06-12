---
title: "Too Many Primary Partitions?"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by erixoltan on 2010-06-12
I just got a new HP laptop with Windows 7 on it.  In contrast to my other desktop system I really need to have a dual boot on this one, since I need to run a few things that will only work in Windows.  

I used a live CD and ran gparted to resize my Windows 7 Partition down from 444GB to 230GB which should be plenty.  Then I couldn't add an ext4 partition because there were already 4 primary partitions.  I deleted one of them that had some HP utilities on it that I figured I wouldn't miss. 

I can create a primary ext4 partition but I can't create a swap partition.  

I don't want to mess up my system if I can avoid it.  Does anyone know a way to make both a bootable Ubuntu partition and a swap partition when there are already 3 other primary NTFS partitions on the drive?  

Thanks,
Erik

---

### Post by oldos2er on 2010-06-12
Create an extended partition, then you can create as many logical partitions inside as you might need. See [https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition)

---

### Post by darkod on 2010-06-12
Only windows is limited and it has to be on primary partition. Create the / and swap as logical, they will go into single extended partition. You are allowed 3 primary + 1 extended which can hold 16 or even more logical partitions inside.

Use manual partitioning to control the size of the partitions, and when asked just select logical, not primary. It will allow you to create also logical swap.

---

### Post by oldfred on 2010-06-12
Did you check that win7 boots ok. 

We have been reccommending to use windows MMC to resize rather than gparted. Sometimes there are issues with gparted but they may be resolved now. Win7 after any resizing often wants to run chkdsk to recover from the change in size.

---

### Post by wilee-nilee on 2010-06-12
> **oldfred said:**
> Did you check that win7 boots ok. 

We have been reccommending to use windows MMC to resize rather than gparted. Sometimes there are issues with gparted but they may be resolved now. Win7 after any resizing often wants to run chkdsk to recover from the change in size.

That was my 1st thought even though herman suggests differently. Or at least suggests a closer look at using gparted this way.

---

### Post by erixoltan on 2010-06-12
Windows did run check-disk when I started up the system, but it didn't try to resize the partition or anything.  I was able to run Win7 OK.  

I will try the excellent advice to create an extended partition with multiple logical partitions inside it!

Thanks,
Erik

---

### Post by erixoltan on 2010-06-12
YAY that solved it.  I am typing this in my new Ubuntu and I've verified again that Win7 is still happy.  

Appreciate the quick help!!!!

---

