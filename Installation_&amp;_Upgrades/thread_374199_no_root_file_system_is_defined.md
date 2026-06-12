---
title: "no root file system is defined"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by albertbc on 2007-03-02
This is a problem I find when trying to install Ubuntu 6.10 I start with live cd and click on install. At the fifth page I have 3 options regarding where to install the OS. 

1.Erase entire disk
2.Use the largest continuous free space
3.Manually edit partition table.

I select option number 2 as I have no experience on partitioning hard drives and I want to have Ubuntu and keep my windows xp.
I understand (maybe I am wrong) that with option number 2 the partition should be made automatically using all the free space I have on my harddrive (18 GB).

But After I select option 2 I get a message saying: no root file system is defined.  Anyone can help? Thank you very much.

I attach partition map of my harddrive in case it may help. It is a dell laptop.

Num   partition    type    status   used   size   start    end   label
1   /dev/sda1   fat16      32,17 MB   78,41 MB   0,03MB   78,44MB   
2   /dev/sda2   ntfs   active   51,726 GB   69,8 GB   78,44 MB   69,88GB   
3   /dev/sda-1   free   hidden   No disp   7,84   69,88GB   69,89GB   
4   /dev/sda3   fat32      2,876 GB   4,64 GB   69,89GB   74,53GB   Dellrestore

Should I first resize the "2   /dev/sda2   ntfs   " partition before starting the installation and taking option 2.Use the largest continuous free space ????

I have tried kubuntu and I get the same error message  :confused: 

Thanks a mil,
Al

---

### Post by chewearn on 2007-03-02
Yes.  Option 2 means find the largest continuous free space.  
You need to resize one partition to free up some space.  Free space simply means space not occupied by any partition.

---

### Post by albertbc on 2007-03-02
Many thanks for your quick reply,

just 2 more easy questions.

1. Would you recomend using qparted for doing the partitions while runing the live cd? I have read in some posts that it is better doing it from window$ with partition magic(Wich I thing is paying software).

2. Will the swap partition be made automatically If I take option 2 in the menu: "Use the largest continuous free space"

Many thanks again,

Cheers
:)

---

### Post by chewearn on 2007-03-02
> **albertbc said:**
> Many thanks for your quick reply,


No problemo. :)

> just 2 more easy questions.

1. Would you recomend using qparted for doing the partitions while runing the live cd? I have read in some posts that it is better doing it from window$ with partition magic(Wich I thing is paying software).

I have not used the Qparted to resize a NTFS partition, no idea how reliable it is.  Only used to clone an ubuntu partition from one disk to another.

I used to depend a lot on Partition Magic 8; it was rock solid, until I started using latest larger capacity harddisk; then it started to fail miserable, costing hours of Windows re-installation.  I search around, and found DriveImage XML.  It's a free Windows application that I used to clone my Windows partitions.  I don't think you can directly use it to resize, but you should at least be able to backup your XP installation, before attempting a risky change.  I learnt the hard way that you should have a second harddisk backup, ready to go, in case the first one borked.  Heck, what am I saying?  if you have a second harddisk, you should installed ubuntu on that harddisk instead.


> 2. Will the swap partition be made automatically If I take option 2 in the menu: "Use the largest continuous free space"
:)

Sure.  Swap will be created automatically.  Oh, wait, you already have 3 primary partition on that disk.  Plus one hidden partition.  Due to legacy reason, you can have up to 4 primary partitions on a single harddisk.  If you try to install ubuntu, the EXT3 will take up one more partition, then you are out.  Not sure how ubuntu installation will proceed after that.

I think you might need to clean up your setup.  Why do you have a FAT16 partition, and a hidden one?  You might need to consolidate your data to the FAT32 partition, then delete the FAT16 partition.  Maybe make a extended partition and put the FAT32 one inside it.  Well the options are many; you decide.

---

### Post by albertbc on 2007-03-02
Thanks! 

The situation looks worst now. I am not sure I now how to proceed with all that. I have no experience on managing partitions :confused: 

The system is a new dell laptop and I don't understand why there are so many partitions. Until now I though there was only one and I only know the content of the ntfs.

Do you think it might be dangerous to resize the big partition and try to install? Do the 2 new partitions for linux need to be primary?

Thank you again!

---

### Post by chewearn on 2007-03-03
> **albertbc said:**
> Thanks! 

The situation looks worst now. I am not sure I now how to proceed with all that. I have no experience on managing partitions :confused: 

The system is a new dell laptop and I don't understand why there are so many partitions. Until now I though there was only one and I only know the content of the ntfs.


Since it is a new Dell Laptop, it might be advisable to check with Dell on the purpose for all those partitions.  Plus, I am not sure if installing another OS will affect your warranty.  I have heard that some systems (e.g. IBM laptops) store system recovery code / data on hidden partition (though this is not a firsthand knowledge).

> Do you think it might be dangerous to resize the big partition and try to install?There is always a risk involved in resizing partition.  I have lots of success in the past, but also suffered from failures.  A single failure can cost days of down time, especially if you don't have immediate access to someone who know how to fix things quickly (example, if you need to send your laptop back to Dell).  You would have to judge for yourself.

> Do the 2 new partitions for linux need to be primary?
I think ubuntu can be installed in an extended partition.  I have no personal experience in this setup, though I have seen others in this forum, who have an extended partition, which is then holding the EXT3 ubuntu install as well as the Swap.  I'm not sure if ubuntu can automatically set this up during installation, or you have to do so manually.  Either someone else in the forum can comment, or you have to experiment by trial and error.  Note also that the extended partition itself will count as one primary partition.  That will means your harddisk will contains 4 primary partitions and a hidden one.  Not sure that will work too.

---

### Post by Robert98374 on 2008-02-26
Hello!
Sorry using an old post but its about the same error message."No root file system is defined.
Please correct this from the partitioning menu."
[http://ubuntuforums.org/search.php?do=process](http://ubuntuforums.org/search.php?do=process)
Basically i am trying to format the Hard drive to fat32 so both systems can use the 320gig WD. My understanding is that it would be the easiest way so both can use the information on it.

What does it mean when it says correct it in the partitioning menu? i had Kubuntu installed with the default option hopping it would then allow me to go back and reformat it to fat32...yeah it didn't work...Thanks for the advice before hand!

---

### Post by louieb on 2008-02-26
Probably berter to start a new thread. 
But a partial answer to your question is you must install Linux in a partition using an open source file system such as ext3 (default for Ubuntu). That means you can't use fat or or NTFS to install Ubuntu.

You can create a separate data  partition to share data between Windows and Linux, and format it anyway you want.

---

### Post by jken146 on 2008-02-26
You can read from and write to NTFS partitions in Ubuntu.  You cannot install Ubuntu on an NTFS or FAT partition.  My recommendation is to put Windows on an NTFS partition and Ubuntu on an ext3 partition.  If you really need to access Ubuntu's root partition from Windows, you can use the drives from [http://fs-driver.org](http://fs-driver.org).

---

