---
title: "Add/Remove Application assert failure"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by jmsmith4 on 2007-06-10
I downloaded the 7.04 .iso image yesterday (June 9) and installed it on a fairly old machine (1.4 GHz Pentium, 256k memory, 60 Gb disk).  I did 50 updates.  So far so good. Then I ran the Add/Remove Application program and it froze.  Running it from a command prompt, I see an assert failure.  

$ /usr/bin/gnome-app-install

** (gnome-app-install:5791): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1532: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)


Any suggestions?  Is there an update for gnome-app-install? 

Jimmy

---

