---
title: "Errors upgrading from breezy to dapper"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by nickoli_02 on 2006-06-11
OK, I'm working on upgrading from breezy to dapper. I followed the instructions at [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) for upgrading with a CD, and I'm getting these errors:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm using an alternate dapper CD, so... do I need to do anything about these errors or am I OK? lol... Thanks for the help!

---

### Post by JoshHendo on 2006-06-11
You have something else open that is using apt (eg, Add/remove programs, Synaptic. You can only use one at a time). Try restarting your computer then trying again.

---

### Post by nickoli_02 on 2006-06-11
Lol, OK... dumb error. That's fixed, now I get these errors:

Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/x/xfonts-core/xfonts-base_6.8.2.1-5_all.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Well I guess that's only one error lol. Any suggestions?

---

### Post by nickoli_02 on 2006-06-11
anyone? heh...

---

