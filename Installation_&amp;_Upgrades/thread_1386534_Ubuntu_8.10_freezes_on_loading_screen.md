---
title: "Ubuntu 8.10 freezes on loading screen"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by Thq on 2010-01-20
I just decided to install Ubuntu on my computer using the Wubi windows installer to try it out.  But it freezes during the loading screen, it gets almost 3 bars and stops.  I found I could hide the loading screen and I got these:

run_program: exec of program '/sbin/modprobe' failed
run_program: exec of program '/lib/udev/vol_id' failed
run_program: exec of program '/lib/udev/scsi_id' failed
run_program: exec of program '/lib/udev/path_id' failed

they're repeated several times in random order.  I've tried adding noapic and nolapic (or something like that)  The live CD also freezes at the same spot, I thought installing it would make the problem go away.

The closest thing I found as an answer is that the image is corrupt, but I 'think' it's fine.  Any Ideas?

---

