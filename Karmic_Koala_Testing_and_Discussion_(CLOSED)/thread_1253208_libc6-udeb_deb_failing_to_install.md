---
title: "libc6-udeb deb failing to install"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-08-29
So I need libc6-udeb for a program I am trying to install... I downloaded it from [here](http://packages.ubuntu.com/karmic/libc6-udeb), however when I try to install the .deb file it fails with the following error message: ```
dpkg: error processing /home/jeff/Data/Downloads/libc6_udeb_2.10.1-0ubuntu8_amd64.udeb (--install):
  trying to overwrite '/lib/ld-2.10.1.so', which is also in package libc6
dkpg-deb: subprocess paste killed by signal (Broken Pipe)
```

Any idea what I can do to fix this? I really want to get this other package installed libc6-udeb is a dependency for.

~Jeff

---

### Post by xebian on 2009-08-29
> **beastrace91 said:**
> So I need libc6-udeb for a program I am trying to install... I downloaded it from [here](http://packages.ubuntu.com/karmic/libc6-udeb), however when I try to install the .deb file it fails with the following error message: ```
dpkg: error processing /home/jeff/Data/Downloads/libc6_udeb_2.10.1-0ubuntu8_amd64.udeb (--install):
  trying to overwrite '/lib/ld-2.10.1.so', which is also in package libc6
dkpg-deb: subprocess paste killed by signal (Broken Pipe)
```

Any idea what I can do to fix this? I really want to get this other package installed libc6-udeb is a dependency for.

~Jeff

Just pass --force-overwrite to dpkg

---

