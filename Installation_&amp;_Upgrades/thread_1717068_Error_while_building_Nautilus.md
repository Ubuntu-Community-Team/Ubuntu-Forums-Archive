---
title: "Error while building Nautilus"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by saphyn on 2011-03-29
I'm somewhat new at building, so I'm hoping this is an easy explanation. 

Downloaded Nautilus source to patch for transparent background. 

Patching went well and fine. 

During building I received this: 

```

Making all in libnautilus-private
make[2]: Entering directory `/home/[x]/nautilus-2.32.0/libnautilus-private'
  GEN    nautilus-marshal.h
  GEN    nautilus-marshal-guts.c
  CC     nautilus-autorun.lo
gcc: @APP_INDICATOR_CFLAGS@: No such file or directory
make[2]: *** [nautilus-autorun.lo] Error 1
make[2]: Leaving directory `/home/[x]/nautilus-2.32.0/libnautilus-private'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/[x]/nautilus-2.32.0'
make: *** [all] Error 2

```Thanks in advance. :)

---

### Post by Brucevdk on 2011-06-19
Please see [my answer on Ask Ubuntu](http://askubuntu.com/questions/32543/app-indicator-cflags-no-such-file-or-directory/49491).

---

