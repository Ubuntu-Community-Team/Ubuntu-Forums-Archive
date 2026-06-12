---
title: "Problem finding Glib when compiling GTK+"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by hochiha on 2008-11-06
Hi!

I just downloaded firefox (3.03) and realized I had to install a newer version of gtk (2.10 or higher). This wouldn't be a problem if I was in fact running Ubuntu, since it's in the repositories, but I'm not. I'm running Debian but I figured I would ask here anyway since it's a general question and the Ubuntu forums are the best around.

So far I've compiled & installed glib (2.18.2) in /opt/gtk-2.14/ (heard from somewhere that you could put what you're compiling and dependencies in one place) without any problems.

So far I've tried to compile gtk with:

$ export PKG_CONFIG_PATH="/opt/gtk-2.14/lib/pkgconfig"
$ ./configure --prefix=/opt/gtk-2.14

but it stops saying "Requested 'glib-2.0 >= 2.17.6' but version of GLib is 2.16.3". GLib 2.16.3 is the current version installed via synaptic.

Have no idea of what's wrong, so thanks for any ideas :) oh, and sorry for the wall of text ;)

/HoChiHa

---

### Post by Partyboi2 on 2008-11-07
> "Requested 'glib-2.0 >= 2.17.6' but version of GLib is 2.16.3"Its telling you that the glib version you have installed is older then the one required to compile with.

---

### Post by hochiha on 2008-11-08
> **Partyboi2 said:**
> Its telling you that the glib version you have installed is older then the one required to compile with.

Which is why I downloaded the 2.18 tarball and compiled it...

I just realized my question was a bit unclear, so I'll rephrase it.. how do I make the configure-script find Glib 2.18

---

