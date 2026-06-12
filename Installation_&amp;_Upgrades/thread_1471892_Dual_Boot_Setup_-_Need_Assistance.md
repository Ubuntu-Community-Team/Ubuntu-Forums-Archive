---
title: "Dual Boot Setup - Need Assistance"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by italianoman421 on 2010-05-03
I have a dell Computer that has a Windows XP Partition and a recovery partition. I want to just dual boot Ubuntu and and my XP, thats it. But the setup for a dual boot like that is complicated for me. I have to use the advanced create partition option and I cannot figure out how to do it. Would someone please provide me the steps I need to dual boot my machine?

Much Appreciated

---

### Post by oldfred on 2010-05-04
Has Dell also used additional hidden partitions? You can have only 4 primary partition, but one primary can become an extended and contain any number of logical partitions. Only windows boot partition has to be a primary.

From liveCD post this:

```
sudo fdisk -lu
```

You need to leave at least 20% free space for windows. If you are going to use both you may want to make a NTFS partition for data to share between windows and linux. Linux can read the windows system partition, but windows cannot read the linux partition.
You should have about 10-20GB for / (root), swap equal to RAM memory and the rest /home.

All this depends on how much free space you have.

---

### Post by italianoman421 on 2010-05-04
I have 88gb, and there are hidden partitions, I just can't figure out how to remove the hidden ones, and leave just the Windows, and Ubuntu. I also don't know what I need to make the partitions called. The NTSF, and other acronymns through me off. I need a step by step for this and the tutorial I found wasn't specific enough.

---

### Post by kansasnoob on 2010-05-04
> **oldfred said:**
> Has Dell also used additional hidden partitions? You can have only 4 primary partition, but one primary can become an extended and contain any number of logical partitions. Only windows boot partition has to be a primary.

From liveCD post this:

```
sudo fdisk -lu
```

You need to leave at least 20% free space for windows. If you are going to use both you may want to make a NTFS partition for data to share between windows and linux. Linux can read the windows system partition, but windows cannot read the linux partition.
You should have about 10-20GB for / (root), swap equal to RAM memory and the rest /home.

All this depends on how much free space you have.

+1! We need the output of "fdisk -lu" to know what we're dealing with :D

If you're using a Lucid (10.04) Live CD press any key as soon as the initial screen shows up with two small "logos" and then you should be able to select language, then select 'Check CD for defects'. Next, if the CD passes, repeat as before, only then, choose to Try Ubuntu without changes, go to Applications > Accessories > Terminal and run that command:

```
sudo fdisk -lu
```

Then copy-n-paste the results here :)

---

### Post by oldfred on 2010-05-04
If just starting out see these:

Beginners guide:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

