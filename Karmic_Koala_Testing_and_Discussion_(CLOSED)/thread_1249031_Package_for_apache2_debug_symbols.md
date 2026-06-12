---
title: "Package for apache2 debug symbols"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-08-24
Does anyone know of Karmic will include packages for the debug symbols for packages such as **apache2-mpm-worker** and **apache2-mpm-prefork** ?

I'd like to have them available to debug a hanging apache2 server, and I'd like to avoid having to build the server myself just to get debug symbols.

---

### Post by Starks on 2009-08-24
Just install the dbg repo or install the packages manually.

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse

[http://ddebs.ubuntu.com/pool/main/a/apache2/](http://ddebs.ubuntu.com/pool/main/a/apache2/)

---

### Post by christian.convey on 2009-08-24
Thank you!!! I didn't know about ddebs!!!

---

