---
title: "axfr installation"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by binary_goofy on 2010-02-18
Hi,

I'm trying to install axfr on my ubuntu 9.10 box from:
[http://packetstormsecurity.nl/groups/ADM/axfr-0.5.2.tar.gz](http://packetstormsecurity.nl/groups/ADM/axfr-0.5.2.tar.gz)

But when i make install am getting the following errors:
-----------------------------------------------------
Making install in zlib-1.1.2
make[1]: Entering directory `/home/<replaced>/<replace>/axfr/axfr-0.5.2/zlib-1.1.2'
make[1]: Leaving directory `/home/<replaced>/<replace>/axfr/axfr-0.5.2/zlib-1.1.2'
gcc -DHAVE_CONFIG_H -I. -I. -I.   -g -O2 -c getaxfr.c
getaxfr.c: In function ‘getaxfrbydomain’:
getaxfr.c:149: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
getaxfr.c: In function ‘axfr’:
getaxfr.c:566: warning: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
getaxfr.c:583: warning: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
getaxfr.c: In function ‘srvy_p_rr’:
getaxfr.c:855: error: ‘MAX_KEY_BASE64’ undeclared (first use in this function)
getaxfr.c:855: error: (Each undeclared identifier is reported only once
getaxfr.c:855: error: for each function it appears in.)
getaxfr.c:1150: error: ‘T_UINFO’ undeclared (first use in this function)
getaxfr.c:1156: error: ‘T_UID’ undeclared (first use in this function)
getaxfr.c:1157: error: ‘T_GID’ undeclared (first use in this function)
make: *** [getaxfr.o] Error 1
-------------------------------------------------------------

It might just be a missing library, but i dont know which one. Tried googling, but hasn't been too helpful. Any direction will be appreciated. Thanks :)

---

