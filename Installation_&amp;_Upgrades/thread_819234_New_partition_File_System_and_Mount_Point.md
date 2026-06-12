---
title: "New partition File System and Mount Point?"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by JEBB on 2008-06-05
In upgrading from 7.10 to 8.04 the Ubuntu partition of my dual boot (XP/Ubuntu) Thinkpad got screwed up.  (No sound was one problem.)  So I decided to wipe clean, reformat, and, at the same time expand, my Ubuntu partition.  I am using Gparted from the Live CD.  It seemed rather intuitive until I got to the screen that is entitled "Edit Partition" where I encountered two choices that were new to me: File System and Mount Point.   What File System should I choose for this Ubuntu partition and what Mount Point?  None of the choices are meaningful to me.  Thanks.

---

### Post by didac on 2008-06-05
To install a Linux system you need a minimum of two partitions, one formatted as ext3 or ext2 and mounted as / or root, and another partition as swap, no mounting point needed. You can also set more partitions with different filesystems like reiserfs, and different mounting points, but that will do.

---

### Post by JEBB on 2008-06-05
Thanks didac.  That was the information needed to finish the formatting and installation.  But, alas, while it boots to 8.04, I can't do anything.  There is no sound, as before, but now no wireless networks are recognized.  Back to 7.10?  Or forget it?

---

### Post by wpshooter on 2008-06-05
> **didac said:**
> To install a Linux system you need a minimum of two partitions, one formatted as ext3 or ext2 and mounted as / or root, and another partition as swap, no mounting point needed. You can also set more partitions with different filesystems like reiserfs, and different mounting points, but that will do.

I would also make sure that I had a separate **/home** partition.

---

### Post by didac on 2008-06-05
Re-post the problem and go through the forums postings on upgrades/installations

---

