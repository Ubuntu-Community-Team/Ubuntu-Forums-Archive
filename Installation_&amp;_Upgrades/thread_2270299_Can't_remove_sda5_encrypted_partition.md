---
title: "Can't remove sda5 encrypted partition"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by chris352 on 2015-03-21
The other day I tried installing Lubuntu using the HDD  encryption option. Something went wrong in the process and the  installation failed, so I tried again, this time without encrypting. I  discovered that the sda5 partition that's created in the encryption  process was still there, and was resulting in an error message during  the boot process. 


  I've since tried erasing and reformatting the drive at least five  times (it's an SSD), but no matter what I do, that sda5 partition always  shows up and causes that same error message. 
  I've tried ATA secure erase, I've tried deleting the partition with gparted, I've tried zeroing out the drive using dd,  I've tried reformatting the drive using the disk utility and selecting  "no partitions," but every attempt has failed. I re-install the OS on  the drive and that same error message comes up, and when I look, there's  the sda5 "unknown" partition. I've even tried installing another distro (Elementary OS) and the result is the same.

Any ideas as to what's going on?

---

### Post by kerry_s on 2015-03-21
take pic of the drives in gparted so we can see how it's setup.

---

### Post by ubfan1 on 2015-03-22
Is the SDD in an external enclosure?  Have you ever successfully run TRIM on it?  Most external enclosures do not support TRIM, so really freeing up blocks can get to be a problem.

---

### Post by chris352 on 2015-03-27
No, I was being dumb. The message that came up on the splash screen had to do with the home directory encryption, not with some remanence of the hard drive encryption. When I tried reinstalling with no encryption at all, no such messages came up.

---

