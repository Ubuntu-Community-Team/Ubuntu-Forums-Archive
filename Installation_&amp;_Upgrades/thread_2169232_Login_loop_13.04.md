---
title: "Login loop 13.04"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by neuman1812 on 2013-08-21
I recently upgraded to 13.04 and I'm stuck at a login loop.  I can switch to Alt F 1 and I am able to log in there but not using GDM or lightDM.    Guest account also has a loop.   I created a new account, same problem.   

My .session has the following.

openconnection: connect no such file or directory.
Cannot connect to brltty at 0
Mkdtemp private socket dir permission denied.


On the last error I checked the permissions on /tmp. And they are set correctly.

---

### Post by steeldriver on 2013-08-21
Are you using an xfce4 session? do you have any other desktop sessions (ubuntu, gnome, lxde etc.) that you can choose from the login screen?

---

