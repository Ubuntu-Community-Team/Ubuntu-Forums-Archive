---
title: "More Hard drive problems"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by rivervalleyprinting on 2005-08-28
I installed a slave drive just to hold music and stuff. It wasnt the easiest thing Ive ever done but it finally showed up in the media folder. But now whenever I try to put anything in there it says I dont have the right clearance. Im the only user on this computer though. So just to see what happens I did a "dmesg" in a terminal and it said this "EXT3-fs: Unrecognized mount option "uid=1000" or missing value". So can anyone fix either of these problems and are they related?
I also ordered my "Linux for Dummies" today so hopefully I can stop bothering you nice people with this silly stuff.
Thanks Tony

---

### Post by jasmuz on 2005-08-28
Open your /etc/fstab, verify the line you added and modify adding after the filesystem the "uid=1000" and "user", so you can have write access, this is just an example:

/dev/hda1       /media/music  ext3    uid=1000,user     0       0

---

