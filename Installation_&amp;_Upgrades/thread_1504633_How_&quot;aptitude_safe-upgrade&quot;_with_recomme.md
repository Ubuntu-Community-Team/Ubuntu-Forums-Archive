---
title: "How &quot;aptitude safe-upgrade&quot; with recommends?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by simonbcn on 2010-06-08
Today I have done an upgrade:
```
sudo aptitude safe-upgrade
```

And this is the warning showed by aptitude:
```
The following packages are RECOMMENDED but will NOT be installed: 
....
```

I have this in */etc/apt/apt.conf*:
```
Apt::Install-Recommends "true";
```

It seems that this line only affects a new installs.

Can I do an upgrade with recommends?

---

