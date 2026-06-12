---
title: "How to find applications installed on a specific day?"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by vgezer on 2013-03-17
Is there any command to list via apt-get or dpkg?


Thanks.

---

### Post by oldos2er on 2013-03-17
Package installation info is kept in the file /var/log/apt/history.log, you can load it into a text editor and search. I'm sure there must be a way to use apt-cache or dpkg-query or something to grep it, but I can't put my finger on it at the moment.

---

### Post by ajgreeny on 2013-03-17
```
grep -w install /var/log/dpkg.log.1 && grep -w install /var/log/dpkg.log
``` will show you everything that you have installed recently that is in those two logs.  Older activity is in the archived and numbered **dpkg.log.#.gz logs** which you would need to extract and then search with the same command, edited for the files' different numbered names.

---

### Post by vgezer on 2013-03-17
Great, thanks.

---

