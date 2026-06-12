---
title: "Re-installing Windows bootloader"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by Jelster64 on 2012-07-01
Hey guys,

So a long time ago I installed Ubuntu 11.10 on my Windows laptop using partitions. Recently a friend of mine tried removing all Linux partitions, leaving me with 3 partitions: Windows, Windows Bootloader and Windows Recovery. Unfortunately my computer boots nothing now. I've tried restoring it using a windows install cd, but that didn't work. All my computer does right now is displaying a command line saying grub rescue. Can I restore the windows bootloader somehow? Or just install grub or something? (My goal is to use windows bootloader and install ubuntu 12.04 using wubi btw)

---

### Post by darkod on 2012-07-01
Wubi is virtual inside windows so I never recommend it over the classic dual boot on separate partitions. But if you want to go ahead, you should be able to restore the windows bootloader with the windows cd. You have more detailed instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If that doesn't work, let us know. There is also one option using ubuntu tools from live mode.

---

### Post by Jelster64 on 2012-07-01
Thank you! Thank you so much! The referred thread worked! Problemo solveto.

---

### Post by Dlambert on 2012-07-01
Please mark this thread as solved.

---

