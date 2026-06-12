---
title: "Boot freeze at pulseaudio"
date: 2015-06-12
forum: Installation &amp; Upgrades
---

### Post by seattle vic on 2015-06-12
Since I've upgraded to 15.04, my laptop takes two or three boot attempts to get to the login dialog.  When I check the syslog files, it seems always to freeze at:

Jun 12 14:03:24 laptop2 pulseaudio[1786]: [pulseaudio] pid.c: Daemon already running.

I have to do a hard power down then power up again.  It never gets through the 1st try, usually the 2nd or 3rd but never 4.  Does anybody have any idea why it's already running?

Thanks in advance...

---

### Post by seattle vic on 2015-06-12
Update: Never mind: I removed pulseaudio and then reinstalled it and the problem went away...

---

