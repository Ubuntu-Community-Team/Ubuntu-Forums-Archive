---
title: "libtool error on Gaim-vv install"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by richard0012sX on 2006-02-24
at the end of running the make command I get this:

lglib-2.0 -LNONE -lSM -lICE -lpthread -lnsl 
../libtool: line 1657: cd: NONE: No such file or directory 
libtool: link: cannot determine absolute directory name of `NONE' 
make[3]: *** [gaim-vv] Error 1 
make[3]: Leaving directory `/home/richard/gaim-vv-1.2.0/src' 
make[2]: *** [all-recursive] Error 1 
make[2]: Leaving directory `/home/richard/gaim-vv-1.2.0/src' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/home/richard/gaim-vv-1.2.0' 
make: *** [all] Error 2 

I figure I probably need to change something in the libtool file but I don't know what I should change anything to.

---

