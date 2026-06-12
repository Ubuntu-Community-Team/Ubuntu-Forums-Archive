---
title: "Thin client problem"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by alexrch on 2007-08-16
Hi guys,

I am trying to set up a thin client following [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto), but unfortunately when I start my thin client, I get this error:

/bin/sh: can't access tty; job control turned off

After pressing Alt+F1 I see this:

mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Thin client has no file system installed (it's a clean virtual machine running on a VMWare). What do you guys think could be wrong?

Cheers,
Alex

---

