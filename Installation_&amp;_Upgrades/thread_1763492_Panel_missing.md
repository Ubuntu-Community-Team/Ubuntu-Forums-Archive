---
title: "Panel missing"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by fweth on 2011-05-20
Hi! I have a problem with my panel in Xubuntu 11.04. I installed the system and everything worked fine, but after running Upgrade Manager and restarting, the panel was gone. Typing `xfce4-panel' in the terminal yields the following error:

[FONT=Courier New]xfce4-panel-Message: Plugin "(null)-1" was not found and has been removed from the configuration

(xfce4-panel:1870): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
Segmentation fault[/FONT]

I tried reinstalling the whole system (with formating) twice, but the problem kept appearing. One thing I always did before updating the system, was deleting the bottom panel (which I cannot imagine to cause the problem). Please help, I love Xubuntu and would be desperate if forced to switch to Ubuntu again.

Thanks!

---

### Post by fweth on 2011-05-20
OK, apperently deleting the second panel before updating did indeed cause the problem. I reinstalled the system again and updated immediately afterwards. Then I did my personal configurations, including deleting the second panel and everything worked fine.

---

