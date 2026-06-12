---
title: "Partition Help!"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by pdnd24 on 2007-06-05
I am having some trouble partitioning. I am a newbie. I tried the guided partitioning and it said it could not be partitioned. I am using the text-based installer.

When I hit manual I am stuck with this:

Thsi is an overview of your currently...

Guided Partitioning
Help on Partitioning

SCSI3 (0,0,0) (sda) - 80.0 GB ATA FUJITSU MHV2080B
          #2 Primary    7.3 GB     K   FAT32             /media/sda2
           #1 Primary     72.7 GB  B  K  ntfs             /media/sda1
                     pri/log      8.2 MB            FREE SPACE

I am attempting to set it up so I can duel-boot Nubuntu and WinXP. Thanks! :KS

---

### Post by dabl on 2007-06-05
Here's great guidance on partitioning for dual boot.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mikewhatever on 2007-06-05
Can you elaborate on what exactly you are trying to achieve. Partitioning is a very broad term which can mean creating, resizing, deleting partitions etc. It is nice to know that you have 2 hdds, but absolutely irrelevant to the question.

---

### Post by vanadium on 2007-06-05
Is there a reason why you use the text based installer? As anewbe, you  better use the live disk for installing and follow the defaults.

---

### Post by Pumalite on 2007-06-05
> **vanadium said:**
> Is there a reason why you use the text based installer? As anewbe, you  better use the live disk for installing and follow the defaults.

If you are going to install Ubuntu in the same drive as XP and at this point you have i big partition, then 1st defrag XP several times and delete al temp file and get rid of anything you don't need or that you can backup tp CD's, DVD's Or external hard drive. THEN use Gparted to make a new partition and format that ext3. Then follow up with the installation.I would also recommend the Live CD for a newbie.

---

