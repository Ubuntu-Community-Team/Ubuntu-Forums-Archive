---
title: "Ubuntu 10.04: problem after 116Mb update"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by hansmex on 2010-10-21
Hello,

Yesterday Ubuntu 10.04 did a big update: 116 Mb.

The system deleted this directory */usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/javaws*, so programs that want to start with a script referring to that directory don't start, but give an error message.

I was able to sort the first problem by manually editing the script and have it point to the right address (I changed the *java-6-sun-1.6.0.20* part into *java-6-sun-1.6.0.22*).

Still, I don't like this kind of updating!!


Hans

---

