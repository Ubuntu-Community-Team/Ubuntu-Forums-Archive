---
title: "Help: I can't get AWN to install!!! configure: error: Package requirements were not.."
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by alexmister on 2008-09-24
Hello, I am new to Linux, so please cut me some slack...

I'm trying to configure Avant Window Manager, but whenever I run ./configure, this shows:
[COLOR="black"][SIZE="3"][SIZE="3"][SIZE="3"]checking for GLIB - version >= 2.8.0... 

*** 'pkg-config --modversion glib-2.0' returned 2.9.6, but GLIB (2.18.0)

*** was found! If pkg-config was correct, then it is best

*** to remove the old version of GLib. You may also be able to fix the error

*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing

*** /etc/ld.so.conf. Make sure you have run ldconfig if that is

*** required on your system.

*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH

*** to point to the correct configuration files

no

checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:



No package 'gtk+-2.0' found

No package 'gdk-2.0' found

No package 'libwnck-1.0' found

No package 'gconf-2.0' found



Consider adjusting the PKG_CONFIG_PATH environment variable if you

installed software in a non-standard prefix.



Alternatively, you may set the environment variables AWN_CFLAGS

and AWN_LIBS to avoid the need to call pkg-config.

See the pkg-config man page for more details.[/SIZE][/SIZE][/SIZE][/COLOR]



I've looked a bunch of threads, and none of them help.  PLEASE HELP!!!

---

### Post by sneeks on 2008-09-24
what version of Ubuntu are you running

---

### Post by alexmister on 2008-09-24
Ubuntu 7.04 Feisty Fawn on PowerPC

---

### Post by alexmister on 2008-09-28
Why isn't anyone answering?

Is it because nobody knows?

---

