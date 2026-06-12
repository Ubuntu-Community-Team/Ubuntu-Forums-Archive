---
title: "[solved]Error message after upgrading..."
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by Jahidul_Hamid on 2014-08-25
Error message:
Unknown configuration key `foreign-architecture' found in your `dpkg'
configuration files.  This warning will become a hard error at a later
date, so please remove the offending configuration options and replace
them with `dpkg --add-architecture' invocations at the command line.

---

### Post by Jahidul_Hamid on 2014-08-25
found solution:
sudo dpkg --add-architecture i386
sudo apt-get autoremove --purge
sudo apt-get clean
sudo apt-get update

---

