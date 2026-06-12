---
title: "C compiling errors..."
date: 2006-04-29
forum: Installation &amp; Upgrades
---

### Post by Elrohir on 2006-04-29
Last night I went for a new install on my PC... now I'm trying to install everything but I keep running with a C compiling error when I try to configure some source codes...

```
configure: error: C compiler cannot create executables
```

help?

I'll attach the config.log that is created...

---

### Post by Greg2 on 2006-04-29
Your config.log shows that /usr/bin/ld cannot find crt1.o, so make sure you have libc6-dev installed.

---

### Post by Elrohir on 2006-04-30
thanx... I just read that it also needs zlib-dev, and as a dependency libc6-dev... so now it is running...

---

