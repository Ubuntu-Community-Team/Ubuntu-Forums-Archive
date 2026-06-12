---
title: "xfce4-appfinder"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by kdjantzen on 2010-11-13
Hi,

I am running Ubuntu 10.04 with xfce.
After booting appfinder is automatically started on workspace 1.
How can I stop this autostart of appfinder?

---

### Post by azertyh on 2010-11-13
hello,
see settings/xfce 4 settings manager/session and startup, and application autostart tab, if appfinder is there, untick it.
one another reason is that you ticked "save session for future logins" when you shut down your computer. close appfinder, untick "save session for future logins" and log out or restart.

---

### Post by kdjantzen on 2010-11-13
Hi,

I have neither the appfinder in the tab for autostart application nor is "save session for future logins" checked.

The solution is:
The user, that has the effect enters on a TEXT console (Ctr-Alt-F3)

rm  -rf  .cache/sessions

I don't know how and when this session setting was generated but 
now this slight annoyance is gone.

Thank you.

---

