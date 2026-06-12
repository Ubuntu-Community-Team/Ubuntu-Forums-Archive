---
title: "Missing drive when Assigning mount points during install"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Pseudo Idol on 2007-03-18
First off, I have successfully installed Ubuntu on quite a few machines but this is the first time I have come across this. I recently reorganized all my files on my Desktop PC so I could give Ubuntu its own hard drive. It was on a small partition on my windows drive but since I was using it more and more, it needed more space.

The install was going fine, I partitioned the drive I wanted for Ubuntu (hdh), and moved on to the assigning mount points screen.  In the drop down list of partitions, none of the partitions on hdh appear. I only see my windows drive (hdg), my external hardrive (sda), and my large data drive (sdb).

/dev/hdg1 - Windows Drive - IDE
/dev/hdh(1,2, 3) - Missing from list, same make and model as /dev/hdg IDE
/dev/sda1 - External USB Drive
/dev/sdb1 - Internal SATA drive

Any ideas why the drive is not showing up in the list.  The installer saw the drive and was able to partition it in the previous step.

Thanks for any help...

[edit]
I downloaded the alternate install cd to try a text based installation. This failed to recognize any of my hard disks except for my external USB disk.

[edit again]
I think that both my IDE drives may be failing, neither of them are be recognized by the motherboard anymore, swaped IDE cables but to no avail.  They are fairly old (7 years) and not that fast or large.  I am contemplating the purchase of 4 SATA hard disks and setting up a RAID 0+1 setup.  It is a good thing I backed up all my data onto my external drive last night.

---

