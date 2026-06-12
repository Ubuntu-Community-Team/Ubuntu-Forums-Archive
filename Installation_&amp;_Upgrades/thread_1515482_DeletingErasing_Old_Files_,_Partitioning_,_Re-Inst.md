---
title: "Deleting/Erasing Old Files , Partitioning , Re-Installation"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by mailc on 2010-06-22
I am giving away a laptop with dual boot XP and Ubuntu. Partitions: 
 - /dev/sda1 : Dell Utility 41MB FAT ;
 - /dev/sda2 : 55GB NTFS ( XP);
 - /dev/sda3 : 20GB Extended (10GB ext4 /, 1.5GB ext4 Boot, 2.0GB Swap, 6.5GB ext4 Home);
 - /dev/sda4 : 5.0GB Dell REstore.
 To erase all old files, I plan on burning an Ubuntu live CD and enter in the terminal:
 'sudo dd if=/dev/zero of=/dev/sda2 bs=1M ' and also :
 'sudo dd if=/dev/zero of=/dev/sda3 bs=1M'
 and leave sda1 and sda4 untouched just in case the new owner wants to reinstall Windows in the future.
  But how should I use the free 75GB ? Install Ubuntu  on a 35GB extended partition and leave the remaining 40GB empty for XP,  if wanted?  
Or should I use the entire 75GB for Ubuntu ?
Thank you for your help

---

### Post by dabl on 2010-06-22
Nothing you have written indicates that you need a separate partition for /boot -- you can lose that one.

It's not clear whether you are setting up the drive from scratch, or just preserving the existing setup.  If it is the latter, then yes, your "dd" approach is a good way to clean off the old data from those partitions.

If you're starting with all new installations of both OS's, then I would advise making a GParted Live CD, and use that to (a) delete all the partitions, (b) make a new partition table, and (c) set up new partitions (without /boot).  Doing that, only a data recovery professional would ever be able to discover any prior data on the hard drive, and you could skip the "dd" thing.

The extra 75GB would be a nice space for general data storage.  If the new user doesn't know/appreciate the benefits of running Linux, then you probably should format it NTFS and let it be a Windows storage drive.

---

### Post by mailc on 2010-06-22
> **dabl said:**
> ....
  It's not clear whether you are setting up .......

A clarification or two is in order:
 - the new owner wants Ubuntu but he also wants to have the option to return to XP
 - the TOTAL availabel space is 75GB (55+20+5= 75)
 - I am not concerned about the grub LOGICAL partition, one way or the other


 - Since the Dell Restore partition and the Dell Utilities partition will not be affected, I was just wandering if I  should install Ubuntu 10.04 on the entire partition available (75GB) or leave some  space empty for XP,  if needed.


  And I am asking the question because I was told that,  once invoked, Dell Restore will overwrite the entire drive , delete Ubuntu and install XP.  A new repartitioning will need to be done and Ubuntu will need to be reinstalled. 


 Is this correct?

---

### Post by darkod on 2010-06-22
Yes, the restore partition usually wipe the whole disk and set up the factory state, in other words XP taking the whole hdd in single partition, very rarely two partitions, one for system, another ntfs for data/spare.
Depending how far you want to go, you might set up 10.04 for the new owner, to help him/her out especially if new to linux.
As far as ubuntu install is concerned, I would make a /, swap and /home setup, to allow easier clean installs in future.
As for the question how to split the 75GB between ubuntu and eventual XP partition, again talk to the new owner if it's a friend. If not, it also depends if you will install it for him/her, because if you're not, then you don't need to make any decision about the partition sizes.

---

