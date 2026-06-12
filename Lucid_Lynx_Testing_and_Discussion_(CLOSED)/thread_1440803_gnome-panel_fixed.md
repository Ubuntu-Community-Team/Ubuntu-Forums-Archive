---
title: "gnome-panel fixed?"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vaskark on 2010-03-27
I know that the problems with nautilus and gnome-panel have been ironed out, but gnome-panel still doesn't load when I log into Gnome. I deleted ~/.gconf* in my home folder and logged back in ... and it still didn't work. I decided to create a new account to see if I encountered the same problem ... and gnome-panel loaded fine there. So the problem must be in my current account settings, but I'm not sure where. Can someone offer some advice? I'm currently using a temporary fix for gnome-panel in Startup Applications. I just want to track down the problem and solution.

Thanks!

---

### Post by PRC09 on 2010-03-28
I had the same problem and used synaptic to re-install gnome-panel and whatever else that was connected with it.However there were a bunch of updates at the same time so not 100% sure which fixed it.Hope this helps.....

---

### Post by plun on 2010-03-28
```
killall gnome-panel
```

fixes this error.

There is also a new kernel out 2.6.32-18 which works (Synaptic install, linux-image AND linux-headers), metapackage for this kernel comes later.

---

