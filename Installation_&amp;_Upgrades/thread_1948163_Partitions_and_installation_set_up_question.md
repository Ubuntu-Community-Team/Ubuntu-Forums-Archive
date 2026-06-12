---
title: "Partitions and installation set up question"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by Zettaichi on 2012-03-27
Hi guys, I'm still getting used to linux and altho I have made it work almost the way I want it I still have some basic knowledge questions that I have had a hard time finding more info about. So hope I'm posting this in the right place.

In my system I have 2 Hard drives
1. 128Gb SSD
2. 1Tb Disk Drive.

This is what I'm trying to do. As must people I came from windows so i'll try to explain it to the best of my abilities. 

in windows I had my SSD as C: and my Disk Drive as D: (I understand the basics of how linux partitions work and I understand it more or less the same but with "folders like names"). What I used to have was "C:" <<SSD>> as my Operating system and some of the heavier softwares (like my main games and so on) and "D:" <<Disk Drive>> as my everything else drive (less use programs, my main drive for Documents videos and other trash information that i did not want in my SSD).

So I want to do something similar to it in linux, but usng the advance setting in installation did not work well for me; the only way I could work around it is to leave my SSD as my root and some swap and use my HDD as my /home so this is how its looking like atm:
Root  Partition 100GB
Swap Partition 28GB
Home Partition 1TB

the thing is I want to be able to place wine in my SSD so I can install wow and some other games that will take advantage of SSD speed.

and alone the same type of question is: is there a way to choose were you install apps and other softwares? or do they all go between root and /home/user??

Thanks in advance for your time

---

### Post by BertN45 on 2012-03-27
The partitions you have created seem right to me. The applications will always be installed in the root partition and the configuration files some in root and user specific ones in /home/user. For Wine and Windows programs you might be able to use d:, I do not know, but you could try it.

Just a remark: Your swap Partition seems large. Normally if you have more then 2 GB you need not to make it bigger then the size of your RAM. It is otherwise simply wasted space.

If you re-install the system. At the moment it starts to propose the partitioning, you have to choose manual partitioning. Here you can define the partitions. The GUI is relatively simple to use so do not worry. The root partition has as mount point "/".

---

### Post by oldfred on 2012-03-27
I only have a 60GB SSD and have two / (root) partitions on it. I also keep my /home inside my root, but it is just about only .wine with only Picasa. My /home is about 1.5GB (mostly Picasa) and my total root uses about 7GB.

I still have all my data on rotating drives in two data partitions. One is NTFS for XP on another older 160GB drive and the other where almost all my new data goes is an ext3 partition. But, I would use ext4 now.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Since my drives other than the XP are Linux only all newly formated drives are gpt partitioning as recommended by Arch.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD

---

### Post by Zettaichi on 2012-03-27
> **BertN45 said:**
> Just a remark: Your swap Partition seems large, do not make it bigger then the size of your RAM.

yeah I made it that big because I was reading that its good to have double your memory so thats what i did well about.

Thats what i did when i set up the partitions as i have it my problem was when I set the partitions before this last time I had 
"/" 30GB
"/home" 80GB
"swap" 18GB
and a random partition lets call it random
"/random" for my HDD of 1Tb
but when I tried to used my "/random" to save my videos and pics i have in dvds it said I was not authorized 

now I do not know if this is me been a novice or what but I was not able to find any information about this. So I figure I did something wrong w/ the partitions setup.

Also how would ubuntu reacts once the partition with "/home" is full?

---

### Post by oldfred on 2012-03-27
When you have added partitions for data you have to mount them and set ownership & permissions. 
You do not have d:, e: etc but can give names like video, music, pictures etc and Linux is mutiuser so you have to define who has ownership and what permissions they have to read, write or execute files in those partitions. 

You can manually mount a partition, but if a permanent drive it is better to add an entry to fstab and have it auto mount on every reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you need specific entry and instructions for editing fstab post this:
```

sudo blkid
```

---

### Post by Zettaichi on 2012-03-28
Thanks Oldfred, as soon as I get home I will see if I can work on it

---

