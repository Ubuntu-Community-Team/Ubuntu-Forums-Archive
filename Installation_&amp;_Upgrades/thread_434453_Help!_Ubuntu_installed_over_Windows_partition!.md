---
title: "Help! Ubuntu installed over Windows partition!"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Zonoid on 2007-05-06
I just installed Ubuntu for the first time, and I'm worried I installed it over my Windows XP partition when I allowed it to automatically partition the disk. How can I check to see if the Windows partition is still there?  Is there anything I can do to recover the files, or is all hope lost?

---

### Post by merlinus on 2007-05-06
Type this in a terminal:

sudo fdisk -l

Post the results.

-merlin

---

### Post by Zonoid on 2007-05-06
It says:

"Device  Boot  Start  End  Blocks  ID  System
/dev/sda1  *1        19268  154770178+  83   Linux
/dev/sda2  19269  19452  1477980           5   Extended
/dev/sda5  19269  19452  1477948+       82  Linux swap/Solaris"

---

### Post by merlinus on 2007-05-06
Sorry to say, it looks as though windows is hosed.

Hopefully you backed up your data before installing ubuntu.

:( 

-merlin

---

### Post by Zonoid on 2007-05-06
Would a partition recovery program be able to salvage anything? I didn't make backups, and I had very important files on that partition.

---

### Post by junior28862 on 2007-05-06
Most likely that would not help because the HDD has been reformatted.  Reformatted with a different type of file system on top of that (NTFS to ext3).

---

### Post by Zonoid on 2007-05-06
Well, I guess that's a lesson learned... any last things I could try? There hasn't been any kind of recovery software developed for this specific situation?

---

