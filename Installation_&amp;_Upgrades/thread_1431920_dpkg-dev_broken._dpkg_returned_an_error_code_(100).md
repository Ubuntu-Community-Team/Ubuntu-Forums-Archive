---
title: "dpkg-dev broken. dpkg returned an error code (100)"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by tomsoms on 2010-03-17
Since I got a update for dpkg-dev I cannot install anything anymore.
Every time I run sudo apt-get install something I get:
E: Sub-process /usr/bin/dpkg returned an error code (100)

I already tried: sudo apt-get autoclean
but the problem still occurs.

---

### Post by tomsoms on 2010-03-31
I solved it.
The permission on dpkg binary was wrong.

I found out the dpkg update had the file /usr/dpkg, cdmod to 000.
Probably because of a bug. Because I am sure i did not do that.

---

### Post by rajhanschinmay on 2010-05-03
I am facing the same problem.

It says:
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

I tried install, remove, clean, upgrade etc. all the options.

Is there a way by which I can upgrade the version 10.04 which just came to get rid of this problem.
Will distribution upgrade help?


Thanking you in advance.

---

