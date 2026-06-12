---
title: "pain in the *** to install airsnort need help"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by killernat on 2008-07-16
ok istalling isint the problom but all the other programs it needs are 
gconvert.c:51:2: error: #error GNU libiconv not in use but included iconv.h is from libiconv
i installed libiconv already what do i do about this error

---

### Post by killernat on 2008-07-16
...

---

### Post by adamogardner on 2008-07-16
use a rolled up dollar bill

---

### Post by killernat on 2008-07-16
4 got to put the hole error msg
gconvert.c:51:2: error: #error GNU libiconv not in use but included iconv.h is from libiconv
make[4]: *** [gconvert.lo] Error 1
make[4]: Leaving directory `/home/j/glib-2.15.0/glib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/j/glib-2.15.0/glib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/j/glib-2.15.0/glib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/j/glib-2.15.0'
make: *** [all] Error 2

---

### Post by killernat on 2008-07-17
bump

---

### Post by killernat on 2008-07-17
bring
my 
post 
up

---

### Post by brundlfly on 2008-08-26
Whenever I get a compile error like that I look in synaptic package manager for a dev pkg called that, and install it if there is one. Seems to do the trick. I don't see a "libiconv-dev" in my synaptic, but I don't see "libiconv" specifically either so I don't know exactly what you're using.

---

