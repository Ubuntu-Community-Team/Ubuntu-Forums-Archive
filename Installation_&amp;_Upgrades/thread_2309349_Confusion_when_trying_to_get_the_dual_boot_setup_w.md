---
title: "Confusion when trying to get the dual boot setup working and windows not recognising"
date: 2016-01-09
forum: Installation &amp; Upgrades
---

### Post by lewis12 on 2016-01-09
Hi everyone, I have finally decided to take the plunge into Linux after using Apple Mac and Windows machines for all my life.
I have decided on Lubuntu on my Dell Inspiron 1545 laptop, to dual boot with Windows Vista (yes I know it's Vista the bloated ram hog, but I am hesitant to install a Windows OS from a downloaded ISO that's pirated since I don't trust it won't have viruses, and I sure ain't paying to upgrade Windows).

Basically when I run the install disc I originally had 3 partitions (I did this from the start with the Hard Drive when I replaced it ages ago after the original hard disk failed, since I wanted to make sure I didn't have to resize partitions, and I have had experience with dual booting Mac OS X and Windows and also Mac OS 9 and Mac OS X before).

The issue is that when I tried to first format the partition (the 3rd one) from NTFS into ext4, I stopped there as it then asked if I want to make changes that can't be undone, and it wanted to make extra partitions that would be numbered 5 and 6, and this confused me a bit so I just stopped and rebooted the laptop.
Windows then thought something was wrong and tried to repair that partition.

I then decided to go into Windows partition manager and delete the 3rd partition from within Windows, so I assume this means Windows will not bother that partition when I create it within the Lubuntu installer, am I right in assuming that?

Also, can people explain, since I always progressed through the menus by choosing to install it alongside Windows and I never chose the erase disk option, then when the installer says it will make changes that can't be undone, do I have any cause for concern?
I don't want it to wipe Windows and my data off the drive.
I have backed up, but I don't want to make a silly move that would erase my data just by clicking something I don't understand by mistake.
Basically why is it trying to make a 5th and 6th partition, and also why not partition 4? (since I had 3 partitions it makes sense the next one would be partition 4.

Sorry if this post makes me sound a bit silly, but I just want to be safe.
I intend to use Linux for 95% of my tasks, and to run wine to avoid using Windows.
Clearly with me running Vista, I am sure to see a massive performance improvement with going to Lubuntu, haha

---

### Post by ubfan1 on 2016-01-09
MSDOS partitioning canonly have four primary partitions, so for more, you make the fourth one an extended partition, and then add logical partitions inside it.  Fifth probably is root, sixth probably swap.

---

