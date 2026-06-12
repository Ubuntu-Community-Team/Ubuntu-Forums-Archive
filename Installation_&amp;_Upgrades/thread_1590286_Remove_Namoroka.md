---
title: "Remove Namoroka"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Obould on 2010-10-07
Hello,

how can I remove Namoroka (3.6.12pre) and reinstall firefox? I already tried the sudo apt-get purge firefox-3.6 but to no avail.
Can anybody tell me what the ppa packages just are? Is it correct that they are Ubuntu specific packages for optimizing applications for Ubuntu?

Best regards,
Obould

---

### Post by lovinglinux on 2010-10-07
Go to Software Sources and disable the entry which contains **ubuntu-mozilla-daily**, then run these commands:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```

For optimizing Firefox see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

---

