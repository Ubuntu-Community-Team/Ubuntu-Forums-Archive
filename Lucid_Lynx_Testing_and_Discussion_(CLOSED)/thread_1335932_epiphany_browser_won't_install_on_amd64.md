---
title: "epiphany browser won't install on amd64"
date: 2009-11-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ronacc on 2009-11-24
When I try to install epiphany it has missing dependencies , or more correctly it has dependencies that have missing dependencies .

---

### Post by SevenMachines on 2009-11-24
gobject-introspection packages are being migrated to a new set of package names (gir1-*). so there might be a number of problematic dependencies while everything is updated. 
if you need epiphany-browser just now while dependent packages are updated, you can install the previous version of [libseed0 (2.28.0-1)]("http://ftp.acc.umu.se/ubuntu/pool/universe/s/seed/"), the current one, 2.28.0-2, is the unsatisfiable dependency package here, then epiphany will be installable.

---

### Post by ronacc on 2009-11-24
Thanks for the reply , Yes its gir1-curl that is plugging up the works here . I use Opera as my main browser  so no problem I just found it amusing that epiphany is the gnome browser and its the one that won't install .

---

### Post by Camilia on 2010-02-03
Did you get epiphany to work?  I want to use it. I downloaded but it is no where to be found.

---

### Post by ronacc on 2010-02-03
yes epiphany has been working fine , when you say you downloaded it do you mean installed it , if you installed it from the repos , it should show up in application>internet .

---

