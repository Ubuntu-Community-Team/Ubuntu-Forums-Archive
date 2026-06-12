---
title: "Questions about Restoring Home Partition"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by DaLazySapien on 2014-07-25
I haven't been able to find a clear answer online and was wondering if someone here could help me out. Currently I have Ubuntu 14.04 installed on a third hard drive. Windows 8 resides on my 60GB SSD and I have second drive that I've installed all Windows programs and personal files. I'll break it down for simplicity.

SSD: Windows 8
HD2: Windows programs (NTFS)
HD3: Ubuntu 14.04 (EXT4)

I still need to keep Windows 8 for a few games sitting on my Steam account but I would like Ubuntu to take advanage of the SSD's speed. I would like to shrink the partition on HD2 and install Windows 8 on the new partition to keep everything Windows related on that drive. Then I would install Ubuntu onto the SSD leaving HD3 as my dedicated Home partition. I'm familar with how to seperate the home partition in the installation process. Here is my question (finally ;)).

If I were to back up my entire /home folder can I just simply copy it over the newly created one? It seems like it would work but I don't want to get that far and have it fail. Thank you all for your help in advance.

---

### Post by Dreamer Fithp Apprentice on 2014-07-25
Yes, that will work. I can see why you ask. Sometimes things aren't as simple as they look. But home is. Be sure you copy the hidden files, the ones with names that start with "." That's really the only potential gotcha. Personally, I like to set my file browser to always show all "hidden" files.

---

### Post by oldfred on 2014-07-25
With multiple drives I prefer to have each system fully installed on one drive with its boot loader. Or each drive can boot without any other drive. Then add data partitions from other drives for shared data, backups and anything else you want.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by DaLazySapien on 2014-07-26
Thank you both for you replies. That's all the information I need and then some.

---

