---
title: "dpkg --configure -a gives parse error"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by aktiv on 2010-09-03
Hi

I killed a stalled apt-get safe-upgrade, which left lock-files on my system. I followed this guide to clean it up:

[http://ubuntuforums.org/showthread.php?t=631128&highlight=lock](http://ubuntuforums.org/showthread.php?t=631128&highlight=lock)

and have done the following:
sudo rm /var/lib/dpkg/lock
sudo rm -r /tmp/*

now, when I try:
sudo dpkg --configure -a
i get:
dpkg: parse error, in file '/var/lib/dpkg/updates/0006' near line 0:
 newline in field name `#padding'

the file var/lib/dpkg/updates/0006 contains nothing but lines of '#padding'

how can I fix this?

System: Freshly installed 10.04 64bit, 2.6.32-21-generic

- aktiv

---

### Post by davidmohammed on 2010-09-03
try

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by aktiv on 2010-09-03
.. still getting the same error

---

