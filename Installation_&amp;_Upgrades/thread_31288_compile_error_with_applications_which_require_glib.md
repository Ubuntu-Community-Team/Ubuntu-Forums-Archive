---
title: "compile error with applications which require glib"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by casualtie on 2005-05-02
I get this message when I try to compile a program which require Glib:
```
checking for pkg-config... /usr/bin/pkg-config
checking for         glib-2.0                    gthread-2.0                 gtk+-2.0                    libgnomeui-2.0         libnjb... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

configure: error: Library requirements (        glib-2.0                    gthread-2.0                 gtk+-2.0                    libgnomeui-2.0             libnjb) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

I've installed Glib an GTK 2.0 trough synaptic. And tried to do it manually too.
Could someone please be so kind to tell me what to do? :)

---

### Post by syltty on 2005-05-02
$ apt-file search libgnomeui-2.0.pc
libgnomeui-dev: usr/lib/pkgconfig/libgnomeui-2.0.pc

try if sudo apt-get install libgnomeui-dev helps

---

### Post by casualtie on 2005-05-02
Thank you. That helped :)

---

