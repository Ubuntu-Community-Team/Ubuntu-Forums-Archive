---
title: "Upgrading from 5.10 (can't find breez-updates)"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by search66 on 2006-10-16
Good morning!  I'm trying to update to Dapper, and I don't have the repository 'breezy-updates' to upgrade...

Any clues on how I can get that repository and upgrade to Dapper?

---

### Post by taurus on 2006-10-16
You need to edit /etc/apt/sources.list and replace the word breezy with the word dapper.  Then, upgrade it...

```

gksudo gedit /etc/apt/sources.list <-- to edit /etc/apt/sources.list
(save it and now run)
sudo aptitude update
sudo aptitude dist-upgrade

```

---

### Post by search66 on 2006-10-16
Thank you!

Wish me luck!!!!

---

### Post by taurus on 2006-10-16
Comment out that line by placing a # in front of it in your /etc/apt/sources.list...  Run run those three commands again.

p.s.  You can do it.  :mrgreen:

---

