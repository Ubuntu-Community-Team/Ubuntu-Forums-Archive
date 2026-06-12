---
title: "need to install libdb2"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by umneydurak on 2007-07-17
Hello
I am trying to install some software but getting:  error while loading shared libraries: libdb.so.3: cannot open shared object file: No such file or directory
After searching around I discovered I need to install libdb2. I tried apt-get and synaptic, both didn't have it. I guess it became obsolete? Where can I get this package?

Thank You.

---

### Post by DirtDawg on 2007-07-18
Hi. Try installing libdb4.4 or libdb4.5 and try again. It may be that libdb2 is simply an older version of the same library. If you are trying to compile the program, you will also need the -dev packages of the same name. For example, libdb4.5-dev.

Let us know how it goes.

---

