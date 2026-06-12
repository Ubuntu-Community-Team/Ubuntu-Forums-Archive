---
title: "missing library files in postgis and postgres 8.2"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by pinan on 2007-05-31
Just tried to upgrade from postgres 8.1/postgis to postgres 8.2/postgis

The library files liblwgeom.so, liblwgeom.so.1 and liblgeom.so.1.1 seem to be missing.  Normaly I would expect to find them in /usr/lib/postresql/8.2/lib

I have checked with the latest version of postgis(1.21) running on another linux machine, these files are created as part of the build procedure.

Is this a bug ?

---

### Post by markdeblois on 2007-08-31
I had the same problem but installed a bunch of other packages via Synaptic Package Manager referring to the same postgres 8.2.4 version (mysql, server stuff) and then it worked! The files are now present as they were missing completely before.

---

