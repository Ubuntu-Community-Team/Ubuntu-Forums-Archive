---
title: "Dapper shutdown problems after package upgrade on weekend."
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by ts2000 on 2006-03-20
The PC won't shutdown after I log in as a user.

It will shutdown when I boot and shutdown from GDM screen (without logging in.)

Shutting down from loging in the system stalls at "Stopping domand name service..."

I once had a screen that said something like "GlibC corrupt****"

When the system won't shutdown I get returned to the tty login: ansi screen - the system is frozen.

Problem is continuous.  Apart from that annoyance - but love dapper.  Any fix or suggestions please?

---

### Post by ts2000 on 2006-03-20
I don't really know what I am doing but I searched DNS in synaptic and found bind9 package.

I tried to reinstall this package and it could not shutdown 'domain name services' to i had to Ctl+c to exit.

---

### Post by ts2000 on 2006-03-20
It's amazing how going to bed and waking up to a fresh day can help one's vision.

The problem was fixed by removing the **Bind9 **package.  I think this package was installed as a dependency to another package.  But it's gone now and that other package may have to go without.

The system reboots fine now.

---

