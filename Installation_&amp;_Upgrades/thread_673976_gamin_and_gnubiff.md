---
title: "gamin and gnubiff"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by epo on 2008-01-21
Hi,

I'm trying to compile the program gnubiff. During creation of the makefile ```
sudo ./configuration
``` the following error appears:

```

[...]
checking whether make sets $(MAKE)... (cached) yes
checking for main in -lpopt... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for main in -lfam... no
checking for FAM... configure: error: Package requirements (gamin >= 0.1.0) were not met:

No package 'gamin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FAM_CFLAGS
and FAM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I installed gamin (version 0.1.7). Can anyone help me out what I should do?

BTW The reason that I do not use  the prepackaged version of gnubiff is that I want to test a new translation (mo-file).

Thanks!

---

