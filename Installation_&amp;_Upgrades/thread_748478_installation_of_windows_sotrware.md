---
title: "installation of windows sotrware??"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by girlleo19 on 2008-04-07
i was trying to install the cd that came with my samsung mp3 player on linux ubuntu and i succeeed but the problem is my computer won't recognize my mp3 player when i plug it in what do i do now help!!!

---

### Post by pseudo-random on 2008-04-07
It does recognize it to an extent.
With it plugged in could you run ```
lsusb
```
from a terminal and paste the contents here as well as mentioning what other USB devices are attached so we can filter them out.

---

### Post by atomkarinca on 2008-04-07
Open up a terminal and type:

```
lsusb
```

If you can see the manufacturer of your player then it's most probably auto-mounted. That means you can browse into your player like a flashdisk. It should be under /media folder. As far as the software goes, I can only suggest you to look it up on [Wine Application Database]("http://appdb.winehq.org").

---

### Post by Therion on 2008-04-07
[Ubuntu and Your iPod](http://www.linuxjournal.com/article/9266)

Long story short... Windows apps for Windows, Linux apps for Linux.  Try using GTKPod for managing your iPod in Linux.
[See here](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/) for more information and guidance.

---

