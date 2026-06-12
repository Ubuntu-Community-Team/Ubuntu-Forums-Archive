---
title: "Does not boot"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by Kristian_Brevik on 2015-01-15
Hey all, I just did a fresh install of Ubuntu 14.04, and have been unable to figure out how to make it boot. Here is a log of where I am now - what other information would be helpful to figure this out? I've tried a number of partition schemes and boot settings. 


[http://paste.ubuntu.com/9758237/](http://paste.ubuntu.com/9758237/)


Thanks!

---

### Post by yancek on 2015-01-15
I can tell you what the problem is but not how to repair it.  Look at the top of your output as it shows Grub installed to the master boot record and says it is looking for the core.img file and it is not there.  It won't boot in that mode.  You also have a FAT32 partition (sda1) which contain the Ubuntu files to boot in EFI mode.  If you use EFI, you don't put Grub in the MBR.  If you use a Legacy BIOS boot, you don't use an EFI partition.  I'm not familiar with the bootrepair but you might check to see if you have an option to select one or the other.  Else wait for someone more familiar with EFI to post.

---

