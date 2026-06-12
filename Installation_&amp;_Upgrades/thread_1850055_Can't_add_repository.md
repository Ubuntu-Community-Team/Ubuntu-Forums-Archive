---
title: "Can't add repository"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by saviouz on 2011-09-25
Hi, every time I try to add any repository from the terminal this message comes up and nothing else happens: ```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv BC9EE88A229B9C049A06D1FB464AD83D4631BBEA
gpg: requesting key 4631BBEA from hkp server keyserver.ubuntu.com
gpg: requesting key 4631BBEA from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

Any idea how to fix this?

---

### Post by oldos2er on 2011-09-25
How long has this problem been occurring for you? Keyserver timeouts happen occasionally for me too, sometimes as long as a day or two.

---

