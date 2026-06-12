---
title: "today's upgrade failed"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by marcadams on 2008-04-19
Hi;

I'm running Hardy, and whilst performing the latest upgrade today (notified by the upgrade icon) - the gui stopped responding, After 5 mins the only option was a hard reboot.

After the reboot I still had some packages to install, but I get the following instructions when trying to perform an update. Running the command does nothing.

The error is:
"
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
"

How can I make the package manager happy again?????


many thanks !
:confused:

---

### Post by Pumalite on 2008-04-19
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by marcadams on 2008-04-19
Hi Pumalite - Many thanks for your help - those series of commands did the trick !!

---

### Post by Pumalite on 2008-04-19
You are welcome. Good luck.

---

