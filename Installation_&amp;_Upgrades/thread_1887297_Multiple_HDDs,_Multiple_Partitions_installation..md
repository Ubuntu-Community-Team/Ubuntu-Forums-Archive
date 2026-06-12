---
title: "Multiple HDDs, Multiple Partitions installation."
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by ObsidianWolf on 2011-11-26
I have two hard drives on my computer.
C: Which is partitioned into three sections, C:, E:, and L:.. C being where I keep my Windows partition, E being my music and movies. L being where I would like my Linux partition to go. As of right now it looks like this

disk0:
     C: - NTFS, 250GB
     L: - unformated, 50GB
     E: - NTFS, 600GB

disk1:
     Z: NTFS - 1.5TB

Drive Z: is my massive storage and backup unit. I store my video games and.. well backups here. 

My problem is every time I load up my linux installer to install 11.10, it only recognizes my Z drive, and wont even look at my other hard drive. But, when I'm just using linux from the thumb drive or CD to do the trial run, i can still access all of the information thats on all of the partitions. I'm very confused. I really want to have this going by tonight but I'm very patient. 

Anyone have any ideas as to why the installer wont see the other hard drive?

Any help would be appreciated so much.
Thanks in advanced

-O

---

### Post by Basher101 on 2011-11-26
hmmm maybe it does not get mounted when the installer is running? otherwise no idea :(

---

### Post by ObsidianWolf on 2011-11-26
> **Basher101 said:**
> hmmm maybe it does not get mounted when the installer is running? otherwise no idea :(

You know, I thought of that. Then I physically ran 11.10 from a flash drive, manually mounted all of the drives, unmounted Z: to no avail. I think Ubuntu is getting greedy and wants that 1.5TB all to itself :P

---

### Post by darkod on 2011-11-26
First of all, I hope L: is imaginary because if it's unallocated space not belonging to any partition, it wouldn't show at all in windows My Computer and wouldn't have any letter allocated to it.

You need it to be unallocated space.

Second, if your disk0 has been used in RAID before it still has meta data on it. Formatting doesn't remove this. The Ubuntu installer ignores disks with raid meta data. If this is the issue, the solution is (only do this if you are not running raid):

Boot with the ubuntu cd in live mode (Try Ubuntu option) and open terminal. To check which disk is /dev/sda and which /dev/sdb in linux notation, run:
sudo fdisk -l (small L)

After that, depending if disk0 is /dev/sda or /dev/sdb, run:

sudo dmraid -E -r /dev/sda (or replace /dev/sda with /dev/sdb)

Confirm you want to remove the meta data. That's it.

---

### Post by bluexrider on 2011-11-26
> **ObsidianWolf said:**
> I have two hard drives on my computer.
C: Which is partitioned into three sections, C:, E:, and L:.. C being where I keep my Windows partition, E being my music and movies. L being where I would like my Linux partition to go. As of right now it looks like this

disk0:
     C: - NTFS, 250GB
     L: - unformated, 50GB
     E: - NTFS, 600GB

disk1:
     Z: NTFS - 1.5TB

Drive Z: is my massive storage and backup unit. I store my video games and.. well backups here. 

My problem is every time I load up my linux installer to install 11.10, it only recognizes my Z drive, and wont even look at my other hard drive. But, when I'm just using linux from the thumb drive or CD to do the trial run, i can still access all of the information thats on all of the partitions. I'm very confused. I really want to have this going by tonight but I'm very patient. 

Anyone have any ideas as to why the installer wont see the other hard drive?

Any help would be appreciated so much.
Thanks in advanced

-O

Use your thumb drive and then format the partition "L" to ext4 

Disable disk1 "Z" drive then do your install.

---

### Post by ObsidianWolf on 2011-11-26
> **darkod said:**
> 

Boot with the ubuntu cd in live mode (Try Ubuntu option) and open terminal. To check which disk is /dev/sda and which /dev/sdb in linux notation, run:
sudo fdisk -l (small L)

After that, depending if disk0 is /dev/sda or /dev/sdb, run:

sudo dmraid -E -r /dev/sda (or replace /dev/sda with /dev/sdb)

Confirm you want to remove the meta data. That's it.

You got it man. Darko you're my hero. 
I'm on my way to having it all installed!

---

