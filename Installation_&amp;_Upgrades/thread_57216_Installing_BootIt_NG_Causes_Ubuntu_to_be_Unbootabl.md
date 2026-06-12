---
title: "Installing BootIt NG Causes Ubuntu to be Unbootable"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by BrokenPipe on 2005-08-15
I installed Windows, then Ubuntu, and grub worked fine.  But I like BootIt more as a boot loader.  I installed BootIt and BootIt says that my Ubuntu partition is unbootable.  Any ideas what may have happened or how to fix it?

---

### Post by blop on 2007-09-20
hey,

i use Bootit NG as well, without seeing how your partitions are mapped and where you installed BING its hard to say. I would guess you have over written the MBR with the one of the install or your partitions were setup in ubuntu in conflict with BING.....very possible.

I would suggest starting again...

1. format
2. load bing
3. setup partitions for xp ubuntu
4. install xp
5 reactivate BING as xp is rubbish and overwrites MBR without asking
6 install ubuntu...but make sure you use partitions u made in BING and that you install GRUB to the ubuntu / partion not let install to default MBR record.
7. enjoy

---

### Post by kellemes on 2007-09-20
Excuse me, but reinstalling is a bad Windows-habit..
Just get SuperGrubDisk for the easiest way to boot into any OS you have installed and/or reinstall your bootloader.. It's a 5 minute job.

---

### Post by blop on 2007-09-23
its possible a partition was overwritten tho.... BING allows 200 primaries instead of the standard 4 which makes using any other partiton program and BING dangerous.

use the BING it has made my XP / VISTA / LINUX install super easy and absoultley a doddle to image and recover.

---

