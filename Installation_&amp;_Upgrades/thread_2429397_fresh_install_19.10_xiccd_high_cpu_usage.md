---
title: "fresh install 19.10 xiccd high cpu usage"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by rattskjelke on 2019-10-17
I just did a fresh install of Xubuntu 19.10 and an autostart program called xiccd is running several instances using up 99% CPU and about to overheat my laptop.

---

### Post by #&amp;thj^% on 2019-10-17
xiccd

xiccd is a simple bridge between colord and X. It does the following tasks:

 * Enumerates displays and register them in colord;
 * Creates default ICC profiles based on EDID data;
 * Applies ICC profiles provided by colord;
 * Maintains user's private ICC storage directory.

It does basically the same as gnome-settings-daemon color plugin or colord-kde
but does not depend on any particular desktop.
Is there a need to have it Auto-Start?

---

### Post by rattskjelke on 2019-10-17
I disabled autostart so it won't melt down my CPU.
This is something new in 19.10. As far as I know I don't have anything that uses ICC color profiles so I probably don't need it.

---

### Post by Pres-Gas on 2019-12-23
I know there was a bug reported on this ([https://bugs.launchpad.net/ubuntu/+source/xiccd/+bug/1845800](https://bugs.launchpad.net/ubuntu/+source/xiccd/+bug/1845800)), but no fix as of yet.

I am trying one package from the PPA there and seeing how it works.

I actually downloaded the package direct from here ([https://launchpad.net/~xubuntu-dev/+archive/ubuntu/experimental/+packages](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/experimental/+packages)) and used the software center to install it. We will see how this goes...

---

### Post by truscellino on 2020-01-07
Hi everyone,
Yes I think bug is well identified in both Debian and Ubuntu. It happens with xiccd version 0.2.x after log out and log in and a few other situations.
For current 19.10 users, I think a more elegant (?) fix is proposed in xiccd's bug report here: [https://github.com/agalakhov/xiccd/issues/9](https://github.com/agalakhov/xiccd/issues/9)
It does change the autostart settings while keeping the same xiccd version and avoiding manual installs, ppa etc.
It worked for me...
Thanks, Marc

---

