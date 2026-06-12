---
title: "Files reserved at the end of the disk"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by DizzyTech on 2007-12-04
I just bought a brand new HP laptop with Vista Home Premium and want to dual boot with Ubuntu.  I would just use Wubi, but I a) want the 'full' dual-boot experience, and b) my laptop only will work in Gutsy.  I want to use Vista's Shrink Partition function to create myself space for an Ubuntu partition (so I don't risk anything), however it won't let me shrink past 8 GB on my 250 GB HDD.  It appears that there are a whole ******** of reserved files towards the end of the disk, although I can't guess what.

This layout appears more or less the same in Safe Mode.  I have disabled my both my swapfile and hibernation, and deleted both files from the hard disk permanently.  Still, the files stay.  I have even powered through a Vista Defragmentation; still nothing.

What do I do from here?  I'm ready to go with my Ubuntu DVD, but I don't want to risk Vista.

---

### Post by logos34 on 2007-12-05
> **DizzyTech said:**
>  I have disabled my both my swapfile and hibernation, and deleted both files from the hard disk permanently.  Still, the files stay.  I have even powered through a Vista Defragmentation; still nothing.

hmm...you did all the recommended steps...maybe those are system restore files (or vista equivalent)? If so you could try turning it down to absolute minimum.  And/or try defrag a couple more times.

---

### Post by DizzyTech on 2007-12-05
I think I have a handle on it.  I also disabled Recycle Bin, and intensively disabled System Restore/Shadow Copy.  Later inspection using PerfectDisk shows me I have the tiniest bit of metadata near the end.  Oh, and guess what?  When I removed the HP recovery partition (using the in-built tool), it didn't tell Windows that it expanded the partition.  Now I have to do the 6+ Hour intensive chkdsk!  Yipee!

---

