---
title: "Partition resizing problems in install"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by Ragnar on 2005-07-22
I have recently installed Ubuntu, my first Linux installation.  I have installed it on an HP Compaq 2145 laptop, which had the entire disk formatted as one 30G primary NTFS partition, as per Compaq's usual practice.  

I need to keep my XP data, so I needed to resize the partition.   I used the manual repartitioning option in the install and reduced the XP partition to the minimum that was reported to be allowable, 11.2 G.  I then set up a Fat partition and several Ubuntu partitions.

I then successfully installed Ubuntu.  So at first I was happy.  However, I have a few questions.  I only have about 5G in the XP partition, as reported by XP.  Why then will the installer not allow me to reduce the partition smaller than 11.2G?  On a 30G drive, 6G is a lot to waste.  I really want to reduce the XP primary partition down as small as possible so that I can easily clone it for backup. I have tried several times but 11.2 is my limit, even when the actual amount of data in the partition is varied significantly.  XP defrag analysis display right after resizing the partition showed that the data had apparently been successfully moved up to the front of the drive, yet the installer will not let me resize the partition to take advantage of it.  

Anybody got any ideas?  It may be a coincidence, but 11.2G is about the maximum amount that I have ever had in the partition.  Is the installer unable to make ntfs let go of any segments that have ever actually been used?  Surely not!

On another, related point, I believe that one of Ubuntu's aims is to encourage as many non-expert people as possible to make the switch to Linux.  This helps the Linux experts too if the market expands to the point where drivers are readily available for instance.  Safety and ease of installation is critical here.  The installer is very good in its basics but could be made far better with a bit more hand-holding.  I would have been able to complete the installation far more easily and confidently if the main Ubuntu site, or indeed the installation CD, had had a good description of the basics of the partitioning process.  Judging by the amount of confusion, evidenced in another thread here, I am not the only person under the misapprehension that you should defrag the ntfs drive and get all the data to the front of the drive before beginning the installation.  There was a lot of talk about using complicated, expensive things like Partition Magic that I understand is inferior to and more risky than Ubuntu's installer.  (I cannot find the thread now, hopefuly it's been taken off as it's full of scary, bad advice that would be very offputting to the newbie.)

Prior to installation I wasted time by trying 3 different defrag utilties, trying to get all data to the front of the partition.  None worked, the best was the MS WINXP built-in defragger, which left data at the 22-24G point.  I therefore didn't have much hope that the installation of Ubuntu would be very successful in getting a decent sized Home directory and nearly gave up on the idea.  I was very pleased to find that the resize worked as well as it did, even though I am now griping that it should have gone better.  

How do you go about providing feedback about these sorts of minor non-technical annoyances and suggestions to the Ubuntu developers?

---

