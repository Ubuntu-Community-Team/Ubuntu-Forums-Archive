---
title: "libxcb-xlib.so.0 missing under ubuntu 9.10"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by alard on 2010-01-15
Coud anyone tell how to install libxcb-xlib.so.0?


When I start one software and it complains that 

"error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory" 

I have lastest libxcb1 installed and searched in my system but didnot find a relevant result.

---

### Post by essgrocott on 2010-02-06
me too -

---

### Post by AlexCamps on 2010-03-22
me to!!!!!!!
help

---

### Post by kholis on 2010-12-21
you can copy it from hardy package [http://packages.ubuntu.com/hardy/i386/libxcb-xlib0/download](http://packages.ubuntu.com/hardy/i386/libxcb-xlib0/download).

- install it
- copy libxcb-xlib.so.0.0.0 to temp directory
- remove the package (or ubuntu will force you to remove it)
- copy back the lib to /usr/lib
- make symlink to libxcb-xlib.so.0

---

