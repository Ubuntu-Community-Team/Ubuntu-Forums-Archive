---
title: "Partition question..."
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by d_stroyer on 2013-07-11
So I have decided to dust off my old netbook and run it as just an Ubuntu machine. Now, I had both Win7 and Ubuntu installed before. I got GParted and I deleted my Windows partition. I have used GParted before, but not as I did this time. So I'm just gonna to post the questions I have about it as a list:

1. I see 2 banks of unallocated space. Is this basically 105gb that is not being used at all?

2. How can I make this unallocated space available for use?

3. I am a little confused on extended partitions so here goes...sda3 contains the whole partition I am already using for Linux in total. sda5 is what is running my actual Linux OS and sda 6 is just swap space correct? And in sda3 there is 46.65GiB unallocated space included. Is this space that is being not available at all?

Thanks for any help. I looked through a few other posts, but I find it's easier if I just post since my situation is a little different than any of the posts I have come across so far. I attached a screen shot so I hope that helps some.Thanks.

---

### Post by oldfred on 2013-07-11
I do not like moving partitions left. That takes a lot longer as all data has to be copied and any power failure corrupts system. But whatever changes you make, you should have good backups.

All partition work with gparted needs to be done from liveCD/CDV/Flash version or separate gparte or PartedMagic liveCDs. You also will have to click on swap and right click swap off as liveCD like to automount swap to speed things up. 

Since the unallocated at the right side or end of drive is already in the extended partition, you should be able to move swap all the way right. You could delete swap and recreate at end but have to update fstab with new UUID. Moving it should not change UUID. Then you could expand your / to include all of the unallocated inside the extended partition. But I tend to prefere / (root) partitions of 25GB and separate /mnt/data partitions or a separate /home.

You can create a new partition in the first unallocated as ext4 and mount it as a data partition or /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

      
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by d_stroyer on 2013-07-12
I just ended up plugging in a Ubuntu Live USB and running a new install form there and starting over. Thanks for the tips though, it helped a little at least.

---

