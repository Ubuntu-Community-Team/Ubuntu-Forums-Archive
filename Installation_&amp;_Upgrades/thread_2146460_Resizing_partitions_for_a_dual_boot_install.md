---
title: "Resizing partitions for a dual boot install"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by urban120 on 2013-05-18
Hello i have windows 7 on my computer but it is getting slow so i decided to try linux. I would like to install ubuntu 13.04. But when i installed windows 7 i have set two partitions 1. for os, installs and unimportant data 2. for important data so if there is a need to reinstall windows i won't have problems with restoring data. Now i don't want to remove windows but i want linux too. I am thinking of having a windows partition, linux partition and data partition.
 My disk has 1,4 TB (1397,26GB on disk menegment) 1. partition 683,59 GB 2. 713,57 GB + system partition 100MB
How can i resize partitions?
How much can i shrink windows partition so i can have OS+windows programs(mostly games)?
How big should linux partition be(for ubuntu and programs)?
Can i shrink both partitions to make linux partition (any problems with holes in allocated disk space)?
Can i shrink windows partition and make linux partition and expand data partition?
Can i even use a NTFS patition for data on both windows and linux?

I would like to keep all my data without backup (at least on my data partition).
I am experienced so don't think i will have problems with more advanced options.

Thank you in advance

---

### Post by oldfred on 2013-05-18
Backup is a good idea.

Linux reads & writes NTFS partitions. Best to set system partition as read only as the Linux NTFS driver shows all the normally hidden files & folders. That can lead to accidents. In Windows I always changed to show them and regularly had to make repairs. 

One reason Windows slows down is that its partition gets too full. Best to keep 30% free, as at 10% free it becomes almost unusable - no room for defrag.

Use Windows data tools the shrink the Windows system partition. But do not create partitions as it will try to convert to dynamic partitions which do not work with Linux. Reboot several times so it can run chkdsk and make whatever repairs it does on a resize.

How many primary partitions are used? With MBR you can only have 4 and most Windows 7 systems use all 4. Windows has to boot from a primary partition, but Linux works just fine from logical partitions. So you have to use one primary to become the extended and can have essentially an unlimited number of logical partitions inside the extended. If you have unallocated space it should be in the extended as otherwise you may not be able to use it.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
This is one suggestion. Others may have different suggestions and whatever you want depends on how you will use system. My own optimal partitioning plan is usually obsolete after a year or two.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by urban120 on 2013-05-18
Ok after half an hour of comprehending, researching and thinking what to do
 I checked i have only 3 partitions and if i understand correct i need to free some space and make a linux(ext4) partition.
[IMG]http://shrani.si/f/1o/lp/2I7VLVu0/disk-menegment2.png[/IMG]
 C: Win 7 D: data 
Ok i plan to:
1. Shrink C partition to about 200 GB (I will move some data to D)
2. Expand D to about 900 GB
3. Run ubuntu 13.04 DVD and install and create partition in free space(allocated disk space)(about 200GB)
Is this OK?
  Can i damage or lose data in D partition if i expand it?
Which data do i risk if i don' backup and do this?
I have read that often used data should be together to minimize disk head movement would it be better if take from D partition and make linux partition there (so D partition is in the middle)?
  I don't intend to interact from linux(OS) with windows partition and vice-versa.

---

### Post by oldfred on 2013-05-18
While almost all the time you can resize and move partitions around. The only time it does not work is the one time you are in a hurry and do not do a backup. If you have a power failure for any reason in the middle then the partition move will be corrupted. 
Moving partition left takes longer and has a bit more risk as all the data has to be moved. Shrinking from the right is usually quick if you have defragged first so end of partition does not really have much data. 

I like to keep system data together in smaller system partitions. Linux does not fragment like Windows NTFS so that is less of an issue with Linux.

You can only have one extended partition with all the logical partitions in it. I usually make that at the end of the drive. Windows occasionally does not like Linux partitions as it does not see them and can rewrite a partition table incorrectly. That usually can be repaired, but that is part of why I prefer the extended to be last.

---

### Post by urban120 on 2013-05-18
OK i will back up most important files shrink D partition form the right so i will have extended partition at the end of the drive.
Do i have to make extended partition with Gparted or will linux installer do it automatically when i install linux?
Can i extend partition from the left?

---

### Post by oldfred on 2013-05-18
You have to move partitions left, you can only expand or contract from the right.
I prefer to use gparted as then the partitioning does not get confused with installing. It seems a tad easier with gparted. But you can do just about everything with the installer, now. Even if you partition in advance you still have to use Something Else as it does not know what you intended partitions for. So on a partition select change, use as ext4, check format box (unless previous installs /home), and mount / , /home, etc. If swap already exists it will find it otherwise you have to create it also.

---

### Post by jamesisin on 2013-05-18
I use GParted (included in any of the Ubuntu LiveCD's) to move/resize partitions.  Anytime that you move the front of a partition (either moving the partition itself or resizing at the beginning edge of said partition) Windows will lose track of where that partition is located.  If you insert your Windows 7 installation media it will detect the problem and fix it (usually).  I had to do this when I (finally) deleted my Vista partition and moved my Win7 partition to the left to fill that space (thus moving that newly emptied space toward the end of the drive where my data partition lives).

The other important thing about installing Ubuntu is remembering to run sudo update-grub after you have installed everything so that GRUB can scan for and create entries for all of the available bootable partitions.

It's already been mentioned above that you'll need to use Extended partitions.  The Windows MBR will only acknowledge four primary partitions.  So you get four primaries and everything else has to be located inside them either directly or as extended partitions.

You might find this article useful:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

---

### Post by urban120 on 2013-05-20
I have installed ubuntu on my computer i used gparted to contracted my second (data) partition since i was not full and made an 200 GB extended partition at the end of the drive where i installed ubuntu.
I will maybe in the future i will move other partitions or i will clean whole disk and install everything from scratch.

Thank you all for your help!!!

---

### Post by oldfred on 2013-05-20
Glad you got it installed ok. :)

---

