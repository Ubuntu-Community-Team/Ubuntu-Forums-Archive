---
title: "Can Partition in 9.04 but not in 9.10"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by sbrandon on 2009-11-18
I have a pc that I have been loading ubuntu on as the upgrades have come out. I was able to do a fresh install of 9.04 and then upgrade to 9.10, but when I tried to do a fresh install of 9.10 to use GRUB2, etc, I ran into problems at the Partition portion of the install. Instead of giving me the colored bars of the existing partitions in the Prepare Partitions section I was presented with a blank Prepare Partitions (PP) with all of the options at the bottom greyed out. Could not go forward and using GParted on the Live CD I deleted and then repartioned the harddrive. I rebooted and then tried to install again and got the same blank PP section. Rebooted with the 9.04 iso disk and was able to do the install using ext4 and I am recreating my system now. I am perplexed as to why 9.04 partitioning works and 9.10 does not. Any thoughts,etc would be welcome.

---

### Post by Ginsu543 on 2009-11-19
You may be having a problem similar to what I had when I was first trying to install 9.10. I have two SATA disks that have been used in a RAID array before and the partitioner wouldn't recognize them. So like you, I had a blank Prepare Partitions page. Give this a try:

1) Boot into a live session using the LiveCD (without installing)
2) Open Terminal
3) Type "sudo apt-get remove dmraid" and hit Enter (command without quotes)
4) Start the installer by double-clicking on its icon

If all goes well, the installer should now recognize your hard drive(s). You can then proceed as normal.

---

### Post by dhavalbbhatt on 2009-11-19
you can also try and use the alternate installer CD to install Karmic. There seems to be an issue with the Desktop installation CD, especially with the partition manager. The alternate installation CD is a CLI based installer, but don't worry, it does the job fine.

---

### Post by sbrandon on 2009-11-19
Thanks for the feedback. I'm going to try the Ginsu method first and then report back as my disks are SATA as well.

---

### Post by sbrandon on 2009-11-19
Ginsu - that worked perfectly. Thanks!

---

### Post by Ginsu543 on 2009-11-19
Excellent! BTW, if you install GParted, you may have to uninstall dmraid again to be able to boot. It seems that GParted reinstalls dmraid as part of its package if it is not already installed. In any case, I'm glad it worked out for you.

---

### Post by sbrandon on 2009-11-20
Did not install GParted just used the one on Live CD prior to doing your RAID fix.  Noticed in another of your posts your comments on Grub2. When I installed I opted for the Installer version which was 1.97 (??). Is that in fact version 2? Can't tell much difference just wondering.

---

### Post by darkod on 2009-11-20
Yes, it is. Strangely enough, grub2 is 1.97 and the previous grub (also called grub legacy now) is 0.97. :) And you thought this would be easy right? :)

---

### Post by sbrandon on 2009-11-20
Wonder if they round up their accounting as well.  Thanks.

---

### Post by Ginsu543 on 2009-11-23
I believe the version numbers are lower because they are in fact beta versions. I suppose that when Grub 2 finally makes it past the beta phase, it will be granted 2.0 status.

---

