---
title: "gcc-4.4-base and libgcc1 dependency problem despite karmic update"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by jml59 on 2010-02-09
Hello, 

I am trying to install the gcc package using Ubuntu 9.10, but fail to do so because of an dependency error, which seems to go in a circle. gcc-4.4-base needs libgcc1 before installation, and vice versa. Downloading the recently updated karmic packages did not help. Any suggestions?

Thank you

---

### Post by unmole on 2010-02-09
An ugly hack:
-Download all the dependency .debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
-Put them all in a folder and cd into it.
-Do a
```
sudo dpkg -i ./*
```

---

