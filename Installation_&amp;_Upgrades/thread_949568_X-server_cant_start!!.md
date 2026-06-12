---
title: "X-server cant start!!"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by ojve on 2008-10-16
Hi!

After last nights upgrade I cant start X-server!

I get:
Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.

What should I do?

Where is the syslog located? How do I connect to internet from the commandline, to see if there are new updates that might fix this?

Thx!
//T


UPDATE: I tried recovery mode and fix x, no luck. I also found syslog, but can't really make anything out of it.

---

### Post by ojve on 2008-10-16
Update again!

It seems there was some problem with inconsistencies in my file system. when trying xstart from command line I got that x server could not lock /tmp/.X0-lock because of a stale NFS file handle

When rebooting I accidentally made an unclean shutdown which triggered fsck and that appearently solved the problem.

You gotta be lucky sometimes!:)

//T

---

