---
title: "Cybergarage (clinkcc) not installing"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by satty8610 on 2010-02-26
Hi,
I am trying to install clinkcc .After doing configure and make:
```
./configure --prefix=/usr

make

```


Then on doing make install, the following error comes:
```
/usr/bin/install: will not overwrite just-created `/usr/include/cybergarage/upnp/media/server/object/SearchCriteriaList.h' with `cybergarage/upnp/media/server/object/SearchCriteriaList.h'
make[2]: *** [install-nobase_includeHEADERS] Error 1
make[2]: Leaving directory `/home/ssaxena/clinkcc/clinkcc/include'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/ssaxena/clinkcc/clinkcc/include'
make: *** [install-recursive] Error 1
root@a153-osb:~/clinkcc/clinkcc# 
```

---

### Post by satty8610 on 2010-02-26
Got it myself.
It seems a couple of files had been included twice in .../include/Makefile.am
Just removing those lines , did the trick.

---

