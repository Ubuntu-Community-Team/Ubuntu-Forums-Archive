---
title: "Adding Second Hard Drive moving /home"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by BSB1 on 2012-06-29
About a year ago I found official ubuntu documentation that gave step by step instructions on how to add a second Hard Drive and move /home to it.  It used rsync to move the files.  And did NOT boot from a live CD.  I have searched the official documentation for this information and I can't find it anymore and I didn't bookmark the location.  Does anyone have the link to the official documentation the explains this process?

---

### Post by oldfred on 2012-06-29
Welcome to the forums.

I do not know if this is the info you were reviewing:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


I actually prefer to have a fully bootable system on every hard drive, so I keep my /home on the same drive as my system, but every drive links to data on other drives. Then if a drive fails, I can boot the other even if I get errors on not mounting data from the failed drive. So instead of moving /home I moved all the folders like Music, Documents etc to my other drive.

---

