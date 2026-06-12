---
title: "Problem trying to install XP on partition"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Captain Carrot on 2010-06-07
This looks like I've accidentally come to the wrong forum...

Anyway, I've got two 20 mb partitions that I formatted and tried to put xp on, (which of course overwrites my Grub, but I figured that out), but I can't get past the first reboot. After it copies all of the files to the partition, it tells me "disk error, press any key" and won't go any farther. Can anyone tell me why this is happening? I've tried, ntfs, fat32, nothing seems to be working.

---

### Post by Captain Carrot on 2010-06-07
Okay, weird. I think the installer might be putting boot.ini, NTDETECT.COM and ntldr in the wrong partition. Would that make sense? They have spontaneously appeared in my larger media partition twice now, and they reference XP. Halp!

---

### Post by confused57 on 2010-06-07
You might try booting the Ubuntu live cd, open gparted, then see where the boot flag is(probably on your larger data partition, which might be why your XP boot files are being installed there).  If that is the case, you could try right click on the partition where you'll be installing XP & set the partition as active.  This "should" set the boot flag to this partition.  Then try installing XP.  

Before reinstalling XP, you might want to use gparted to set the boot flag to the XP partition, then boot up with the XP cd, press "r", then run "fixboot" and "fixmbr".  This may repair the boot files.

---

### Post by wilee-nilee on 2010-06-07
> **Captain Carrot said:**
> This looks like I've accidentally come to the wrong forum...

Anyway, I've got two 20 mb partitions that I formatted and tried to put xp on, (which of course overwrites my Grub, but I figured that out), but I can't get past the first reboot. After it copies all of the files to the partition, it tells me "disk error, press any key" and won't go any farther. Can anyone tell me why this is happening? I've tried, ntfs, fat32, nothing seems to be working.

I'm not sure how you have built the partitions, but I haven't gotten XP to install on a ntfs created by gparted. XP can be installed in a blank space, with a custom install and be told the size of the partition to be built.

---

