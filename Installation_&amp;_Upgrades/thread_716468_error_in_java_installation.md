---
title: "error in java installation"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by bryle on 2008-03-05
Hi! I'm installing java6 on ubuntu7 and I followed some of this procedure given in some of the forums.
  - chmod 755 filename.bin
  - sudo ./filename.bin
  - sudo update-alternatives java
  - java -version

I'm stuck in this error during my command: sudo update-alternatives java I got this error: unknown argument 'java'. What does this mean?

Any help on this, thanks in advance.

Regards,
Bryle

---

### Post by zvacet on 2008-03-06
I know it sounds trivial,but did you replace** filename.bin** with exact java file name?If you want to try other way to install Java here it is

1.system<admin<software sources>check all boxes under Ubuntu software and updates tab.Reload.In terminal

```
sudo apt-get install ubuntu-restricted-extras
```

---

