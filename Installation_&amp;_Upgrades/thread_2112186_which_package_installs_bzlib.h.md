---
title: "which package installs bzlib.h?"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2013-02-04
Hi, all:
I'm using ubuntu 12.10. Just have no idea why bzlib.h is not installed?

---

### Post by schragge on 2013-02-04
It's in libbz2-dev.

```

$ apt-file search /bzlib.h
libbz2-dev: /usr/include/bzlib.h
...

```

---

### Post by jiapei100 on 2013-02-04
Thanks so much.



> **schragge said:**
> It's in libbz2-dev.

```

$ apt-file search /bzlib.h
libbz2-dev: /usr/include/bzlib.h
...

```

---

