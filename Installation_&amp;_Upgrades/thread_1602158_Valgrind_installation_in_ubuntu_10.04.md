---
title: "Valgrind installation in ubuntu 10.04"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by anup.techonly on 2010-10-21
Hi All,

I was trying to install valgrind on Ubuntu 10.04 but failed because of a dependency error.

If I try to install using synaptic or from terminal, it shows 
```
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6-dbg 2.11.1-0ubuntu7.2
```

If I download valgrind from its website, when I try to configure it, it stops at version error

```

checking the GLIBC_VERSION version... unsupported version
configure: error: Valgrind requires glibc version 2.2 - 2.10

```

Please help..

---

### Post by gmargo on 2010-10-21
You are out of date; the current version of libc6-dbg for Lucid is 2.11.1-0ubuntu7.4.  You need to do an "aptitude update" or update the sources through apt-get or a gui like syntaptic, and then upgrade.

I had no problem installing valgrind from the repository on both 32-bit Lucid and 64-bit Maverick.

---

### Post by anup.techonly on 2010-10-25
Thanks, the issue is solved...

---

