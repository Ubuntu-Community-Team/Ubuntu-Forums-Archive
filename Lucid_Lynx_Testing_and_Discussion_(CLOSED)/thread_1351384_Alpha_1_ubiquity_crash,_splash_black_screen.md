---
title: "Alpha 1 ubiquity crash, splash black screen"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-12-10
Alpha 1 on Compaq Presario ati integrated graphics
1.  Splash is a black screen.  I can workaround with "nomodeset".
2.  Boot and check CD for errors.  I think it ran, don't know what it said, black screen.
3.  Ubiquity crash from normal boot, launchpad bug #494608.  I was trying to do manual install to a partition with a tired Lucid, see #4.  There's also a karmic and a jaunty on the disk already which I hope to preserve.  The bug report says don't select format and continue.  I'll try gparted to do the format ahead of the install....
4.  Lucid from updates is pretty sick.  Opening a window overwrites the top line with Applications Places System.  Clicking on the bottom left to display desktop doesn't even think there's a window manager running.

Jerry

---

### Post by ranch hand on 2009-12-10
If you create your partitions ahead of time and then run the installer and do NOT have the installers partitioner do ANY formating, it is supposed to work.

Mine isn't quite done downloading so I do not know from my own experience.

---

### Post by waspbr on 2009-12-10
ubiquity will only crash if you try to format partitions, it will work if you simply use gparted to create/format your partitions and use ubiquity just to install lucid.

---

### Post by jerrylamos on 2009-12-10
Install worked O.K. after pre-formatting the partition by running gparted from a karmic partition.

Do note that gparted is no longer a default package.

Jerry

p.s. still get black text on a black screen on the CD booting up unless I replace "splash" with "nomodeset".

Jerry

---

