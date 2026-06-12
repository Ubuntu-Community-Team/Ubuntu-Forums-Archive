---
title: "List installed package by date using Apt-Get"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by concord on 2006-11-25
With RPM based distros I usually use up2date or MandrakeUpdate, then I do:

[FONT="Courier New"]#rpm -qa --list | less[/FONT]

This way I can view the list of packages I've updated as well as the date/time they were actually installed.

Can I do this with apt-get (or dpkg or whatever) on Ubuntu Server 6.06LTS?  I've read the man page for both apt-get and dpkg but I can't make sense of it.

Thanks,

- Frank

---

### Post by MJN on 2006-11-25
Would the contents of **/var/log/dpkg.log** (and old rotations) suffice?

Perhaps processing this to suit with **grep install /var/log/dpkg.log **for example?

Mathew

---

### Post by concord on 2006-11-26
Yes, that works.  Thanks.  

I'm using:

[FONT="Courier New"]grep "status installed" /var/log/dpkg.log[/FONT]

That's working fine.

- Frank

---

### Post by MJN on 2006-11-26
Note you can also search the compressed rotated logs with **zgrep** (if that's of any use, perhaps for older packages).

Mathew

---

