---
title: "apt-get sources not available"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by ictguy on 2007-07-06
G'day,
I'm running kubuntu 5.10 and just recently when I do a "sudo apt-get update" I get a whole lot of errors with repositories not being available - any suggestions? I get these errors below among I whole lot of other similar errors.
```
Ign http://security.ubuntu.com breezy-security/main Packages
Err http://security.ubuntu.com breezy-security/main Packages   404 Not Found
Ign http://au.archive.ubuntu.com breezy Release
Err http://au.archive.ubuntu.com breezy/main Packages 404 Not Found
```
I have spent some time looking for the answers here but with no luck. TIA.
Any help would be appreciated.

---

### Post by lisati on 2007-07-06
You might want to try another mirror by using "Software sources" from the System->administration menu.

---

### Post by lisati on 2007-07-06
> **lisati said:**
> You might want to try another mirror by using "Software sources" from the System->administration menu.

p.s. the server that is geographically closest isn't always the best, speed wise. There is an option to "choose best server"

---

### Post by ictguy on 2007-07-06
Thanks for the relpy,
I'm updating via ssh'ing to the machine and then running sudo apt-get update. I'll just edit my /etc/apt/sources.list manually.

---

