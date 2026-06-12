---
title: "Old compiz-switch may break Ubuntu 11.04 upgrade"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by baekgaard on 2011-04-28
In case anyone else run into the same problem as I did...:

I had an old compiz-switch package installed on my system. It has a "Priority: low" denotation in the package, which happens to break the installer somewhere mid-way.

A few manual edits of the package files fixed this and allowed me to run a "apt-get dist-upgrade -f", so I got my system running again.

But in case anyone sees this before attempting an upgrade: I guess remove the compiz-switch package (completely) before doing the upgrade may be advisable.


-- Per.

---

### Post by Sjoerd de Vries on 2011-06-24
Hi,

I had the same problem here, cost me a few hours. The dpkg parser seems to have become overzealous, I filed a bug report with them.

---

### Post by DiscoStu570 on 2011-08-31
Yea, i definitely didn't know about this before i tried to upgrade to the newest release (how would I) and I'm definitely pretty jammed up over it.  What would be the way to remove compiz-switch from the command line?

---

