---
title: "upgrade dapper to edgy"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by TDFlanders on 2007-09-10
Hi,

when I do the update-manager -c

I still don`t get the upgrade available button

Anyone got a clue?

Thanx


root@thomasdelbeke:/home/thomasdelbeke# apt-get update-manager
E: Ongeldige operatie update-manager
root@thomasdelbeke:/home/thomasdelbeke# apt-get upgrade
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
root@thomasdelbeke:/home/thomasdelbeke# apt-get upgrade check-distribution
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
root@thomasdelbeke:/home/thomasdelbeke# update-manager -c
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
root@thomasdelbeke:/home/thomasdelbeke#

---

### Post by linuxwizard on 2007-09-10
run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c" 


[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

