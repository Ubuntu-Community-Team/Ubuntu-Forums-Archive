---
title: "blank grey screen after updates"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by myfigurefemale on 2008-05-29
After running updates that were up to 41 days old, now I get a blank human colored screen when I log in to a Gnome or X session.  After a minute it fades to grey. No background pic, no task bar, nothing. I've been using "failsafe gnome" to be able to get in and make changes.  Does anyone know how to fix this?

---

### Post by ridgeland on 2008-05-31
I would guess it's either the result of a kernel upgrade or X-system.
Check in /boot/grub do you have multiple files like:
vmlinuz-2.6.20-15-generic
If so you might boot to an older kernel and see it that solves it.  Grub should present these options at boot time.
The second place I would check is /etc/X11
Do you have several xorg.conf files of various names?  If so make a safe copy of xorg.conf (like cp to xorg.conf.20080531) then copy in the most recent of the other xorg.conf files.  Use gedit to view the files to see that this could be useful.

---

