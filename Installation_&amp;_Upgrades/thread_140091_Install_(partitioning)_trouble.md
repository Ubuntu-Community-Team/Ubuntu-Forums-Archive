---
title: "Install (partitioning) trouble"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by infiniteLoop on 2006-03-05
Hi!

I'm trying to install ubuntu on my computer (tried with 5.104, 5.10 and 6.04). I have Abit AN7 with SATA (Sil3112) controller and WD 120GB drive. On the drive I have 2 ntfs partitions and some free space (I'd like to install ubuntu on that free space).
So when it comes to partitions my drive detects OK but it looks as it is a brand new drive (no partitions are listed). When I try to partition a disk installer says that a new partition table will be created and all data on disk will be lost.
So I booted the ubuntu live CD. I ran sudo: fdisk -l and it listed both ntfs partitions and free space I was able to mount the ntfs partitions and read from them (So I guess the partitions can be detected - there must be a problem with the installer).
I tried runing Mandriva installer and it detected my drive and partitions OK and I was able to partition the free space. After that I ran the ubuntu installer again but still there were no partitions shown. 
I booted windows (yes that's why I have two ntfs partitions) and disk manager showed me two ntfs partitions and two "unknown" (ext) partitions.

So does anyone have any advice on how to install ubuntu on either free space or mandriva prepared partitions? Well I guess I could just install mandriva but I really like how ubuntu (debian) handles the packages.

P.S.: I tried installing debian but it failed on "loading scsi modules" or something like that (I guess it's a SATA problem).

---

### Post by oskvaz on 2006-03-05
I have the same trouble on my notebook, an IBM thinkpad T40. I can install mandriva without problems, but if I try to install ubuntu, the installer die when begin partitioning.

Please, help us!

Thanks:confused:

---

