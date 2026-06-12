---
title: "Missing liblzo1 and liblzo-dev packages"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-06-20
Hello,

I'm having the following issue when trying to cross-build [uClinux]("http://blackfin.uclinux.org/gf/project/uclinux-dist") on an x86 Ubuntu host running 10.04:

```

gcc -D_FILE_OFFSET_BITS=64 -O2 -g -Wall -Wextra -Wwrite-strings -Wno-sign-compare -c -o /usr/src/switchfin/build_ip01/uClinux-dist/user/mtd-utils/build-606f38a2221648ca5c5fa292c9f71d2ddd59fa66-host/mkfs.ubifs/lpt.o lpt.c -g -Wp,-MD,/usr/src/switchfin/build_ip01/uClinux-dist/user/mtd-utils/build-606f38a2221648ca5c5fa292c9f71d2ddd59fa66-host/mkfs.ubifs/.lpt.c.dep
In file included from lpt.c:23:
mkfs.ubifs.h:48:23: error: uuid/uuid.h: No such file or directory
make[5]: *** [/usr/src/switchfin/build_ip01/uClinux-dist/user/mtd-utils/build-606f38a2221648ca5c5fa292c9f71d2ddd59fa66-host/mkfs.ubifs/lpt.o] Error 1
make[5]: Leaving directory `/usr/src/switchfin/build_ip01/uClinux-dist/user/mtd-utils/606f38a2221648ca5c5fa292c9f71d2ddd59fa66/mkfs.ubifs'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/usr/src/switchfin/build_ip01/uClinux-dist/user/mtd-utils'
make[3]: *** [mtd-utils] Error 2

```

Although I have packages liblzo2-2 and liblzo2-dev installed, [this thread]("http://blackfin.uclinux.org/gf/project/uclinux-dist/tracker/?action=TrackerItemEdit&tracker_item_id=4164") seems to say that this could be caused by the absence of packages liblzo1 and liblzo-dev.

However, those packages don't seem available for 10.04:
```

# aptitude search lzo
liblzo2-2
liblzo2-dev
lzop

```

Is there a way to find and install liblzo and liblzo-dev, and see if this solves the error?

Thank you.

---

