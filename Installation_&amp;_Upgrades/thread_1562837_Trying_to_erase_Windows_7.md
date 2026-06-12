---
title: "Trying to erase Windows 7"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-08-28
Windows is really annoying. Getting rid of Linux is always so simple....delete the partition. Windows 7 is not making it easy for me. 

I have tried to delete the whole thing (all disk partitions) but Gparted couldnt delete some of the partitions....they wouldnt unmount, or a few of them just wouldnt delete for reasons unknown to me.

There are now 5 versions of Windows 7, according to bootup....but there is only 1 installed. These are previous versions of Windows and Windows 7. They were installed to an expanded partition then to an NTFS partition in the same area, but nomatter what I do, as soon as there is a windows partition back on the disk it still reads these old versions.

Whats worse, Linux wont boot unless I install it to the same partition, but that makes the other 800gb unusable for anything but storage. 

I tried using Dans nuke, or whatever, but it failed. I didnt remember the message, but it was the same problem as with Gparted.

I tried using linux by installing it to the entire disk, then putting windows back on to a newly created partition, but as soon as I put windows back on the hard disk it still remembers the 5 previous installs and I have the same boot problems with Linux aagin.


What am I doing wrong?

---

### Post by oldfred on 2010-08-28
If they are in an extended partition and your Ubuntu is in the extended since it is one partition the entire partition is mounted. 

You then cannot use the gparted in Ubuntu but must use the liveCD and make sure you click on the swap partition and swap off or it still may be mounted.

show us your partition layout:

```
sudo fdisk -lu
```

---

### Post by Nick_Jinn on 2010-08-28
I did use a live CD. It didnt fix anything. 

I eventually did manage to erase all partitions, but when I put Windows back on it still had memory of the last 5 installs of windows, and then the same problems booting Linux again. I want to be clear....it said the entire disk was blank with no partitions, but then on a FRESH install with NO PARTITIONS, it REGAINED memory of previous installs. WTF?


This was from a supposedly clean slate after deleting all partitions. I deleted everything from a live disk, but apparently it wasnt really deleted.

---

### Post by oldfred on 2010-08-29
Gparted has a two step process to changing things. One you select a partition to change/delete. Then you have to click the check to implement the changes. 

Even if you did not reformat the partitions windows should not find the installs as the partitions are deleted.

From liveCD show us:

```
sudo fdisk -lu
```

---

### Post by Nick_Jinn on 2010-08-30
It was the damndest thing. I thought maybe the changes were written to the bios or something....I thought maybe it was a quirk since the guy who initially owned this computer may have been used a hacked version of Windows that did something to the bios or something.


Anyway, when I delted the partitions, reformatted the entire disk, deleted again, then used different portions of the disk this time, swapping my /data partition with the previous windows partition, that took care of it.

I was using Gparted properly. Its a program I use a lot. I install Linux and Windows as a side job and do about 5 a week.

---

