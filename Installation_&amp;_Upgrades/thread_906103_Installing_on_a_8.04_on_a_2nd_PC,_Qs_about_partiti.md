---
title: "Installing on a 8.04 on a 2nd PC, Qs about partitioning/LVM"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by hcaleman on 2008-08-31
I've installed and tested Ubuntu on my Toshiba laptop and like it so far, now I want to go ahead and install on my desktop.  I'm going to go out and buy another SATA drive for the install and testing so I still have my current XP pro drive and data safe.

I have some questions on partitioning.  On my XP drive I have setup two partitions, one for the OS and main operating files, another for other programs/games and media.  

Would like to do a similar thing in ubuntu during the alternative cd install.  Say I buy a 400gb drive, if I want to dedicate roughly 20GB to the main OS section (enough?), Xgb to swap (do I need a dedicated swap area, recommended size with 2GB or RAM?), Ygb to programs, and Zgb to media can I do this via LVM?  the program & media partitions/volumes can be merged if that makes things simpler.  

What would be the main advantage of doing this via LVM instead of traditional partitioning (from my understanding dynamic adjustability of volumes); especially if I don't foresee ever using 400gb of space?  Also, is setting up encryption capable LVM setup or must I stick to standard partitions if I would like to try this?  Any other tips I should be aware of?

---

### Post by jmate24 on 2008-09-26
Yes 20GB will do for a / Partition, and RAM=Amount of Swap, also I'm sure that any Linux Partition can be encrypted, and LVM is somewhat similar to the Windows XP Pro's "Dynamic Disks" in that you can span 2 or more drives with a single partition, or you can setup an LVM RAID which will allow you more functionality but greater the cost :( and if your in doubt about LVM it does not hurt to keep asking around the forums.

Jmate24

---

