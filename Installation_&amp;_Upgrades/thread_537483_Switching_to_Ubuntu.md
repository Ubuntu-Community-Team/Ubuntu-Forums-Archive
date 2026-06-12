---
title: "Switching to Ubuntu"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by shaftesburyiv on 2007-08-29
I'm leaving Xandros after many problems with sound for Ubuntu.  I currently have a dual boot of XP and Ubuntu ... I don't want to get rid of XP just yet, though I rarely use it, esp. b/c I have the Thinkvantage software, which is probably difficult to replace.  Unfortunately, when I do the Ubuntu installer, it only gives me two options, Manual Install and to Install on the whole 80Gb harddrive.  I want to replace the 15 gig Xandros partition, and the 1.45 gig Xandros swap partition.  Should I delete these in Windows first, or is there another way to do it in the Ubuntu Installer (the Manual method?).  Thanks

---

### Post by merlinus on 2007-08-29
The manual option will allow you to select the partitions for ubuntu.  You will also need to select the mountpoints, / and /swap.

-merlin

---

### Post by shaftesburyiv on 2007-08-29
thanks for the quick reply ... I think I understand that I need to select the Ubuntu main partition and the swap, but what do you mean by mount points?

---

### Post by merlinus on 2007-08-29
When you select the partition, you may need to right-click on it and select the mountpoint from a dropdown list, IIRC.

-merlin

---

### Post by shaftesburyiv on 2007-08-29
ok, now i understand what you mean.  my only issue is that it says: 

Edit a partition:

Use as: reiserfs

Mount Point: /

I understand the mount point, but what should I select for Use as?

thanks!

---

### Post by merlinus on 2007-08-29
I use ext3.

-merlin

---

