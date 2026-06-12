---
title: "GUDEV missing during install of ModemManager"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by stefan_bahrens on 2016-09-23
I am running Ubuntu 16.04.1 64bit LTS. I'd like to use my mobile phone to connect to the internet so I am trying to install ModemManager-1.6.2

If I run ---
[INDENT]./configure --prefix=/usr   
--sysconfdir=/etc  
--localstatedir=/var  
--enable-more-warnings=no  
--with-suspend-resume=system  
--disable-static && make
[/INDENT]

then I receive this error message ----
[INDENT]checking for GUDEV... no
configure: error: Package requirements (gudev-1.0 >= 147) were not met:

No package 'gudev-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GUDEV_CFLAGS
and GUDEV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/INDENT]

I cannot find any way to install gudev-1.0. I don't know what it is. I don't know what these other 2 suggestions mean or how to execute them.

1) Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.

2) Alternatively, you may set the environment variables GUDEV_CFLAGS and GUDEV_LIBS to avoid the need to call pkg-config.

Any help with how to rectify this error regarding missing GUDEV would be
greatly appreciated.

---

### Post by stefan_bahrens on 2016-09-25
OK. I'd like to set the environment variables GUDEV_CFLAGS and GUDEV_LIBS to avoid the need to call pkg-config (as recommended above). Can someone advise me how to do this? Thanks in advance.

---

