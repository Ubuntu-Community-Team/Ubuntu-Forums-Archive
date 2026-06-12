---
title: "Input/output error during read on /dev/sda"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by twola on 2010-07-18
Brand new hard drive and system and trying to install Ubuntu 10.04. Windows XP & Vista installed just fine. However Ubuntu coming up with the above mentioned error. When i try to install it i keep having problems. I dont know if its  because i dont have a system on it already or what. So anyways when i  try to install it it stops at 15% and an error thing pops up saying  "input/output error during read on /dev/sda" with the options of Retry  which does nothing Ignore which makes a new load thing that says  "creating ext3 file system for / in partition #1 of SCSI1 (0,0,..." and  it stops at 5% and says "failed to create a file system" and underneath  it says "the ext3 file system creation in partition #1of SCSI1 (0,0,0)  (sda) failed" and then sends me back to step 4 which is the partition  thing.

---

### Post by davidmohammed on 2010-07-18
usually these input/output errors is due to either a bad download of the install iso or that it has been burned at too high a speed.

Try another burn but at the lowest speed available.

---

### Post by twola on 2010-07-18
I will try it however the 5% and the 15% is something that is duplicated everytime. And I have seen some other users have identical (to the percentage) errors.

---

### Post by twola on 2010-07-18
Re downloaded the ISO. Burnt it at lowest speed and still the same. This issue is quite wide spread. In my case I have a brand new hard drive which installs all other O/S's without a problem.

---

### Post by davidmohammed on 2010-07-19
what's your hardware specs (run 'lspci' in a terminal)?  e.g. if using a RAID - what RAID, RAID controller.  What sort of discs are you using?  IDE, SATA, SCSI (what variant?)

Why are you using ext3 instead of ext4?

How have you partitioned the discs - do you have multiple disks - what O/S is on what partition/disk?

sorry for all the questions - but those that could help will need more information first to see what your issue and possible fix is.

---

