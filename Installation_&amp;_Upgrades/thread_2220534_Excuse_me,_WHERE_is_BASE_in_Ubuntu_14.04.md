---
title: "Excuse me, WHERE is BASE in Ubuntu 14.04?"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by dreamquartz on 2014-04-28
Just updated,  But no BASE in LO? I had to install the LO version from LibreOffice.org to get BASE.  This does not make any sense.  Does anyone have this problem as well? LO is integrated, would like to use the Ubuntu version, because of auto updates.  Dream

---

### Post by slickymaster on 2014-04-28
According to [14.04 manifest]("http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.manifest"), Base is not installed by default. To install it you'll have to```
sudo apt-get install libreoffice-base
```

---

