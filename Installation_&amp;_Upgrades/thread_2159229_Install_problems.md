---
title: "Install problems"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by IvanMP on 2013-07-02
Hi all,

I [FONT=Verdana]recently try to install bind9 and dnsutils and i have the following errors

[/FONT]> root@nagios:~# apt-get install bind9 dnsutilsReading package lists... Done
Building dependency tree
Reading state information... Done
bind9 is already the newest version.
dnsutils is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-server : Depends: linux-headers-server (= 3.2.0.45.54) but 3.2.0.48.58 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@nagios:~#


can someone tell me what to do ....

---

### Post by dino99 on 2013-07-02
why do you want to install something already installed ? (bind9 & dnsutils)  :confused:

install linux-headers-server

---

### Post by IvanMP on 2013-07-03
I have notes that, but what about the errors iv got, iv try installing other things and same ...

---

