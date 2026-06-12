---
title: "gparted mess-up at installation"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by elfuego on 2009-11-13
I'm using Asus EeePC 901 with two SSDs, 4+16GB. On 4gb SSD there is a fully-working windows XP. I was trying to set up a dual-boot with Ubuntu 9.10 by creating a "live-CD" (live-USB), partitioning the 16GB SSD (8gb ntfs, partitioned in WinXP + 8gb ext4, free space partitioned in gparted, mount "/"). After starting the installation, I got the error "cant write to sdb".

I went back to gparted, repartitioned the drive, tried again - but got the same error. I restarted the system, boot up live USB, ran gparted, deleted partitions from the 16gb SSD, ran the installation again this time using the whole drive for Ubuntu but it ended up with the same error as earlier. 

I gave up, loaded up Windows XP, entered disk management administration, but the 16gb SSD wasn't there. I tried running diskpart.exe, but it failed with error "the disk management services could not complete the operation". 

I would appreciate any help or advice on how to restore the SSD back to a working state, possibly with Ubuntu 9.10 on it ;) BTW, I don't need any old data from the 16GB SSD.

Note that I've ran Ubuntu 8.04 dual-booted on the same machine earlier so this should have worked... :(

---

### Post by elfuego on 2009-11-14
Solved with hirens boot USB (killdisk). After reinitializing disk installation of Ubuntu 9.10 went ok. :popcorn:

---

