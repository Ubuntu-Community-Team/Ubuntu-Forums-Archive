---
title: "Postgres install error"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by luftadler on 2009-12-13
Hi,

I try to install PostGis and when i configure it gives me an error 

> configure: error: could not find pg_config within the current path. You may need to try re-running configure with a --with-pgconfig parameter.
and this is the error when i give the make command

> make -C liblwgeom 
make[1]: Entering directory `/home/vasile/postgis-1.4.0/liblwgeom'
gcc -g -O2  -fno-common -DPIC  -Wall -Wmissing-prototypes  -c -o measures.o measures.c
In file included from measures.c:16:
liblwgeom.h:18:31: error: ../postgis_config.h: No such file or directory
make[1]: *** [measures.o] Error 1
make[1]: Leaving directory `/home/vasile/postgis-1.4.0/liblwgeom'
make: *** [liblwgeom] Error 2
Any ideas?

---

