---
title: "can not upgrade to 10.10"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2011-02-24
I haven't used Ubuntu in a while and decided to upgrade Jaunty. So it went fine to 9.04, to 9.10, and now I am at 10.04 LTS. Now, when I run Update Manager it says the system is up-to-date, and Apt-get Upgrade shows 0 upgraded. What could be the issue?

---

### Post by Hippytaff on 2011-02-24
your probably up to date..everything is up to date...if your worried (which I wouldn't be) then post the output of ```
cat /etc/apt/sources.list
```

---

### Post by merlin666 on 2011-02-25
Thanks, I figured it out - need to change settings in Update Manager otherwise only new LTS are upgraded.

---

