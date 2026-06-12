---
title: "Initial setup for Xorg doesn't allow me to log in."
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by neltnerb on 2005-07-22
This problem puts me at a loss, I've been using debian for years and have never seen something like this.

I did the standard auto-ish installation, and then redid the installation in expert mode with the same result.

In any case, when the ubuntu brown screen pops up and I try to log in, it fails in all modes with the following error:

---

running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "neltnerb"
/etc/gdm/Xsession: Beginning session setup...
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server

---

with more of the same beneath in the log.

Now, I have no idea why this would be happening, I've never had this sort of problem with any installation ever before, so I'm quite certain that my hardware is all kosher. And then all the configuration files for xorg are in places I'm not used to, so I can't figure out where the appropriate files are anymore...

What gives? Anyone have any ideas? I imagine someone else is having this problem too, no?

-Brian

---

### Post by neltnerb on 2005-07-24
Has anyone had any ideas?

Has anyone else even had this problem? I can't think of anything special about my computer (all components are about 1-2 years old, so it's all supported).

-Brian

---

