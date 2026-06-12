---
title: "Installing with Vista"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by UrKo2376 on 2010-07-28
How can i install ubuntu ona machine which has already got vista on it.  When i put the cd in and boot from it it doesnt give me the option to partition the drive to install.  Want to dual boot it with ubuntu.  Have also tried to create a partition on the drive and install it there but i get the same issues.

---

### Post by zvacet on 2010-07-28
Of course,back up all your valuable data first.Check your ubuntu Cd for errors (before that check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of your Ubuntu iso) and if everything is fine with Gparted shrink Vista partition and on unallocated space make new partition formated as ext4.When you put Ubuntu Cd in the drive on partition stage it should recognize ext4 partition.Install ubuntu on it.

---

### Post by oldfred on 2010-07-28
It is a bit safer to use the Vista partitioning tools to shrink the Vista partition. Also gparted & the Ubuntu installer will not "see" NTFS partition that need chkdsk running. From windows run chkdsk. My XP install worked just find, but then gparted would not see it. I ran chkdsk and then gparted could see it.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

