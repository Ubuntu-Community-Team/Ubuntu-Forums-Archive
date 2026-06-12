---
title: "alsa-tools, gtk+2.18.6, cairo and pango"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by GlowBird on 2010-02-15
I installed Ubuntu 9.10 and wanted to build the alsa--tools (1.20) directory.  The ./configure said I needed gtk.  ./configure for gtk says I need cairo and pango.  The last ttime I tried to install cairo myself, I lost all my fonts and had to reinstall ubuntu.  I tried to find the Cairo packages on the Ubuntu website, but the ones I have installed have not made the gtk ./configure happy.  Where can I find a version of Cairo that will work with Ubuntu 9.10 and meet the requirements for gtk?

thanks




ERROR output:

checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.21.3    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

