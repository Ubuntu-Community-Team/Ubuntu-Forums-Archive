---
title: "NTFS Resize Partition Lesson"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by Greslore on 2007-08-08
Thought I would share my experience with everyone here in hopes to save them some time. I was trying to dual boot a WinXP box with Kubuntu 7.04.  But the Kubuntu installer kept throwing errors back at me when it tried to resize the NTFS partition on my drive.  (160gb SATA).  The errors were to the effect of "Unable to read NTFS partition".  

I downloaded the latest gparted ISO, and still it would not resize the NTFS partition.  Now after searching a few forums, I have read that people should defrag and disable Windows System Restore.  For some reason, my mind completely dismissed those notions.  Well...  After defragging three times and disabling Windows System Restore, I was indeed able to resize NTFS.

So, if anyone else is having resizing issues - I can say with experience now, Defrag and Disable Windows System Restore!  :)

---

### Post by guguma on 2007-08-08
Yeah you are right indeed. System Restore is just sick useless nonsense.

---

