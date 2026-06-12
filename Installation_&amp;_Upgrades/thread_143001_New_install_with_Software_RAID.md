---
title: "New install with Software RAID"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by kaptainlange on 2006-03-11
Hello all, thanks in advance for any help you can give me.

I am currently trying to install Breezy on a computer that will act as a server for my Mom's small business.  She has data which she needs to ensure is safe so I am trying to set up a Mirror (RAID-1) on her two 160G sata drives.

My partition scheme as as follows.

Disk 1:
Primary - 10GB mounted on /, ext3
Logical - 150GB software raid partition

Disk 2:
Logical - 5GB mounted on /tmp, ext3 -noatime
Logical - 1.5GB for swap
Logical - 3.5 mounted on /var, ext3
Logical - 150GB software raid partition

RAID Partition
150GB mounted on /home, ext3

This seems to work no problems, with the partitioner, no warnings are given.

Next step in install process is, Install Base System or something of that nature.  It gets about 70 percent done, and at the stage where it is done configuring all the packages, and enters the next stage it fails.

Alt-F3 provides me with an error though I am unsure if it is related.  It comes up at the same time as the install fails so I assume it is.

"mdadm is already the newest version
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
ubuntu-minimal: Depends: aptitude but it is not going to be installed
E: Unmet dependencies.  Try 'apt-get -f install' with no packages (or specify solution)."

I have tried with several disks this exact install process, thinking maybe my disks were bad.  I suppose that isn't the case here.  Any insight would be much appreciated.

*UPDATE*

Upon trying again this time i could see what happens right before it fails.  It is saying Creating device files and then fails.

---

