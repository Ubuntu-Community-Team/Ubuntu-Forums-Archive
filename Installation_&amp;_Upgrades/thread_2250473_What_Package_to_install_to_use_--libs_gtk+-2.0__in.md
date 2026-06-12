---
title: "What Package to install to use --libs gtk+-2.0  in c compile"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by keith14 on 2014-10-28
Hi,
  I'm trying to compile c program that uses gtk+-2.0 library. What do I need to do to add this package?
After several attempts of adding different packages I still get many undefined references:
gui_slide.c:(.text+0x157f): undefined reference to `gtk_widget_show'
gui_slide.c:(.text+0x1598): undefined reference to `gtk_label_new'
gui_slide.c:(.text+0x15a1): undefined reference to `gtk_table_get_type'
  ... ... .. and on-on.

The makefile call is:  gcc -c `pkg-config --cflags --libs gtk+-2.0` $< -o $@
thanks,
Keith

---

### Post by steeldriver on 2014-10-28
If pkg-config isn't throwing an error, then the package is likely already correctly installed. It's probably a matter of changing the gcc command line to make sure the libraries come AFTER the prerequisite $< e.g.

```

gcc $< `pkg-config --cflags --libs gtk+-2.0` -o $@

```
or you can split the CFLAGS and LIBS like
```

gcc `pkg-config --cflags gtk+-2.0` $< `pkg-config --libs gtk+-2.0` -o $@

```

(I'm guessing you don't want -c here since you are apparently linking to form an executable)

---

### Post by keith14 on 2014-10-28
Yes, TY

---

