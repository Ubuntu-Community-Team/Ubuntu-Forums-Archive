---
title: "Resizing the ntfs Partitions error"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by jvanoort05 on 2007-04-04
I have a XP computer  that i want to dual boot UBUNTU on. i started up the live cd and tried to resize my ntfs partition. gparted started but then reported a error while trying to shrink the partition. what is wrong?

---

### Post by garlik42 on 2007-04-04
Is there any more information, than "reported an error".
This might be a fix for you, boot whatever OS has created the NTFS partition, and defragment it. I had this problem once.

---

### Post by jvanoort05 on 2007-04-10
Ok i tried this for several days in a row and it seems to be working. i can see that the files are being moved away from the end of the partition but there are several clusters of unmovable files at the end. how do i get rid of those or can't i.

---

### Post by garlik42 on 2007-04-17
If the files won't defrag (red) they are system files.
Either a swap file or a hybernation file. 

In power settings (control panel) turn off hibernation (after your done you can turn it back on)
Also, make the swap file either 0 bytes or as small as possible (right button system properties on my computer)/Advanced/Virtual memory.

good luck.

---

