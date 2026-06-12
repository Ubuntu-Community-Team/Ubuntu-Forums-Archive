---
title: "No root file system found"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by vikramreddyk on 2005-02-23
Hello everyone,
I have been trying to install Ubuntu on to my Toshiba Satellite with Win XP. I have a 60 GB disk and want to make it dual bootable.
Now I have 3 partitions 
11 GB primary NTFS (C drive)
35 GB (D drive) for all random data
14 GB E drive which is empty. 
I want to install Ubuntu into the last partition which is empty.
I put the bootable Ubuntu and kept following instructions till i ran into the manage disks partitions. 
I said manually handle partitions. It listed all 3 partitions I chose the third and said format and next carry the changes.
After that it showed me the error "[COLOR=DarkRed]No root file system found[/COLOR]" :roll:  and kept throwing me back to the same manually set partitions GUI. I have no idea how to tell Ubuntu that I want it to use the 14 GB partition to store its root files and all other files.

Please Help me get past the "[COLOR=DarkRed]No root file system[/COLOR]" error message.
Regards
Vikram

---

### Post by aNTwNHs on 2006-10-27
I have the same problem with Ubuntu 6.10 (Edgy Eft). Any suggestions?

---

### Post by majabl on 2006-10-27
I'm currently trying to deal with this too, though at the moment I can't even get my computer to get that far through the CD boot process!  Anyway, there's another thread going where someone has given a solution that worked for him - [http://www.ubuntuforums.org/showthread.php?t=285890](http://www.ubuntuforums.org/showthread.php?t=285890)

---

### Post by galileon on 2006-10-27
ummm...theres somewhere it asks you about which partitions to mount where, in a list.... you should make sure the partition3 where you want to install linux is marked '/' instead of being something else....

an easier option is to delete the partition E: complete;y, then run install again and tell it to use the largest available free space

---

### Post by rwahner on 2006-10-27
Hello ubuntu people. :-) 

I just want to confirm the problem in this thread. I'm trying to install
ubuntu 6.10 desktop on a fujitsu-siemens notebook. In step 5 of 6 
("Prepare mount points") I specify the following (Partition, Mountpoint, 
format or don't format):

  /dev/hda1,     /winxp,   don't format
  /dev/hda2,     /,        format
  /dev/hda3,      swap,    format

The partitions have, from top to bottom, 20GB, 50GB and 2GB.
Anyway the installer complains that there is "No root file system".
Don't understand why the installer doesn't accept my partitioning.

Friendly,

Ralf

---

### Post by imcsk8 on 2006-10-27
I have the exact same problem on ppc, on other thread someone commented that we should use the alternate CD instead.

Does someone knows how to boot the live cd in text mode??

thanks

> **vikramreddyk said:**
> Hello everyone,
I have been trying to install Ubuntu on to my Toshiba Satellite with Win XP. I have a 60 GB disk and want to make it dual bootable.
Now I have 3 partitions 
11 GB primary NTFS (C drive)
35 GB (D drive) for all random data
14 GB E drive which is empty. 
I want to install Ubuntu into the last partition which is empty.
I put the bootable Ubuntu and kept following instructions till i ran into the manage disks partitions. 
I said manually handle partitions. It listed all 3 partitions I chose the third and said format and next carry the changes.
After that it showed me the error "[COLOR=DarkRed]No root file system found[/COLOR]" :roll:  and kept throwing me back to the same manually set partitions GUI. I have no idea how to tell Ubuntu that I want it to use the 14 GB partition to store its root files and all other files.

Please Help me get past the "[COLOR=DarkRed]No root file system[/COLOR]" error message.
Regards
Vikram

---

### Post by aNTwNHs on 2006-10-29
I finally downloaded the dvd version which has extra installation options and  get on with text mode installation. I'm not sure if live cd has this optio hidden somewhere:P

---

### Post by galileon on 2006-10-29
the alternate cd has text mode install  - btw i use only this, coz its really faster to get to the actual install process, as opposed to waiting for ages for a whole GUI to load

---

### Post by cumanji on 2006-11-14
Hello,

I deleted the partition that i want to install, then i restart the install and select "use continous free space".
Then it worked me. 
Thanks to Galileon for this tip.

Regards

---

### Post by scrooge_74 on 2006-11-14
> **cumanji said:**
> Hello,

I deleted the partition that i want to install, then i restart the install and select "use continous free space".
Then it worked me. 
Thanks to Galileon for this tip.

Regards

A few weeks ago made a clean install of 6.06 on a 3 year old Toshiba no problems after deleting XP first

---

### Post by aNTwNHs on 2007-02-28
A solution has been posted [here]("http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29") and [here]("http://antonis.wordpress.com/2007/02/23/kubuntu-installation-no-root-filesystem/").

---

### Post by proshanto on 2008-04-29
I had the same problem for a few days.

I tried G-parted live CD, Xubunto 7.10, Ubuntu 8.04 LTS, and ended up with same "no root file system defined message. Finally, I noticed that you need to **format** the root area set out for Linux (staring anywhere in the disk) in file system type 83: either ext2 or ext3. I repeat, don't forget to **format**. Swap can be even fat16/fat32, does not matter; and that will be formated, too.

See if this works.

---

### Post by proshanto on 2008-04-29
I had the same problem for a few days. Finally installed Ubuntu 8.04 LTS on my desktop.

I tried G-parted, Xubunto 7.10, Ubuntu 8.04 LTS, - all live CDs - and ended up with same "no root file system defined message. Finally, I noticed that you need to **format** the root area set out for Linux (staring anywhere in the disk) in file system type 83: either ext2 or ext3. I repeat, don't forget to **format**. Swap can be even fat16/fat32, does not matter; and that will be formated, too.

See if this works. I had a lot of helpful advice from Prof Norm Matloff of UC-Davis, who, however thinks that something else did the trick. Anybody interested to find out: I will be more than glad to send the fdisk typescipts - both pre- and post-installation.

I am glad to be free, finally.

---

