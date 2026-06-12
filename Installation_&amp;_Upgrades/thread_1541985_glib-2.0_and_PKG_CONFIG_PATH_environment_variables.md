---
title: "glib-2.0 and PKG_CONFIG_PATH environment variables"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by j_zhill on 2010-07-29
Hi,

I'm trying to install the latest version of tracker - 0.8.15. When I run ./configure, I come up with an error like this:

```
checking for getline... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... configure: error: Package requirements (glib-2.0 >= 2.24.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB2_CFLAGS
and GLIB2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jez@jez-eee901:~/Desktop/tracker-0.8.15$ 

```

When I run sudo apt-get install glib-2.0, I get the "couldn't find package error". However, I can see that I have some packages installed that look relevant:

gir1.0-glib-2.0 version 0.6.8-1
libglib2.0-0 version 2.24.1-0ubuntu1

Surely the libglib2.0-0 package is some kind of replacement for glib-2.0? My understanding from the man page is that PKG_CONFIG_PATH is some way of linking to and checking requested packages... is this right? Can I change it to point at the libglib package instead?

Thanks.

---

### Post by anglican on 2010-07-30
> **j_zhill said:**
> Hi,

I'm trying to install the latest version of tracker - 0.8.15. When I run ./configure, I come up with an error like this:

```
checking for getline... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... configure: error: Package requirements (glib-2.0 >= 2.24.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB2_CFLAGS
and GLIB2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jez@jez-eee901:~/Desktop/tracker-0.8.15$ 

```When I run sudo apt-get install glib-2.0, I get the "couldn't find package error". However, I can see that I have some packages installed that look relevant:

gir1.0-glib-2.0 version 0.6.8-1
libglib2.0-0 version 2.24.1-0ubuntu1

Surely the libglib2.0-0 package is some kind of replacement for glib-2.0? My understanding from the man page is that PKG_CONFIG_PATH is some way of linking to and checking requested packages... is this right? Can I change it to point at the libglib package instead?

Thanks.
Try:
```
sudo apt-get install libglib2.0-dev
```H

---

