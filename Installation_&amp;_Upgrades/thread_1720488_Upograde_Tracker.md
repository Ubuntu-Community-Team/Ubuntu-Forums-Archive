---
title: "Upograde Tracker"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by amacus on 2011-04-03
Hello all,

I am a big fan of the tracker software. However, the latest version installed on my computer is 0.6.95. I went on the website ([http://projects.gnome.org/tracker/](http://projects.gnome.org/tracker/)) and the latest stable version appears to be 0.10.6

I downloaded the tracker-0.10.6 tar, and ran 

```
/configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

However, it fails with 


```
configure: error: Package requirements (glib-2.0 >= 2.26.0) were not met:

Requested 'glib-2.0 >= 2.26.0' but version of GLib is 2.24.1
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GVDB_CFLAGS
and GVDB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

I'm guessing I need to upgrade glib to install it? But I have no idea how. Any ideas? I'm running 64 bit ubuntu 10.04 lts

---

