---
title: "Can't upgrade to 14.04"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by Tristan_Williams on 2014-04-19
I am running Xubuntu 13.10.

running the command 'sudo apt-get dist-upgrade' does nothing, even though Trusty has been released

What do I do?

---

### Post by deadflowr on 2014-04-19
Try
```
sudo do-release-upgrade
```

dist-upgrade uogrades the existing system and does nothing to upgrade to a new release.
Unless you change out the sources, which I wouldn't recommend with Ubuntu.

Far easier to just run the do-release-upgrade command and let it run as it suppose to.

Edit: You probably don't need sudo, but what the hey, right.

---

