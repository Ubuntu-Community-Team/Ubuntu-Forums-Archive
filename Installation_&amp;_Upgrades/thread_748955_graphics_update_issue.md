---
title: "graphics update issue"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by eman7613 on 2008-04-07
So, i isntaled ubuntu on a new computer, just finished setting everything else up, and its time to get my gpu (8800 gtx) running with 3d support. i used envy (.9.10) to intstall the latest drivers since the restricted drivers manager always installs out of date drivers. restarts and everything seems to work, the little buble even pops up to say restricted drivers are in use, GREAT! 

 i go to turn on the desktop effects, and click the bubble and it pops up saying it needs to enable restricted drivers, i click ok, and it says restart (i dont know why) and it restarts. next thing i know, Ubuntu wont start, the bar dosent even budge on start up. does anyone know what just happened or how i would go about fixing it? (posting from M$, it still works)

---

### Post by tubasoldier on 2008-04-08
The problem is that you installed the drivers using Envy. Envy uses the lastest drivers while the drivers in the repositories are a little older. You pointed this out yourself. 
As a result you now have two separate Nvidia kernel modules installed and they are conflicting with one another. 

You can boot Ubuntu up in the rescue mode and change the /etc/X11/xorg.conf file a little to get a graphics environment to better troubleshoot.

change the driver from nvidia to nv. This will allow you to get a graphical environment, without all the frills. This will also allow you to uninstall the restricted-drivers or envy. I reccomend removing envy. After every kernel upgrade you will have the same issue.

---

