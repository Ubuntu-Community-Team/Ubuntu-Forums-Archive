---
title: "Where is the openbsd-inetd program?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by PhilKarras on 2008-04-15
I know where it is supposed to be, /etc/init.d but since it did not install when I installed the Ubuntu Server I used:

"sudo apt-get install openbsd-inetd"

to install it & it did NOT go into /etc/init.d

Do I need to uninstall it & do it again & tell it where to install this time?

I do not know how to find it, or uninstall it, or install into a known location, help with all of these would be appreciated.

---

### Post by Deathrend on 2008-04-15
I would do this:

```

sudo bash
cd /
find -name openbsd

```

This may turn up a lot of results, it also depends on what the exact name of the normal init.d file is.

As a note, I've never used OpenBSD, I know what it is, just never seemed like something worth using for me (I have both a BSD server, and two SunOS servers) so I don't know the exact name of the file, or how it actually installs, but this is my best guess.

---

### Post by PhilKarras on 2008-04-15
OK thanks, that did it and guess what, it was where it was supposed to be, I must not have used ls correctly?

OK, then there's only one other problem, why can't I Telnet into the Linux Server box?

---

