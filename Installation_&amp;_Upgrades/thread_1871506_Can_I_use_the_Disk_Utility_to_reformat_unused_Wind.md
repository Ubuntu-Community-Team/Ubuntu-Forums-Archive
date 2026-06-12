---
title: "Can I use the Disk Utility to reformat unused Windows partition?"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by JoeDesertrat on 2011-10-29
I apologize if I posted this in the wrong forum. 
My work PC was initially set up as a dual boot with Ubuntu and Windows XP. I have not used Windows once in four years and I would like to claim the unused partitions for my use with Ubuntu (actually, the Xubuntu desktop with Ubuntu - the hardware is too old for the Ubuntu 11.04 default install). It is an 80 MB hard drive and over 60% is unused as it was partitioned for XP and the restore partition for XP. I'm having drive space issues and this would be a first step in resolving them.
It appears to me that I could simply reformat those partitions using the Disk Utility. Is this true? Has anyone tried this? Would I be better off just trying a complete reinstall (that could cause issues with setting up various network connections and the Citrix server connections, etc.).
I was the beta tester for Linux at my company but the IT guy behind the drive to go open source left and I was pretty much left to provide my own support if I don't want to revert to Windows. And I really don't!

---

### Post by wojox on 2011-10-29
You would need to boot a Lice-CD or USB and use G-Parted to accomplish this.

---

### Post by Bao2 on 2011-10-29
Yes, Disk Utility is what I use. Practice before with an USB, try to delete the partition on the USB, then create one again and choose if you want it to be NTFS or FAT32 or Ext3 or whatever. When you understand then format the unused windows partition (instead formatting I would delete the partition and then create a new one. In the same window you have a button to unmount the partition first, then delete and create and then mount again.

---

### Post by JoeDesertrat on 2011-11-01
Thank you. I will give this a shot when I get a bit caught up here and post the results.

---

