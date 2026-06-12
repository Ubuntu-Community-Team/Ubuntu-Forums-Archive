---
title: "eclipse &amp; ant1.8"
date: 2014-05-19
forum: Installation &amp; Upgrades
---

### Post by quigi on 2014-05-19
The thread [http://ubuntuforums.org/showthread.php?t=1473194](http://ubuntuforums.org/showthread.php?t=1473194) is closed, but the problem persists:

Android development requires eclipse and ant1.8.

If you install eclipse in Ubuntu 10.4 and then ant1.8, the second 'apt-get install' **removes** eclipse.

If you install ant1.8 first and then eclipse, the latter **fails** with this message:
```
The following packages have unmet dependencies:
  eclipse: Depends: eclipse-jdt but it is not going to be installed
           Depends: eclipse-pde but it is not going to be installed
E: Broken packages
```

Has there been any progress?

---

