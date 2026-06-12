---
title: "Problem while installing source file : No package 'gtkglext-1.0' found"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by Sahos on 2012-09-16
Hello,

I am running on Ubuntu 12.04 and am I trying to install a program from source using :

```

./configure
make
sudo make install

```

But I have an error after typing ./configure :

```

configure: error: Package requirements ("gtkglext-1.0") were not met:

No package 'gtkglext-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTKGLEXT_CFLAGS
and GTKGLEXT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I removed and reinstall gtkglext but it does not work.

I don't know what to do. Can you help ?

Thanks in advance,
Sahos

---

### Post by Sahos on 2012-09-16
Ok I got it alone. I needed it download one more package called libgtkglextmm-x11-1.2-dev which is different from libgtkglext1 that I had already installed !!

Curious but solved.

---

### Post by Fallon9111 on 2012-09-25
> **Sahos said:**
> Ok I got it alone. I needed it download one more package called libgtkglextmm-x11-1.2-dev which is different from libgtkglext1 that I had already installed !!

Curious but solved.



Thanks, it worked  \\:D/

---

