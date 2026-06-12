---
title: "Install Dual Boot Feisty Fawn-Vista with Raid 1"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by ManoloM on 2007-05-21
I've been trying to install a dual boot system with Vista and Ubuntu 7.04 and its been a nightmare!

Here are my specs:
Dell Precision Wkstation 490 with two Quad Core Intel Xeon processors, 4MB RAM and Windows Vista 64 bit installed. Two 160GB SATA 10K hard drives set up as a raid 1 array with a SAS 5iR hardware controller card. As far as I know, this is a true hardware raid 1 array, not a "fake" one.

I need to install a dual boot Vista-Ubuntu system that preserves the raid 1 array. That is Vista with, say 80 GB, and Ubuntu with the remaining 80GB. But I need to preserve the raid 1. How do I do it?

This is what I did so far. I got both an alternate and a live CD of Ubuntu Feisty Fawn AMD64 bit, as well as a Knoppix live cd (just in case). Inside of vista I created a 24GB free space with the windows partitioner. I first tried to use the Ubuntu Live CD but it wouldn't recognize the raid array. I then tried to use the alternate CD but you can only install a "software" raid with it.

I ended up doing the following: I degraded the raid array and installed Ubuntu in the free 24GB partition of only one of the two HDs (Swap 4GB, root and home directories 10 GB each), did not touch the free space of the other HD. I think this worked ok except for a message that says: "File system doesn't have expected sizes for windows to like it. cluster size is 2k (1k expected); number of clusters is 28034 (55950 expected); size of FATS is 110 sectors (219 expected)" . I ignored the message and finished the installation. After exiting, I checked that the dual boot was working properly, and it was. I finally rebuilt the raid array so that both HDs are now synchronized (this is done inside of Vista).

At first, I thought this worked. Ubuntu and Vista were both booting up properly and all the files and programs looked ok. Ubuntu was only seeing one HD, but the \media directory listed both HDs with identical partitions and files.  Then I started to mess around with Ubuntu, installing and changing stuff and I realized that something was not right. When I would restart and log on to ubuntu again, a different login window would appear, with a different setup than the one I'd just closed. I used the Knoppix live CD to investigate and used "sudo fdisk -l" command to check the directories. The two HDs were listed with the correct partitions, but also a lot of other garbage with error messages and "tables do not correspond to partitions" warning messages.

What can I do?

---

