---
title: "Xorg broken during dist-upgrade - XGL works -Dapper F5"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by Monster_user on 2006-08-13
I installed Dapper (6.04?) Flight 5 a while ago. I have been upgrading every month since, and I am now using the full release of 6.06 LTS.

The whole point of using Dapper was to try out/compare XGL/Compiz and Transset/Xcompmgr within a Debian distro.

Now, Xorg has stopped working. It instead seems to hang, and then a gives an empty error log, and the "X could not start" error.  I can still load XGL.

I can also load an old Xorg binary by linking to it (-> X.old). Compositing is broken when I link to the old version. So it is not much of a fix...

**Edit**
-----------------------------------------------
Okay. After updating today, it gives an error that "/usr/bin/X' is not executable.

'./X' gives an "Xwrapper.config" error.

"Unable to open wrapper config file /etc/X11/Xwrapper.config."

--------------------------

It seems that I had backed up my xorg.conf to my home folder, and that was causing the problem. Now to find a way to keep the composite extension from loading too early, and crashing Gnome.

---

