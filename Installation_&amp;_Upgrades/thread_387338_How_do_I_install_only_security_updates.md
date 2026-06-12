---
title: "How do I install only security updates?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by tictacman on 2007-03-18
I'm quite happy with the package versions at the moment, and I don't want to install everything that adept updater says is upgradable, but I would like to download packages that need to be updated because they have been found to have vulnerabilities.  How can I update these packages only without having to sift through all upgradable packages in adept updater?

---

### Post by yabbadabbadont on 2007-03-18
Either edit /etc/apt/sources.list and comment out all the lines that don't say "security.ubuntu.com" or disable them using the preferences in Synaptic.

Edit: You need to leave the entries for "main" in there too, or you won't be able to install any new software.  :oops:

---

### Post by yabbadabbadont on 2007-03-18
Since a picture is worth a thousand words, here is an example sources.list for edgy:
```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

```

Notice how the updates and backports repositories have been commented out.

---

### Post by tictacman on 2007-03-18
Thanks for that, its definately a solution.  I also wondering if there was a terminal command that would do the same, something like apt-get upgrade security?

---

