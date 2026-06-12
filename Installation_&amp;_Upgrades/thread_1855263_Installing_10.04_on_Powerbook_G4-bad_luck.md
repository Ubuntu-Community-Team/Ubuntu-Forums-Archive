---
title: "Installing 10.04 on Powerbook G4-bad luck?"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by hypermeter on 2011-10-05
Hello all!

I had initially wanted to install Ubuntu side by side with my OS X, but I didn't have the installation discs for it anymore and could not resize the partition, etc. I decided to use the Ubuntu PPC live cd to wipe out OSX and install Ubuntu only. The installer ran and erased my harddrive entirely, but then could not install Ubuntu. It could not create an Ext4 partition. 

I tried configuring the partitions manually in MANY different configurations, and I keep getting the same message. In general, I have been creating the Ext4 under "/", then the Newworld boot at "home" and finally a small "swap". 

Help please!

---

### Post by tgalati4 on 2011-10-06
It's been several years since I played with Ubuntu on my old G4 powerbook, but I recall having to use the OSX disk and booting it live and using the system "disk utility" to manually create the partitions.  The mac BIOS needs certain headers on the partition that gparted or the Ubuntu installer doesn't mimic properly.  I also set it up as dual-boot.  There might be issues with not having a mac partition as the first partition, so you might need to install OSX first then shrink the partition to make room for Ubuntu.

---

### Post by lcman on 2011-10-06
> **hypermeter said:**
> Hello all!

I had initially wanted to install Ubuntu side by side with my OS X, but I didn't have the installation discs for it anymore and could not resize the partition, etc. I decided to use the Ubuntu PPC live cd to wipe out OSX and install Ubuntu only. The installer ran and erased my harddrive entirely, but then could not install Ubuntu. It could not create an Ext4 partition. 

I tried configuring the partitions manually in MANY different configurations, and I keep getting the same message. In general, I have been creating the Ext4 under "/", then the Newworld boot at "home" and finally a small "swap". 

Help please!

MAC don't ship regular scsi drives I think, I'm not really sure but it might not be possible to install linux on it unless you get a regular scsi drive.

---

### Post by hypermeter on 2011-10-07
Thanks! I was worried that I might have to reinstall OSX because I don't have the cd's anymore...Should I try a different Linux based OS?

---

