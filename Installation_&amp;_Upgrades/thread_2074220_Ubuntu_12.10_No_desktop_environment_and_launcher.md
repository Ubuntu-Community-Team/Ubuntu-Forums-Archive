---
title: "Ubuntu 12.10 No desktop environment and launcher"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Freedomfriez on 2012-10-21
Hello,
I recently upgraded to 12.10 from 12.04, and when I log in the only thing I see is my wallpaper. I can right-click and access to the wallpaper settings but that's it. No top bar, no launcher, no desktop icons... I have a HP 625 notebook.



Thanks in advance for help :)

---

### Post by syndicate0017 on 2012-10-21
Was this on a fresh install? Or did you by chance install nvidia-current drivers? I had the same problem if you ran into it after install the proprietary drivers. I ran

```
sudo apt-get purge nvidia-current
```

Rebooted to a working desktop with nouveau drivers and then installed nvidia-current-updates through software sources. Rebooted again and my system booted to a working desktop with updated drivers.

*Just saw you said you updated. So not sure my advice really applies*

---

### Post by Freedomfriez on 2012-10-21
I can't even access to the terminal... :/

---

### Post by Freedomfriez on 2012-10-21
[http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing/202782](http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing/202782)

Hey, 
did this and it fixed my problem! thanks :)

---

