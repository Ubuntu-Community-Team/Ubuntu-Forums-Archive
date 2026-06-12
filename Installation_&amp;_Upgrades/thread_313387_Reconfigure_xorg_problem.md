---
title: "Reconfigure xorg problem"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by alpacaman72 on 2006-12-05
what is the command to reconfigure xorg automatically, as the installation made it?
If I use:

sudo -dpkg-reconfigure xserver-xorg

It sends me into the setup program, but I keep making mistakes which crashes the x server. I want it to set it exactly how the install cd did, without the  setup getting any input from me.

---

### Post by pay on 2006-12-06
To get it exactly as the liveCD you could boot the liveCD and then copy the file /etc/X11/xorg.conf and then email it to yourself or something then copy it into your new installation, or you could chroot into your environment.

---

### Post by alpacaman72 on 2006-12-06
Thanks, I'll try that
by the way, in dapper it does the reconfiguration automatically, right?

---

### Post by confy on 2007-12-17
delete me

---

