---
title: "Efty Edge to Feisty Fawn upgrade problem"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by geoffatmk on 2007-05-05
I am using the upgrade button on my update manager and get this warning;

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

(Actually I get it twice) in the Error During Upgrade window.

When I open the page listed via Firefox I see the content of a binary file so it seems to be there.  Can anyone tell me what I can do to overcome this issue?

Thanks.

Geoff :confused:

---

### Post by zvacet on 2007-05-05
```
sudo aptitude update && sudo aptitude upgrade
```

---

