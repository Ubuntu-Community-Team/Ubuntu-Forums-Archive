---
title: "Rearranging my partitions"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-01-13
Hi Gurus.
I have been using Ububtu for about eight month alongside window$ 7,did a successful upgrade from 11.04 to 11.10 and pretty much happy with my system with an exception.

Currently, i have a basic partition scheme as follows:

/dev/sda1  -  60gib for win 7 os
/dev/sda2  -  176.18gib ext4 as / 
/dev/sda3  -  ntfs for data sharing between win7 and ubuntu
/dev/sda4  -  an extended partition
/dev/sda5  -  a 1.91gib logical partition for Linux-swap
(as in the attached image "Current_partition_scheme".)

However, [B]there are 2 extra unallocated spaces in my drive which wasn't created by me and neither do i know what is that for. 
[/B]
So, I would very much like to know what was that extra 1 Mib and 2.34 Mib unallocated spaces created for ? ? I realized that there are 3 Primary partitions and 1 Extended partition and so i won't be able to simply make a new volume out of that unallocated space. I want to know how i can merge those 2 unallocated spaces ? ?:confused:

Next, since i have  / and /home in my same partition, i would also like to have a new partition for /home. 
I have been following two links
[ [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) and [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866) (this might be old, will it still work ? ) ] for understanding how /home can be created in a pre-installed ubuntu system. Currently im not worried on how to achieve the processes mentioned in the links.

**So**, [B]i would first like to manage my existing partitions and then create an ext4 partition for /home so that i can later migrate to a separate /home partition. How can i achieve this?


Thanks in Advance.
Regards,WinuxUser.
[/B]

---

### Post by oldfred on 2012-01-13
You only have tiny unallocated, which now is part of the leftovers on the new rounding to 1MB partitions. You used to have some unused space before but now it is large enough that the rounding shows it. One user that tried to change things messed up his system royally, so I do not recommend any changes.

You have a lot of data in your / (root), so you do not have a lot of room to work with. Do you have it fully backed up?

I have now gone to keeping /home inside my / but keep / at about 25GB and link in folders from data partition(s). I have a NTFS shared and a ext3 data partition which then I link into /home.

---

### Post by nipunshakya on 2012-01-13
Thank You for your quick reply oldfred.
> **oldfred said:**
> You only have tiny unallocated, which now is part of the leftovers on the new rounding to 1MB partitions. You used to have some unused space before but now it is large enough that the rounding shows it. One user that tried to change things messed up his system royally, so I do not recommend any changes.

Keeping that in mind, i won't make changes now. I thought those spaces were something else:D

> **oldfred said:**
> You have a lot of data in your / (root), so you do not have a lot of room to work with. Do you have it fully backed up?

