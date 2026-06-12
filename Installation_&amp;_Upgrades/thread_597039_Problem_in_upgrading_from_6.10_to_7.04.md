---
title: "Problem in upgrading from 6.10 to 7.04"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by mcastel on 2007-10-30
Hello,

I have a problem that occour during my attempt of upgrading a 6.10 ubuntu installation in a 7.04: namely, just after the new repository has been enabled, the procedure stops and return this error message:


```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2  bzip2 has reported a code error (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 I bzip2 has reported a code error (2)"
```

After that, the system rollback to my previous installation. Could anyone give me a suggestion to solve the problem?

Thanks in advance ;)

---

### Post by ThrobbingBrain66 on 2007-10-30
Go to System > Administration > Software Sources and change the 'Download from' box to a different server and try your upgrade again.

---

