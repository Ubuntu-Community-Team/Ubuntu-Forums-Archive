---
title: "Restart hangs on Hardy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by eljaco on 2008-04-26
Hi,

I have a Dell PowerEdge 400SC server and with previous versions of Ubuntu, I was able to reboot without a problem, but now with Hardy, whenever I tell the system to restart (either through UI or "sudo reboot") the system shuts everything down and simply takes me to a blank screen with a blinking "_".

In order for me to get the system to restart, I have to manually press ALT+CTRL+DEL - which is fine for the most part, but I sometimes work remotely and would like to be able to reboot the machine.

Anyone know how to fix this?

---

### Post by matogrosso on 2008-05-03
Same problem here !

---

### Post by satellite360 on 2008-05-04
Same problem on a Dell Dimension 9200

---

### Post by mjtg on 2008-05-28
I'm seeing the same thing here.  This doesn't happen all the time, it seems to be only after the PC has been running for a few days (ie. if I try rebooting/shutting down within a day or so of last reboot, it's ok).

For me, this is part of a bigger problem on my PC.  It seems that my /sys filesystem is getting into a bad state after a day or so.  If I try to do a "ls /sys" from a console, it hangs.  Also, Openoffice hangs when starting up (when I run an strace on Openoffice, it's hanging at the point where it's trying to access /sys).

So, is anyone else seeing this problem with /sys ?

---

