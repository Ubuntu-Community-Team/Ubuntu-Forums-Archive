---
title: "[ubuntu][Solved]Can't install 'appindicator-0.1'"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by khan.orak on 2013-10-28
Hi,

I am new to Ubuntu. I want to install **indicator-multiload-0.1** so that I can view resource usage. When I try to run command **./configure**, it gives me an error:
```

..................................
..................................
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for MULTILOADDEPS... no
configure: error: Package requirements (gtk+-2.0 cairo appindicator-0.1 glib-2.0 gio-unix-2.0 gmodule-2.0 libgtop-2.0) were not met:

**No package 'appindicator-0.1' found**

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MULTILOADDEPS_CFLAGS
and MULTILOADDEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I have installed many missing packages, but I can't seem to make this **appindicator-0.1** to work.

I installed appindicator-0.1 by using the following command:

```
sudo apt-get install appindicator-0.1
```

It installed successfully. But when I retry to execute ./configure command, it gives the above mentioned error.

Any help?

---

### Post by oldos2er on 2013-10-28
Is there some particular reason you're compiling from source? indicator-multiload is in the repositories (at least on 13.10).

---

### Post by khan.orak on 2013-10-28
> **oldos2er said:**
> Is there some particular reason you're compiling from source? indicator-multiload is in the repositories (at least on 13.10).

Hey thanks for the reply.

That's so stupid of me, didn't even think about that.

Just entered 

```
sudo apt-get install indicator-multiload
```

and it installed.

Thank you for the heads-up!

cheers

---

