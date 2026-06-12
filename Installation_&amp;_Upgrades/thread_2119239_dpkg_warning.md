---
title: "dpkg warning"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2013-02-23
Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)

current dpkg
dpkg (1.16.1.2ubuntu7.1) 

receieved above while upgrading jdk. Though this time it did not hang.


[http://ubuntuforums.org/showthread.php?t=2117161]("http://ubuntuforums.org/showthread.php?t=2117161")

---

### Post by schragge on 2013-02-23
See LP bug #[lpbug]1024650[/lpbug].
When you run
```
dpkg-query -W openjdk-6\*
``` it should show you the package name with an architecture qualifier (like *openjdk-6-jdk:amd64*).

---

### Post by pjmlmas on 2013-02-23
openjdk-6-jre	6b27-1.12.3-0ubuntu1~12.04
openjdk-6-jre-headless	6b27-1.12.3-0ubuntu1~12.04
openjdk-6-jre-lib	6b27-1.12.3-0ubuntu1~12.04

---

