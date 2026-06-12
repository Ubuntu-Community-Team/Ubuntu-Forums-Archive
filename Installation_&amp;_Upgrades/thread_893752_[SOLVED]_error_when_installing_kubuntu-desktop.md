---
title: "[SOLVED] error when installing kubuntu-desktop"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by desideratha on 2008-08-18
Hi I get this message when trying to install kubuntu desktop


:~$ sudo apt-get install desktop-kubuntu
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any ideas

---

### Post by coffeecat on 2008-08-18
Did you have Synaptic, update manager or the Add/Remove app open when you got this error message? Close any GUI apps that install/update from the repositories before invoking apt-get from the terminal.

---

### Post by desideratha on 2008-08-18
Hi, I cannot recall if I did...

I'll try your suggestion.. thanks

---

