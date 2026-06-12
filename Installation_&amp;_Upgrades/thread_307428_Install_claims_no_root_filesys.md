---
title: "Install claims no root filesys"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Radhil on 2006-11-26
Allright, I've had a few Ubuntu versions under my belt now, but I'm kinda futzed here.  Got an Acer laptop that's run dual-boot WinXP/Ubuntu6.06 for a while now.  I'm trying to install the new 6.10 version (fresh install from the desktop install CD, 'cause I see the direct upgraders are having so much fun), and the install dialogs prompt me for partitioning through gparted, which I ignore and is fine from my old setup.  Then it asks for the assignments and reformatting, which is where it goes south.  I have hda2 set to be root, and hda3 to be swap, formatting both, my other two partitions just media mounts, and the idiot installer keeps insisting I have to set a root partition.  I've tried swapping around the root assignment and it still says I don't have a root partition set.  So can anyone tell me how to trick this stupid thing into doing it's job and start installing?

---

### Post by Radhil on 2006-11-26
Nevermind, it seems to like it just fine when I yank the partition completely and create a new one.  Why that's a requirement is beyond me, I'm not a fan of editing the partition table just for giggles.  Maybe someone can work on that.

---

