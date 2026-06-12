---
title: "reset drive UUID (messed up lvm physical volume)"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by draugen on 2007-04-27
Well, the title says it all I guess. After the 'normal' grub-install did not work as expected, i tried it myself. On the wrong drive. A drive which is part of a 950 GB LVM volume group. And contains shedloads of movies and music. As a consequence, the UUID of the drive has changed, confusing vgscan greatly.

Is (the data on) my volume group lost forever? or is there a way to (re)set the drive's UUID/MBR to what vgscan is expecting? vgscan is helpfull enough to tell me what it is expecting, at least.

---

