---
title: "Need Help With Grub"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by btole79 on 2007-07-27
so after playing with ubuntu for the entire week i have decided i really like it.  unfortunatly i still need a copy of windows xp from time to time for my work and trouble shooting issues.  

this is my problem.  i had loaded ubuntu on half my 120gb HDD and everything was good.  today i finally got around to loading xp on the other half hoping to make a dual boot system.  unfortunaly windows is handling the boot menu now instead of GRUB.  is there anyway of reversing that change and saving my old ubuntu install or am i just screwed and have to start from scratch?

---

### Post by Pumalite on 2007-07-27
Just reinstall Grub following these guidelines: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grug: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by merlinus on 2007-07-27
Boot from the ubuntu live cd, open a terminal, and enter:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute your results for (hdx,x).

-merlin

---

### Post by MQMike on 2007-07-27
setup (hdx) should be setup (hd0)

(hdx, x) will come from the find command he gave you.

---

