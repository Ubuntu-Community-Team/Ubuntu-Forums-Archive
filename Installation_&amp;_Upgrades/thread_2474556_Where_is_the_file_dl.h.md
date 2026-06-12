---
title: "Where is the file dl.h ?"
date: 2022-05-02
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2022-05-02
I'm using Ubuntu 22.04
My ENV is:

```

&#10140;  ~ uname -r
5.15.0-27-generic
&#10140;  ~ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy
&#10140;  ~ gcc --version
gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```


Is there a file **dl.h** in the system? Which package contains **dl.h** ?
```

Has header "dl.h" : NO 

```

Thank you ...

---

### Post by ubfan1 on 2022-05-03
Take your pick:
apt-file search /dl.h 
libcoin-dev: /usr/include/Inventor/C/glue/dl.h
libfuntools-dev: /usr/include/funtools/dl.h
libnacore-dev: /usr/include/NASPRO/core-5/NASPRO/core/dl.h
libopenmpi-dev: /usr/lib/x86_64-linux-gnu/fortran/gfortran-mod-15/openmpi/openmpi/opal/mca/dl/dl.h
libopenmpi-dev: /usr/lib/x86_64-linux-gnu/openmpi/include/openmpi/opal/mca/dl/dl.h
libtensorpipe-dev: /usr/include/tensorpipe/common/dl.h
libxmlsec1-dev: /usr/include/xmlsec1/xmlsec/dl.h
php8.1-dev: /usr/include/php/20210902/ext/standard/dl.h

---

