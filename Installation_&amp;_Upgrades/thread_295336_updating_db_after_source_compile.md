---
title: "updating db after source compile"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by pstep9407 on 2006-11-07
I wanted R 2.4, and so downloaded the source code and compiled it on dapper. Works great. The problem is that apt-get or aptitude does not know, apparently, that I have R 2.4 on my system. How do I make it known to apt?

---

### Post by tvst on 2006-11-08
I'm not sure, but maybe you'll need to make a package from the source and install it from there. Look at the dpkg man page.

---

