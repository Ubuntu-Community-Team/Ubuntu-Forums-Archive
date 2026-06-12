---
title: "problem installing Gcompris-9.1"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by helianthae on 2010-02-05
Hi,

just upgraded to Koala, but found it is still using version 8.4.12 of Gcompris, so have downloaded source files for 9.1. Eventually managed to configure it ok, but when trying [make] I get following error message:

[HTML]make[3]: Entering directory `/home/***/Desktop/gcompris-9.1/docs/C'
texi2html -monolithic gcompris.texi
/bin/bash: texi2html: command not found
make[3]: *** [gcompris.html] Error 127
make[3]: Leaving directory `/home/***/Desktop/gcompris-9.1/docs/C'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/***/Desktop/gcompris-9.1/docs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/***/Desktop/gcompris-9.1'
make: *** [all] Error 2 [/HTML]I have tried to [make install] anyway, but now get following error message:

[HTML]make[3]: Entering directory `/home/tanja/Desktop/gcompris-9.1/docs/eu'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/local/share/gnome/help/gcompris/eu
mkdir -p -- /usr/local/share/gnome/help/gcompris/eu
/usr/bin/install -c -m 644  gcompris.html /usr/local/share/gnome/help/gcompris/eu
/usr/bin/install: cannot stat `gcompris.html': No such file or directory
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/tanja/Desktop/gcompris-9.1/docs/eu'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/tanja/Desktop/gcompris-9.1/docs/eu'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tanja/Desktop/gcompris-9.1/docs'
make: *** [install-recursive] Error 1
tanja@Formaldehyde:~/Desktop/gcompris-9.1$ [/HTML]I would be very grateful for any tips to resolve this.

thanks
Helianthae

---

### Post by Statik on 2010-02-15
How did you manage to configure it? I tried both 9.1 and 9.2 and I keep getting:
```
checking for GCOMPRIS... configure: error: Package requirements (  gtk+-2.0 >= 2.12.0   gstreamer-0.10   librsvg-2.0 >= 2.26.0   libxml-2.0 >= 2.7.3) were not met:

No package 'librsvg-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GCOMPRIS_CFLAGS
and GCOMPRIS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I'd love to be able to install a more recent version.

Statik

---

