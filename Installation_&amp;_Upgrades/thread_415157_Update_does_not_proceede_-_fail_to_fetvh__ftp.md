---
title: "Update does not proceede - fail to fetvh  ftp"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Chris11 on 2007-04-20
The update from 6.10 to 7.04 does not proceed at the initial stage of retrieving information using the update manager. The update is interrupted by:

> Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Packages.gz) Imposible traer archivo, el servidor dijo 'Can't open /debian-marillat/dists/unstable/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]


Any ideas? thanks in advance, Chris

---

### Post by Chris11 on 2007-04-20
I solved the situation.

I had do deactivate the source and voila, it is updating now..

Thanks anyway. Chris

---

