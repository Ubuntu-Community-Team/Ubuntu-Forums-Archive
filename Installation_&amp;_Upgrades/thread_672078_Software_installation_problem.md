---
title: "Software installation problem"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by lacroixmouz on 2008-01-19
When I am tryin to run a installer.exe via Wine, when The installer asks me to put Disc 2, I click to eject the 1st disc and it says that it cant be rejected cause it used by another program
What should I do? please explain easy because I am a new nub

---

### Post by dabang on 2008-01-19
You need unmount the disc manually, either by right clicking the CD icon on the desktop or by
```
sudo umount /path/to/mount_point
```
whereas "/path/to/mount_point" probably is /media/cdrom.

---

