---
title: "Nvidia 180.22 and Clocksource unstable - Long boot time"
date: 2009-01-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by egesia on 2009-01-27
Hi,
After installing the nvidia-glx package (180.22) on Ubuntu 9.04 my boot time increased and the screen shows the nvidia logo for about 2 minutes.
Dmesg shows this new line:
[ 95.557070] Clocksource tsc unstable (delta = 4682796731 ns)

I also tried changing my 8400 gs with a 8600 but the system doesn't boot (nvidia logo flickering and system stucked). Booting with ubuntu nv driver is fine.

On Ubuntu 8.10 i haven't any issue with 180.11 (glx) package but 180.22 drivers from nvidia site doesn't work.

What can i do to investigate the problem and submit all the needed information to ubuntu dev team?


```

Jan 27 12:51:54 luca-desktop kernel: [   16.801368] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jan 27 12:52:00 luca-desktop kernel: [   22.311806] Clocksource tsc unstable (delta = 4687166498 ns)
Jan 27 12:54:07 luca-desktop kernel: [  148.994927] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```

---

### Post by lithorus on 2009-01-27
You should look in here :
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

