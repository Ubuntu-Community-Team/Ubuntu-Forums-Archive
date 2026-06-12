---
title: "Update-Manager unexpectedly crashes"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by ch1n4sailor on 2014-06-12
Ubuntu 14.04

Update-Manager unexpectedly crashes

Prompts for "Unauthenticated Sources OK?"

Then as soon you hit "OK" it dies... As of today, all of my PC's running 14.04, the Update-Manager (Software-Updater)
will crash on the exact same spot.

Any Ideas..?

Was working fine, just until 2 days ago, what-ever update, from 2 days, now causes update-manager to crash.

Thank You!

---

### Post by mörgæs on 2014-06-12
What happens if you reboot and run
```
sudo apt-get update
sudo apt-get dist-upgrade
```
?

---

### Post by ch1n4sailor on 2014-06-13
> **mörgæs said:**
> What happens if you reboot and run
```
sudo apt-get update
sudo apt-get dist-upgrade
```
?


That did it, Thank You!

---

### Post by mörgæs on 2014-06-13
Good, please mark the thread 'solved'.

---

