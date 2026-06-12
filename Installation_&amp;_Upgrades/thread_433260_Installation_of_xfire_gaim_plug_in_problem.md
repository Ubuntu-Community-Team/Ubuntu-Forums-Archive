---
title: "Installation of xfire gaim plug in problem"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by t3roriz3r on 2007-05-04
Hi can anyone help me, i was following the how to guide and have encountered a problem, this is my last bit of code ouput have the full thing saved but its pretty long: -

```
/bin/sed 's/#define PACKAGE/#define GFIRE_PACKAGE/g' pre_config.h > gfire_config.h
make  all-recursive
make[1]: Entering directory `/home/ian/Desktop/gaim-xfire-0.6.0'
Making all in src
make[2]: Entering directory `/home/ian/Desktop/gaim-xfire-0.6.0/src'
/bin/bash ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"      -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include                    -Wall -g3 -c gfire.c
gfire.c: In function 'gfire_login':
gfire.c:353: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
gfire.c:353: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
gfire.c:353: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: error: too few arguments to function 'gaim_proxy_connect'
gfire.c: At top level:
gfire.c:1498: warning: initialization from incompatible pointer type
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/ian/Desktop/gaim-xfire-0.6.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/Desktop/gaim-xfire-0.6.0'
make: *** [all-recursive-am] Error 2

```

Started up GAIM and can see nothing about xfire, anyone know whats going wrong? Is 0.6.0 plugin compatible with GAIM 2.0 beta?

Thanks

---

### Post by t3roriz3r on 2007-05-06
Anyone have any ideas?

Thanks

---

