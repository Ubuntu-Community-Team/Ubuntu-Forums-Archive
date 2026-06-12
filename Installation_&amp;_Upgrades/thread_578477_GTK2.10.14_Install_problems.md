---
title: "GTK2.10.14 Install problems"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by crewe on 2007-10-17
I'm trying to update my version of GTK so that I can install the latest version of Gimp, but everytime I ./configure gtk2.10.14 I get this:

```

checking for GLIB - version >= 2.12.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.14.2, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```

I've tried synaptic and that doesn't help, and the apt.

---

### Post by W8eR_CZech on 2007-10-25
I suggest, that you should install the same version, which is in your ubuntu (2.12.11). Worked for me:)

---

