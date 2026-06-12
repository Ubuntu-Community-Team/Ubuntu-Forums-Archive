---
title: "Google Earth 5.0 Cracks at start"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2009-03-29
Anybody else is having this problem?
I'm uysing an intel IGM and I can't open Google Earth. 

```
./googleearth
Warning: Unable to create prefs directory '/home/lorenzo/.googleearth'. Il file esiste.
get fences failed: -1
param: 6, val: 0
./googleearth-bin: relocation error: /lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

Can't really understand this output. Any help?
Thank you

---

### Post by plun on 2009-03-29
This bug is discussed within this thread

[http://ubuntuforums.org/showthread.php?t=1059167](http://ubuntuforums.org/showthread.php?t=1059167)

Post No 8 works.


The Medibuntu version is fixed...

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

EDIT,  Medibuntu version

Setting up googleearth-data (**5.0.11337.1968-0medibuntu6**) ...

---

### Post by Kosimo on 2009-03-29
> **plun said:**
> This bug is discussed within this thread

[http://ubuntuforums.org/showthread.php?t=1059167](http://ubuntuforums.org/showthread.php?t=1059167)

Post No 8 works.


The Medibuntu version is fixed...

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

EDIT,  Medibuntu version

Setting up googleearth-data (**5.0.11337.1968-0medibuntu6**) ...



FIxed using MEDIBUNTU version.

Thank you soo much! ;)

---

### Post by | MM | on 2009-03-29
I just used googleearth-package and that works as well.

---

### Post by ubulette on 2009-03-29
```

$ apt-cache madison googleearth-package
googleearth-package | 0.5.4.1~0ubuntu1 | http://archive.ubuntu.com jaunty/multiverse Packages
googleearth-package | 0.5.4.1~0ubuntu1 | http://archive.ubuntu.com jaunty/multiverse Sources

```

This version should work. I fixed the bug mentioned above when I updated this package to support googleearth 5.

---

