---
title: "Can't boot into xubuntu after reinstalling windows"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by daithi_dearg on 2010-01-05
Hello,

I've re-installed Windows and now can't boot xubuntu 9.1. I've looked at:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I did the the fdisk -l and tried mounting each of the partitions but I couldn't mount sda4 which I think is the partition that my xubuntu is located on. A clue that this is the partition is that it is the only one of type extended as I saw in gparted. It was also the only one apart from sda5 that I wasn't able to mount and sda5 I think was an old USB partition. 

Do you have any advice on anything else I could try or are you going to need the output of "fdisk -l" to get a fuller picture.

I appreciate any help you can offer me.

Thanks,
David

---

### Post by Prendi on 2010-01-05
What makes you think that the Ubuntu partition would be of type "Extended"? Extended partitions do not actually contain a single file system, but are containers holding up to four additional partitions. So it makes sense that you can't mount it. If your extended partition is sda4, then the partitions it countains would be sda5-8. 

In a simple Ubuntu installation you should only have a single partition that fdisk shows to be of type "Linux", so you'll only need to mount that one partition.

---

### Post by theDaveTheRave on 2010-01-05
Hi,

I know from reading around (and bitter experience), that windows like to be installed onto a pc before any other OS's.

This makes sense in a microsoft world (it stops the competition!)

However in your situation it can be a pain.

The solution is probably going to be to somehow re-install GRUB. The link that you have pointed to should be good. I have used the same procedure myself on an old XP terminal when I had a similar issue.

The other solution is.

Boot up to a live CD, this should enable you to determine the drive name for the partition holding your linux install.

Backup your importantant data from the linux partition (as you should be able to access it via the live CD).

Now you should be able to post the results of the following.

On the partition that had your original linux install find the file </etc/fstab> and post the contents. It will enable us to help you correctly identify your disks etc etc....

David

---

### Post by drs305 on 2010-01-05
Take a look at this:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

