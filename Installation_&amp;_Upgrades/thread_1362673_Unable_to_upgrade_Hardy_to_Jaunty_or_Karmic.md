---
title: "Unable to upgrade Hardy to Jaunty or Karmic"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by trp on 2009-12-23
Hello everyone!  I have a very perplexing issue with my Dell mini 9.  The system is currently set up with 2GB ram, 16GB Supertalent SSD 80/40 (read/write), and OS 8.04 LTS supplied from Dell.  I had tried to upgrade several months ago to Jaunty, all went well except I could never get the wireless to work, so I re-installed 8.04 without issue.  In October, I tried to install 9.10 (Karmic) from DVD provided by Canonical.  Scaned the DVD for errors prior to installing, all checked out well, so went to install.  After partitioning SSD (used the entire disk-removed Hardy no dual boot) the install stopped with the message ext4 file system failed to install.  Tried several more times, with the same result ending at 5% with the same error message.  Tried to install 9.04 (Jaunty)and received the same error message, except text ext4 was replaced by ext3 file system failure.  Also tried several more times with no luck.  Frustrated, I again went back to my OEM 8.04 LTS (Hardy) and had difficulty installing it.  It would appear to download properly but upon re-booting instead of going to desktop it would give me a black screen with the text grub>.  Tried re-booting several more times and got the same results.  Re-installed Hardy again this time on re-boot got the black screen with the text MBR 1FA.  By entering "a" I got MBR 1234FA.  If I typed "2" the system would then go to desktop (entering 1, 3, or 4 had no effect).  I subsequently have determined that the MBR had been corrupted apparently from the failed install of Hardy.  I repaired the MBR in Hardy and now the system boots normally.  To make a long story short, what the heck is going on?  I have a second Dell mini 9 with the same specs and upgraded to Jaunty and now Karmic without incident.  Yet on my other mini I cannot get passed Hardy.  Call me a glutten for punishment, but earlier this week I again attempted the install of 9.04 and recieved the same install failure notice for ext3 file system at 5% (and remember this version originally installed fine but wirelesss did not work).  I have searched the forums for a fix and have not been able to resolve this.  Hardy is okay (Dell re-mixed Ubuntu)but I would like to update my distro,  am already 2 behind.  Just for additl info., I have 2 DVD`s for 9.04 and both failed to install properly but checked out on disk scan.  These were also the discs that installed succesfuly on my other mini 9.  HELP!  I am out of ideas.  Thanks to everyone in advance for your interest and help.    Happy Holidays,     Tom

---

### Post by labinnsw on 2009-12-24
Upgrades must be done sequentially, from 8.04 to 8.10 to 9.04 to 9.10. Or when Lynx is officially available you will be able to upgrade from 8.04 LTS to 10.04 LTS.

In my opinion upgrades take too long. I recommend backing up your home directory, and making a note of your user installed applications. Do a fresh install of the release you want, re-install your applications then restore your home directory.

I would also recommend formatting the entire disk for the new installation. That should replace the ext3 file system with the ext4 system. Good luck.

---

### Post by trp on 2009-12-24
> **labinnsw said:**
> Upgrades must be done sequentially, from 8.04 to 8.10 to 9.04 to 9.10. Or when Lynx is officially available you will be able to upgrade from 8.04 LTS to 10.04 LTS.

In my opinion upgrades take too long. I recommend backing up your home directory, and making a note of your user installed applications. Do a fresh install of the release you want, re-install your applications then restore your home directory.

I would also recommend formatting the entire disk for the new installation. That should replace the ext3 file system with the ext4 system. Good luck.




Any Ideas why 9.04 which is using ext3 file system also failed to install on one mini 9 and not the other?  Both had the OEM dell re-mix version of 8.04 LTS.  Or why the boot loader apperared to have gotten corrputed and grub had to be re-installed?  Also,  using gparted, the file system (ext2, ext3 ect,) can not be detected?  Any thoughts would be appreciated.  

Thanks!

---

### Post by labinnsw on 2009-12-24
> **trp said:**
> Any Ideas why 9.04 which is using ext3 file system also failed to install on one mini 9 and not the other?  Both had the OEM dell re-mix version of 8.04 LTS.  Or why the boot loader apperared to have gotten corrputed and grub had to be re-installed?  Also,  using gparted, the file system (ext2, ext3 ect,) can not be detected?  Any thoughts would be appreciated.  

Thanks!

Not  a clue. :confused:

---

