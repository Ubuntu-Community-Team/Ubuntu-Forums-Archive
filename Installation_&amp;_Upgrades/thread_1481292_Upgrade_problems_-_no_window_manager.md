---
title: "Upgrade problems - no window manager"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by subject117 on 2010-05-12
I tried to upgrade my laptop to the latest version of Ubuntu but am having some problems.

The upgrade crashed after downloading all of the packages, so I had to reboot and finish the upgrade from the command line.  Eventually I was able to get to the end but when I logged in I would get just a black terminal in the upper left corner of the screen.  I figured there was a problem with xorg so I tried purging, reinstalling and reconfiguring xserver-xorg but that didn't work.  Actually it made things worse and now I can't get the terminal in the corner of my screen; the best I can get is a login prompt where I can log in and try to finish the upgrade but I don't know what to do.  Any advice?

Thanks!

---

### Post by subject117 on 2010-05-12
OK, discovered I needed to install ubuntu-desktop and my /etc/X11/xorg.conf file was missing.  I restored a backup and now I am back to the terminal in the upper left corner of the screen.  What do I do next?

---

### Post by subject117 on 2010-05-12
It seems I got it to work!  Unfortunately it required a lot of flailing to get it to work, but it basically amounted to installing some missing packages.

---

### Post by johntash on 2010-05-13
> **subject117 said:**
> It seems I got it to work!  Unfortunately it required a lot of flailing to get it to work, but it basically amounted to installing some missing packages.

Remember which packages were missing by any chance? Or how you found them?    

I'm still working on fixing a similar issue, but I'm about to try reinstalling ubuntu-desktop

---

### Post by subject117 on 2010-05-13
Yes, ubuntu-desktop was one of them, also kubuntu-desktop.  Then some xserver-xorg packages.  And some compiz packages.

Also, note that on the login screen (if you are getting one) you can pick a login mode.  Make sure you are picking gnome or kde and not some xterm mode.

---

### Post by johntash on 2010-05-13
Thanks subject117,  I was able to get it fixed by following the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=9262390&postcount=13").  Turns out compiz was trying to start up each time, and I guess just freezing.   I forgot I was using compiz before the upgrade just with all the effects turned off so I didn't even think it'd be the issue.   

I did reinstall ubuntu-desktop as well, but I think the link above(setting the WM manually back to metacity) is what actually fixed it

---

