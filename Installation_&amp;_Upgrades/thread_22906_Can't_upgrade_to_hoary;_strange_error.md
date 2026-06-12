---
title: "Can't upgrade to hoary; strange error"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-03-30
I've tried this several different ways. I've tried twice with apt-get and now with synaptic. Each time it hangs at the same point and then spits out a bunch of terminal output that makes no sense. I've changed all the sources to "hoary" and I have even tried to disable all but the primary Ubuntu sources to no avail.

Here is the error I get:

> dpkg-deb: file `/var/cache/apt/archives/diveintopython_5.4-1ubuntu1_all.deb' contains ununderstood data member data.tar.bz2    , giving up


I tried to google the above, and just parts of it, but I get nowhere.

---

### Post by alastair on 2005-03-30
No idea. It looks like an obscure dpkg error - but google doesn't help much.

Have you tried removing this package "diveintopython" before doing any upgrade?

---

### Post by Psquared on 2005-03-30
[QUOTE=alastair]No idea. It looks like an obscure dpkg error - but google doesn't help much.

Have you tried removing this package "diveintopython" before doing any upgrade?[/QUOTE]

Actually, I was able to work around this problem, but now I get a bunch of text spit out in the terminal window. If you do a search for "upgrade to hoary" you will find the other thread where I posted this.

If you have any ideas let me know.  [-o<]

---

