---
title: "Dual boot partitioning question qtparted"
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by rsperberg on 2006-05-06
I have a new lowest-end Dell computer. I thought that before doing anything else, I would put Ubuntu on it as well as Windows.

Following instructions I found at [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/) I booted from the Linux System Rescue CD and launched qtparted.

From Dell there were unexpected three partitions, one of less than 100 mb, 70+ GB, and one of 7 GB, of which roughly half were occupied. Within Windows I don't see this partition, and have no idea what's on it.

I resized the big partition down to 50 GB, and found I couldn't do anything till I moved the third partition directly after it.

Then I could make 1 additional partition. No matter what I tried or what sizes I made it, or where I put it, I could only make 1 partition. Following the recommendation, I was going to make a 15 GB Linux partition, a 1 GB linux swap partition, and a 5 GB FAT 32 extended partition to share between OSes.

Does anyone have any idea why I couldn't do this? Eventually I just made one 21 GB ext3 partition for linux. Will no linux swap partition will it impact things much?

Thank you,

Roger Sperberg

---

### Post by Sef on 2006-05-06
> Then I could make 1 additional partition. No matter what I tried or what sizes I made it, or where I put it, I could only make 1 partition. 

You can only make 4 primary partitions.  What you need to do is make the others logical partitions.   Usually I will make 3 primary partitions and the others logical.


> Following the recommendation, I was going to make a 15 GB Linux partition, a 1 GB linux swap partition, and a 5 GB FAT 32 extended partition to share between OSes.

Go back and make the logical partitions and you should be able to set up the disk how you want to.

> Will no linux swap partition will it impact things much?

Unless you have at least a 1 GB ram, you need swap.  Otherwise your system might end up going real slow or freezing up if the ram gets all used up.

---

### Post by matelot on 2006-05-07
The two other partitions in XP are hidden and are concerned with the OS and recovery information, I believe. That means you have three primary partitions already, and only room for one more. I didn't need to touch the other two.

I've just divvied up my 160Gb disk with *gparted* - seems superior working in isolation to a distro. Anyway, that's what I found.

Google for Dirms-S and Buzzsaw-S (same website). These are superior defraggers to Windows Defrag, and install and run them. May take a while. Then reboot from the *gparted* LiveCD and shrink your NTFS partition. If your drive was properly defragged, it should only take a few seconds. I shrunk 140Gb down to 50Gb in less than 30 seconds. In the space that's left create an extended partition. In the extended partition you can now create the logical partitions (drives) you want for Linux.

It worked for me. Hope that helps. :D

---

