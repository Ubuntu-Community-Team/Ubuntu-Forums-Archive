---
title: "Problem with Apollon plugin"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by mateamargo on 2006-10-22
Well, I have installed Apollon from the repositories, and came with Gnutella and OpenFT plugin (both are working fine).
But I want to add giFT-ares support, so I have downloaded the plugin from this page:
[http://gift-ares.berlios.de/](http://gift-ares.berlios.de/)

The problem it's while I'm try to compile it, because trhows me this error when I run the **make** command (after **./configure**):
```

make  all-recursive
make[1]: Entering directory `/home/mateamargo/Downloads/gift-ares-0.3.0'
Making all in lib
make[2]: Entering directory `/home/mateamargo/Downloads/gift-ares-0.3.0/lib'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I/usr/include -Wall -g -O2 -MT as_hashtable.lo -MD -MP -MF ".deps/as_hashtable.Tpo" \
          -c -o as_hashtable.lo `test -f 'as_hashtable.c' || echo './'`as_hashtable.c; \
        then mv -f ".deps/as_hashtable.Tpo" ".deps/as_hashtable.Plo"; \
        else rm -f ".deps/as_hashtable.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I/usr/include -Wall -g -O2 -MT as_hashtable.lo -MD -MP -MF .deps/as_hashtable.Tpo -c as_hashtable.c  -fPIC -DPIC -o .libs/as_hashtable.o
In file included from as_hashtable.c:32:
as_ares.h:57:36: error: libgift/proto/protocol.h: No such file or directory
as_ares.h:58:33: error: libgift/proto/share.h: No such file or directory
as_ares.h:61:40: error: libgift/proto/if_event_api.h: No such file or directory
In file included from as_hashtable.c:32:
as_ares.h:182: error: syntax error before '*' token
as_ares.h:182: warning: type defaults to 'int' in declaration of 'gift_proto'
as_ares.h:182: warning: data definition has no type or storage class
as_hashtable.c: In function 'as_hashtable_insert_str':
as_hashtable.c:492: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
as_hashtable.c: In function 'as_hashtable_remove_str':
as_hashtable.c:533: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
as_hashtable.c: In function 'as_hashtable_lookup_str':
as_hashtable.c:570: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
make[2]: *** [as_hashtable.lo] Error 1
make[2]: Leaving directory `/home/mateamargo/Downloads/gift-ares-0.3.0/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mateamargo/Downloads/gift-ares-0.3.0'
make: *** [all] Error 2

```

Any help, may be any repository when I could find this to install it with Synaptic?

---

### Post by dguerre on 2007-09-30
hello,

I'm sorry to revive this old thread, but I'm having the same problem. Does anyone know how to solve it?

Did the OP solve the problem?

Thanks,

DAGA

---

### Post by ironfistchamp on 2007-12-15
Bit of a necrobump but I have the same issue here. Anyone know why, or got an giftAres deb?

Thanks

Ironfistchamp

---

### Post by 3d0 on 2008-01-23
Sorry for the necroposting, but i've found the solution: install **libgift-dev** and **libgiftproto-dev**


```

sudo aptitude install libgiftproto-dev  libgift-dev

```

Now you'll be able to compile and use the plugin...

---

### Post by dguerre on 2008-01-23
It does work for me, installing  libgift-dev is probably not needed because it was already installed in my system.

Thanks to 3d0

---

