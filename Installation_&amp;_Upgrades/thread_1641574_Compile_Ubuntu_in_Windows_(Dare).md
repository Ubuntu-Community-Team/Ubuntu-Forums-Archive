---
title: "Compile Ubuntu in Windows (Dare)"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by jjmutumi on 2010-12-09
Hello. Simple brain teaser for you guyz. What happens if you compile Ubuntu in mingw or SFU etc. Do you get a win32 binary compartible Ubuntu?

---

### Post by amauk on 2010-12-09
Windows doesn't have any of the GNU toolchain, so Linux will simply will not compile under windows

You'd need to install a full POSIX environment on windows, including all the GNU utilities (Eg. a full Cygwin install) in order to compile the kernel

---

