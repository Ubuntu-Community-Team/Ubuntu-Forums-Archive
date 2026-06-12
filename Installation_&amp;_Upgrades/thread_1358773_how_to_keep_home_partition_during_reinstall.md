---
title: "how to keep /home partition during reinstall"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by m4lte on 2009-12-18
Hey there,
I want to reinstall Ubuntu. I have my /home on a separate partition and I would like to keep it without change. How do I have to proceed during the installation? Is there anything I have to be careful about when installing but keeping the /home partition?
How do I specify my /home partition without having it formatted?

cheers!

---

### Post by darkod on 2009-12-18
In step 4, select Manual Partitioning. You will see the list of current partitions. The linux ones will not have the mount points.
Click on your /, then at the bottom on the button Change. Change the filesystem from Not Used to ext4, tick the format box to wipe the old install, and select mount point /.
For /home, change the filesystem to what it was (ext4/ext3), DO NOT tick the format box, select mount point /home.
Do the same for swap (you can't select format for swap).
That's it.

---

### Post by m4lte on 2009-12-19
Worked great, thank you!

---

