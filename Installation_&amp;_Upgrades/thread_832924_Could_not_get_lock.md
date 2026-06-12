---
title: "Could not get lock"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by rwizibuntu on 2008-06-18
I am trying to install a new package but keep on getting the message below 
I have tried to such but do not seem to get the search terms right 
does  anyone know a link to a thread with this problem solved

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Thanks and rgds to all

---

### Post by PmDematagoda on 2008-06-18
Are you running another package process? If so then close it and try again, if not then do:-
```
sudo rm /var/cache/apt/archives/lock
```
and see if that fixes it.

---

### Post by rwizibuntu on 2008-06-19
> **PmDematagoda said:**
> Are you running another package process? If so then close it and try again, if not then do:-
```
sudo rm /var/cache/apt/archives/lock
```
and see if that fixes it.

Thanks I rebooted and was able to install

---

