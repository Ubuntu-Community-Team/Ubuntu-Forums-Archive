---
title: "ia32-libs Upgrade Error"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by chessforce on 2006-06-17
During my upgrade to Ubuntu Dapper Drake from Breezy Badger, I encountered the following error when apt was trying to upgrade ia32-libs:
```

Unpacking ia32-libs (from .../ia32-libs_1.4ubuntu19_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was wondering if anyone knew what to do in this case.

---

### Post by chessforce on 2006-06-18
I followed the directions at
[http://ubuntuforums.org/showpost.php?p=858658&postcount=10](http://ubuntuforums.org/showpost.php?p=858658&postcount=10)

replacing "libgl1-mesa" with "ia32-libs".  This allowed me to proceed with the upgrade to Dapper Drake.

---