I just have only a few of them backed up. So i thought of making a separate /home so that later, i won't have to loose any of my data if an upgrade fails(Just in case). But then following the first community document was reliable one. But isn't the second link i am referring to a bit old? ?  i mean it was written in 2005 ! (please see my post #1 for links and recommend me something)


> **oldfred said:**
> I have now gone to keeping /home inside my / but keep / at about 25GB and link in folders from data partition(s). I have a NTFS shared and a ext3 data partition which then I link into /home.

i am planning to allocate 30gb for / and then the 146.18 gb for my new /home. But then, i realize that i haven't backed up all my data from the current / where all my stuffs lie. Somewhere i learnt that i can't go from extending a primary to logical and vice versa. In my context, i don't have enough space here. I might know what to do, but i am getting confused here on how should i begin with  . . .  :confused:

**1. should i free my / partition from the data i stored in it and then divide / into two partitions: / and /home? (will following **[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)[B] lead me right?)
2. if i intend to use the 60gb NTFS partition as /home, should i first format it to ext4 and then use it as /home? i guess NTFS isn't considered as good for /home , is it?[/B]

Regards,WinuxUser

---

### Post by oldfred on 2012-01-14
Backups are always important. Hard drives fail, we make mistakes, and sometime software does things it should not.

I normally suggest a shared NTFS partition if dual booting from Windows. I still have my NTFS partition with Firefox & Thunderbird profiles in it even though I almost never boot XP anymore. Just never reorganized and it works.

Your /home has to be a Linux format - ext4 or ext3 are most common, but it cannot be a Windows format like FAT32 or NTFS.

I still suggest the link you have for moving /home. I read two other suggestions, but the only difference was one used cp -a and the other used cpio for copy command. I prefer rsync so suggestion is still good. Basically you copy all your /home into a new partition (you do not look like you have room), edit fstab to mount new partition and then when it is working houseclean out the old /home that is inside / (root).

I do most of my major reorganizing when I get a new larger hard drive and have lots of room to work with. Since I know drives do not last forever, I usually upgrade a drive every 2-3 years.

---

### Post by nipunshakya on 2012-01-14
^^^^^Thank you very much guru for your support. I will keep this thread alive until i get my job done. Thanks a lot.

Regards,WinuxUser

---

### Post by fantab on 2012-01-15
You are better off without separate /home. Personally, I use just a LINUX EXT4 partition to store my Data. You can either automount it with system start or Mount it whenever needed. 

One of the reason I do this is because I find version Upgrades almost always troublesome and I prefer Clean Install of the newer Ubuntu version than Upgrade. And when I do a clean upgrade I don't have to worry about losing my Data and go through the BACK UPS and restorations. Yes, If you have a common / and /home you will lose your preferences and will have to customize again. But then I Like customizing all over again. I have this Linux Data Partition shared between THREE LINUX DISTROS. 

As suggested by oldfred, you can make this partition NTFS if you want to share data with windows. 

In the end its a matter of personal choice and preferences... I hope you will consider the suggestion to have a separate Data Partition than have a /home.

---

### Post by nipunshakya on 2012-01-15
> **fantab said:**
> You are better off without separate /home. Personally, I use just a LINUX EXT4 partition to store my Data. You can either automount it with system start or Mount it whenever needed. 

One of the reason I do this is because I find version Upgrades almost always troublesome and I prefer Clean Install of the newer Ubuntu version than Upgrade. And when I do a clean upgrade I don't have to worry about losing my Data and go through the BACK UPS and restorations. Yes, If you have a common / and /home you will lose your preferences and will have to customize again. But then I Like customizing all over again. I have this Linux Data Partition shared between THREE LINUX DISTROS. 

As suggested by oldfred, you can make this partition NTFS if you want to share data with windows. 

In the end its a matter of personal choice and preferences... I hope you will consider the suggestion to have a separate Data Partition than have a /home.

Sir, frankly speaking, i don't know about other types of partitions and mount points except /, /home and /usr and some others(rest i get confused). The only reason for me to have a /home partition seperated was because i wanted my stuffs to be safe after updates..( I have to run on low spaces and thats the main reason why im afraid to have my stuffs within the root.) I didn't realize this problem before.

I already have an NTFS to be shared between the two OSs. I want a separate partition for just ubuntu because by the time the LTS is released, im planning to completely switch to Ubuntu forever and ever. :D
So i'd pretty much like to know what mount point is your LINUX EXT4.(or are u saying u simply use / for everything? ??:confused: i got confused here.)

I go through [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview) once a day, still, i dont get an idea of what is being said.(Hate to memorize :D )

Basically, till next release, i want a separate / and /home. Please suggest me if i need to change other things too. :)


Thank You.
Regards,WinuxUser

---

### Post by oldfred on 2012-01-15
I normally suggest the separate /home for new users as it makes a complete reinstall a bit easier.  I only had /, swap & a shared Windows partition for a couple of years.

But I have progresses further as when I upgraded from 32bit to 64bit I had a new hard drive & lots of room. So I installed my / (root) into a new / and kept the old root. But I did not want to share the user settings in /home and found they are actually pretty small. My /home is about 2GB with most of that my .wine with the Windows version of Picasa. So I went to a separate /data partition where all the user data like Documents, Music etc is kept and some of the hidden folders that programs store lots of data like my Kmymoney folder.

---

### Post by nipunshakya on 2012-01-16
Thank you sir. I think im gonna go with 15gib of a / , 10gib for /home and rest of the space to /data. That way, i can have my application preferences as well as no worries to loose my data 

Thanks for watchin my back oldfred. Thanks everyone for your time.
Satisfied my heart and mind. [SOLVED]
Regards,WinuxUser

---

### Post by oldfred on 2012-01-16
Sounds like a plan.

Realize that whatever is your best partitioning plan today, it will change tomorrow as you learn and change what you are using Linux for.

---

### Post by nipunshakya on 2012-01-16
> **oldfred said:**
> Sounds like a plan.

Realize that whatever is your best partitioning plan today, it will change tomorrow as you learn and change what you are using Linux for.

The only thing that doesn't ever change is change itself guru.:D ... all these preparations, well to give a warm welcome to the new LTS. I know its 3 months far, but im excited for it.

---

