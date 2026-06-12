---
title: "Where do TTY's get launched?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by tcroswell on 2010-01-31
I've installed Ubuntu 9.10.  6 TTY's are launched at startup.  In previous versions of Ubuntu/LINUX these were controlled from /etc/inittab.  In 9.10, I've seen documentation that with the new startup mechanism, these have been moved to /etc/init and that there are ttyX.conf files for each tty.
 
So far so good, or so I thought.
 
So how come, if those files are removed, the getty and the TTY's are still launched by the OS upon reboot?
 
Where are these really configured and started?
 
Thanks,
 
Tom

---

### Post by feistybill on 2010-02-06
.

---

