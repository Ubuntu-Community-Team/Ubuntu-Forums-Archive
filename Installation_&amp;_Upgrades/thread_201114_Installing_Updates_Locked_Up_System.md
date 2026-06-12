---
title: "Installing Updates Locked Up System"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by solomke on 2006-06-21
:confused:  Help!  I logged on to my ubuntu and got the notice that updates were available.  In the middle of installing, it locked up.  I rebooted my machine and got to the logon screen.  After entering my ID and password I get a blank desktop with cursor, it stays there, like it froze, any solutions or fixes for this?????

---

### Post by givré on 2006-06-21
go in recovery mode and upgrade there:
```
sudo apt-get update
sudo apt-get upgrade
```
restart and that should be ok

---

### Post by pjs_flyer on 2006-06-21
sudo apt-get upgrade or sudo apt-get dist-upgrade?

---

### Post by givré on 2006-06-21
dist-upgrade is for upgrading distribution (fom breey to dapper for exemple)
and upgrade is just to upgrade your sustem.

---

