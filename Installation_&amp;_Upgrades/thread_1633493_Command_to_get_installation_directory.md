---
title: "Command to get installation directory?"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Davste on 2010-11-29
Hello, does a command exist that will return the installation directory of an installed program? thanks :)

---

### Post by oldos2er on 2010-11-29
**which** <program name> searches your PATH.

**whereis** <program name> is similar, but also tells you where the source, binary, and man pages are.

---

### Post by sisco311 on 2010-11-29
And
```
dpkg -L package-name
```
lists all files installed to your system from *package-name*.

---

### Post by Davste on 2010-11-29
Thanks!

---

