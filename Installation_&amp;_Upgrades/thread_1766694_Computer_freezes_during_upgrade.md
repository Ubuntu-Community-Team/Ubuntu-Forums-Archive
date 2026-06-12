---
title: "Computer freezes during upgrade"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2011-05-24
Just wanted to upgrade my desktop computer and after the terminal shows:

...
Installling new version of config file /etc/apparmor.d/usr.sbin.cupsd ...
cups start/running, process 7944

The display froye, mouse does not move any more, keyboard does nothing, no chance to escape into a text terminal. Nada.

After rebooting the system I get a kernel panic.

This is now second of two upgrades to 11.04 that failed, and I do not know how often upgrades failed previously, but rather often.
This is very frustrating and not really helping to build my trust in Ubuntu :(:(:(:(

---

### Post by johann_p on 2011-05-24
It was possible to  boot into the previous version of Linux .. that got me into a text console.

In the text console it was possible to do
  sudo dpkg --configure -a 
which eventually installed the remaining stuff and allowed me to boot into Ubuntu 11.04.

---

