---
title: "Quick Question -Prepare partitions"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Preserved_Killick on 2008-11-14
Hi,

I'm in the middle of a clean 8.10 install at the "prepare partitions" screen. I've got /dev/sda3 as my home partition from a previous install, which I want to keep intact. The screen I'm looking at has the partition, but has the mount point blank.  If I select that partition, I see "Use as: do not use the partition". 

I'm a little nervous here, is this just telling me that the installer won't touch my home partition? And when all is done, my home partition with home directory will still be there????

..waiting for some input before I continue...

-Preserved

---

### Post by mikewhatever on 2008-11-14
You have to go with the manual partitioning and explicitly specify all mount points (/,/home, swap) for the root swap and home partitions. Make sure you don't tick the formatting box for home.

---

### Post by taurus on 2008-11-14
I assume you've picked _Manual_ when you get to the partition screen.  Just mount a partition as / and format it to ext3.  However, mount your /home partition to /home as ext3 but tell the installer not to format it.  Make sure there is no check mark in a little box in front of the mount point, /home.

---

### Post by Preserved_Killick on 2008-11-14
I would think the installer would see that the partition is already ext3 and mounted as /home? If I run Gparted (before any install) it can see my /dev/sda3 as ext3 and /home. 

I just want to be sure the installer does not mess with that partition and the stuff in it. 

I've selected "edit partition", then use as ext3 with Mount point /home. Careful to leave "Format the partition" unchecked. 

Am I safe with this?

---

### Post by mikewhatever on 2008-11-14
You should be safe, just don't forget to specify all three paertition. The installer wouldn't know anything about mount points from the previous installation, although it may see partition numbers and file systems.

---

### Post by Pumalite on 2008-11-14
You can ignore /swap. The installer will recognize the one you already have.

---

