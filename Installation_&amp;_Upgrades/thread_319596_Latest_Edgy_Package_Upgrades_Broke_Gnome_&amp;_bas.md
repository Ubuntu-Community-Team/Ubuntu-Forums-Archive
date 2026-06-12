---
title: "Latest Edgy Package Upgrades Broke Gnome &amp; bash_completion"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by nuclear_eclipse on 2006-12-15
Ubuntu told me I had 72 packages to upgrade, most of which were language updates, but some were notable, like kernel images, gdm, and kopete.  After it got done installing the new packages, it asked to reboot (so new kernel could load I presume). Now I can't log in to a Gnome session.  It fails out with the following errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/log/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "john"
/etc/gdm/Xsession: beginning session setup...
/etc/bash_completion: 44: Syntax error: Bad substitution

Everything was working perfectly well before the upgrade, and I'm not competent enough with the internal workings of X, Gnome, and bash_completion stuff to know how to fix his problem.  Does anyone have any suggestions?

Thanks

---

### Post by SorApp on 2006-12-22
Hope this helps.  I had the same problem.  Totally sucks but I managed to find a thread that fixed it for me ([https://launchpad.net/distros/ubuntu/+source/gdm/+bug/60079]("https://launchpad.net/distros/ubuntu/+source/gdm/+bug/60079")).  Long story short:

Change "#!/bin/sh" to "#!/bin/bash" in ./etc/gdm/Xsession

Apparently the new version of bash is stricter than its predecessor.

---

