---
title: "Installing IW-0.9.19 ...pkg-config not found?"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by mktg82 on 2010-02-11
Hi all, I'm trying to install iw-0.9.19 on xubuntu.

When i type the command "make", i get:

/bin/sh: pkg-config: not found
/bin/sh: pkg-config: not found
Makefile:38: *** Cannot find development files for any supported version of libnl. Stop.


I read the Readme file and it says:

"To build IW, just enter make. If that fails, set the PKG_CONFIG_PATH environment variable to allow the Makefile to find libnl".

libnl-dev is installed, so I guess that I must set that PKG_CONFIG_PATH variable to solve my problem, right? But I don't know how to do it... can someone help me?

---

### Post by mktg82 on 2010-02-12
there's anyone?

---

### Post by slw369 on 2010-04-03
I had the same problem fixed by installing pkg-config!

sudo apt-get install pkg-config

---

