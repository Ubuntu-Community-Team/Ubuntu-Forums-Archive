---
title: "Firefox"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by SecurityCop on 2008-09-22
I'm running Ubuntu dapper and I need to update my firefox from version 1.5 because my email doesnt work properly. So I can't install firefox 2 because I cannot find the files for it, and I can't install firefox 3 because I have to rewrite the source code of gtk+, and whenever I make it to 
```
./configure --prefix=/opt/gtk210
```
from [these instructions]("http://www.captain.at/howto-run-firefox-3-debian-etch.php") this code always comes up.
```
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:
Requested 'glib-2.0 >= 2.12.0' but version of GLib is 2.10.3
Requested 'cairo >= 1.2.0' but version of cairo is 1.0.4

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

``` and I have no idea how to change the enviornment variable. Can someone explain in rediculously simple steps on how to install either version of firefox?

---

