---
title: "Installing PHP-GTK"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by Sh4wn on 2007-03-12
Hi all,

I'm trying to install PHP-GTK extension, but I'm experiencing some problems..

I've downloaded the last source tarball from [http://gtk.php.net](http://gtk.php.net), and extracted it. Then in command line, i type ./buildconf everything works fine so far, but than comes the ./configure part, and a problem too.

When I type ./configure, it sais, I have installed a version of Glib lower than 2.6, and you need 2.6 or higher. So I downloaded Glib 2.6.6 source tar ball, and extracted it too. It compiles without a problem, so I try to install PHP-GTK again. But now I get the message:

```

checking for GLIB - version >= 2.6.0...
*** 'pkg-config --modversion glib-2.0' returned 2.6.6, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

And now, I don't know what to do anymore, anyone ideas?

Thanks in advance.

---

### Post by Sh4wn on 2007-03-12
Well, I already fixed it, just re-installed libgtk through synaptic, and it worked xD

---

