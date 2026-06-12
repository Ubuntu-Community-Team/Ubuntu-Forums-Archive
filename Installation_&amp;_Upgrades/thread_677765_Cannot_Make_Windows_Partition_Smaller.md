---
title: "Cannot Make Windows Partition Smaller"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by stephenbrazier on 2008-01-25
Im trying to partition my 20GB hard drive on the Ubuntu **7.04** Alternate CD. Currently, I have a Windows NTFS partition that used all 20GB of the drive. I asked the CD to partition it to 50% (this should be no problem as there is space to do this) but the instalation screen goes Red and it says there was an error and the partition can not be resized. I realy want to duel boot and I cant use Ubuntu without XP at the moment.

I do have a Windows Xp Installation CD, so if It means deleting the current partition, making a Ubuntu one using 50%, then reinstalling Windows and tell the installer to use the free space, I am willing to do so.  Or, is  there any windows applications i can use to resize the current XP partion to 50% then installing ubuntu?

Or all my ideas lame and should i do something else?

Thankyou very, very much for your help.

The sooner im on ubuntu the happier i'll be.

---

### Post by lswest on 2008-01-25
be sure to defragment your XP drive before you resize, as some data spreads out and can cause problems with partitioning.  Also, be sure to resize it so you still have enough extra space for the virtual memory allocated to XP

---

### Post by Porpoise on 2008-01-25
> **stephenbrazier said:**
> Im trying to partition my 20GB hard drive on the Ubuntu **7.04** Alternate CD. Currently, I have a Windows NTFS partition that used all 20GB of the drive. I asked the CD to partition it to 50% (this should be no problem as there is space to do this) but the instalation screen goes Red and it says there was an error and the partition can not be resized. I realy want to duel boot and I cant use Ubuntu without XP at the moment.
 
I do have a Windows Xp Installation CD, so if It means deleting the current partition, making a Ubuntu one using 50%, then reinstalling Windows and tell the installer to use the free space, I am willing to do so. Or, is there any windows applications i can use to resize the current XP partion to 50% then installing ubuntu?
 
Or all my ideas lame and should i do something else?
 
Thankyou very, very much for your help.
 
The sooner im on ubuntu the happier i'll be.
 
Bear in mind that you can't resize an active partition - you need to boot from another source to make that partition available without being active. I use a PartitionMagic boot disk for that purpose (as it can resize partitions without destroying the data).
 
However, if you're going to be running a duel-boot Ubunto/Windows system, I'd say you're probably going to need to upgrade that 20Gb disk to something an order of magnitude bigger...  I've just had to upgrade my 30Gb drive in my laptop to an 80Gb.

---

### Post by stephenbrazier on 2008-01-25
> **lswest said:**
> be sure to defragment your XP drive before you resize, as some data spreads out and can cause problems with partitioning.  Also, be sure to resize it so you still have enough extra space for the virtual memory allocated to XP

I already defragmented it. I wont lemmie resize it.

---

### Post by stephenbrazier on 2008-01-25
Would I be able to delete all data on my hard drive, then say put 50% for Ubuntu, then install ubuntu, then wack in my Windows CD and say that sould use the rest. Im not bothered about losing my data as its all backed up on my pen drive.

I just want to make sure it works before I go fiddling.

---

