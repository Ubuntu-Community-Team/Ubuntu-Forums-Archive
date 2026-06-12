---
title: "Dual OS booting questions"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by roneilden on 2006-09-26
When I changed to 6.06LTS I fitted a new 160Gb SATA drive, loaded Ubuntu on and went on happily from there. I left my old M$ XP Pro on an old 40Gb IDE drive unplugged but still in the box. Now I have to resurrect XP for a couple of specific programs so I think I'll need to dual boot. I have read some posts on this but most seem to assume XP was loaded and running when the Ubuntu install was carried out. Are the solutions relevent to this configuration, if not what is, short of a Ubuntu reinstall.

---

### Post by ajgreeny on 2006-09-26
Need to know what your partition numbers etc are with just the one disk installed and then with both installed, and which is the primary disk and which the secondary.  It may mean that you get back to the windows MBR booting straight into windows when you re-attach that drive but I think it will be a case of, try it and see what happens.  If you're lucky you may simply be able to boot a live CD and edit the ubuntu menu.lst file to take account of the partitions, but I suspect it may be more difficult than that.

Put the old disk back in and see what happens.  Alternatively, of course, you can simply swap drives back temporarily and use windows for as long as you need and then come back to ubuntu by swaping back again, totally ignoring dual booting possibilities.

---

### Post by alanmzifa on 2006-09-26
I've just done something like that. If you haven't seen the thread already it's [here]("http://ubuntuforums.org/showthread.php?t=265103").

I also found [this]("http://www.psychocats.net/ubuntu/partitioning") and [this]("http://users.bigpond.net.au/hermanzone/p15.htm") useful.

---

### Post by roneilden on 2006-09-26
I have tried to boot from the IDE XP drive without the SATA Ubuntu disk connected and bios changed to boot from hdd0 without success. I would normally boot from ATA0.
Disks Manager lists IDE XP drive as dev/hda1 at /temp/disks-conf-hda1 and SATA as dev/sda1 for the Ubuntu root partition.
current /boot/grub/menu.lst shows SATA Ubuntu root as (hd0,0)
current /boot/grub/device.map shows only (hd0,0) dev/sda
I'm not sure what else include that may help.

Thanks for the advice so far

---

