---
title: "how do I use modprobe"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by alexofindy on 2005-02-20
This is a newbie question.  It's been a while since I've tried to install Linux, and the world has changed.

I'm trying to install ubuntu on an old system.  During network detection the installer reports that it can't find my network card, and suggests I go back and install a module for it. 

I try to do so, by opening up a shell.  The module it needs for my network card is
smc-ultra.ko
which is present in the /lib/modules/2*/kernel/drivers/net directory. 

But when I try to install it with modprobe, modprobe says it can't find the module.
E.g., 
modprobe /lib/modules/2*/kernel/drivers/net/smc-ultra
returns "Fatal error - module not found" or something similar.

I've tried variations on the name (e.g., smc-ultra.ko) and cd'ing to the above directory and modprobe ' ing from there.  Same error.

What am I doing wrong?  Do I need to configure modprobe before I use it?  Should I just install ubuntu without network support and then add the module once I have a working bootable system?

Thanks!

---

### Post by wallijonn on 2005-02-20
#man modprobe

[http://www.die.net/doc/linux/man/man8/modprobe.8.html](http://www.die.net/doc/linux/man/man8/modprobe.8.html)

What do the logs in /var/log say?

If you cd to that directory (in my case it is /lib/modules/2.6.8.1-3-386/kernel/drivers/net/ ) can you execute it from a root terminal?

---

