---
title: "Can't install with synaptic"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by jasplund on 2005-07-27
All of the sudden I get this message (see attachment) when I try to install/uninstall something with synaptic. Any idea what's wrong?



Johan

---

### Post by Sam on 2005-07-27
Hum, can you translate the error ??? :?

---

### Post by jasplund on 2005-07-27
OOps sorry


Here's what it s

dpkg: Configuration error: Unknown flag log: Succeeded

EDIT: It's so annoying when things are partly in Swedish and partly in English.

---

### Post by jasplund on 2005-07-27
I just remembered I

"Commit Log for Wed Jul 27 08:47:19 2005


Downgraded the following packages:
dpkg
dpkg-dev
dselect"

I downgraded them to the version in hoary-security I had previously upgraded them to the version that was in the (now) official backports a few days ago.

I guess something's happened with my dpkg-configuration. But how do I fix it?

Johan

---

### Post by jasplund on 2005-07-27
dselect says that dpkg and dpkg-dev is unpacked but not configured. What should I do?

---

### Post by jasplund on 2005-07-27
Trying to configure unconfigured packages with dselect gave me this 

"running dpkg --pending --configure ...
dpkg: konfigureringsfel: okänd flagga log: Lyckat

dpkg --configure returnerade felkod 2."

dpkg: configuraion error: unknown flag log: Succeeded

Perhaps it means Locked and not Succeeded but in that case it's a terribly bad translation

---

