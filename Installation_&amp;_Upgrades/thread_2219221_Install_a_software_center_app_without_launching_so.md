---
title: "Install a software center app without launching software center?"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by cxw1985 on 2014-04-23
Hi guys,

I run Ubuntu 14.04 with only Flubox. I'd like to install Steam but it seems to require me to install software center. I tried to run "apt-get install steam-launcher" but didn't work. Is there a way to install an app from software center using commands?

Kind regards,

Xianwen

---

### Post by ajgreeny on 2014-04-23
In what way didn't it work?  Could it not find steam-launcher; what error messages do you get?

We need more info to be able to help you as the command you mention should work, assuming that you used **[COLOR=#ff0000]sudo[/COLOR] apt-get install steam-launcher**.  Software-centre, synaptic, aptitude or apt-get all use the same software underneath to install applications.

---

### Post by cxw1985 on 2014-04-23
Thanks. So the right package name is steam, not steam-launcher. Problem is now fixed.

---

