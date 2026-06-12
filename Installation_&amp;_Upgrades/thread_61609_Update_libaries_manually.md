---
title: "Update libaries manually"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by Trojan1313 on 2005-09-01
Hi, I'd like to update some things without using synaptic, the things I want to update are pygtk, gtk and glib.
The reason? None really, I'm just obsessed with updates.

The thing is, if you update gtk and glib (don't know 'bout pygtk) the old version stays, and this needs to be removed. If I remove it with synaptic it deletes all gtk, meaning just about everything stops working.

How, how, how, hoooow do I fix this?

---

### Post by DJ_Max on 2005-09-01
You're dealing with crucial libraries. I wouldn't tocuh them unless you know what you're doing. Like you said, there's no reason to update, and you're probably just run into problems with little or no benfit.

Anyway, if you still feel the need to mess with things, I wouldn't upgrade, but just rather install side-by-side. Because none of the Ubuntu apps are compiled for different GTK versions, so you probably won't even use it, that is until Breezy w/ GTK+ 2.8.

---

### Post by Trojan1313 on 2005-09-01
I've tried installing side-by-side, but then I get problems when compiling. GAIM complained about having two glibs and not knowing which one to choose.

I know it's really not neccecery, but I still really want to update them for no apparent reason. Is there no way to do this without re-installing every single gtk-using app on my computer?

---

### Post by Trojan1313 on 2005-09-01
checking for GLIB - version >= 2.0.0... no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).

I get that error when trying to compile GAIM 1.5.0. Now I got a reason to update. :)

---

### Post by DJ_Max on 2005-09-01
> **Trojan1313]checking for GLIB - version >= 2.0.0... no
configure: error:
*** GLib 2.0 is required to build Gaim said:**
> http://www.gtk.org/[/url].

I get that error when trying to compile GAIM 1.5.0. Now I got a reason to update. :)
 No, not really. You need libglib2.0-dev packages from the Ubuntu repo.

Glib is a core library, if you want to upgrade, make sure it's not on a Ubuntu partition you want to use, but rather a testing, or "break" box.

---

### Post by Trojan1313 on 2005-09-01
Ah there we go.
Ok, I won't upgrade before I have either a fresh install, an install I'm ready to crash or another PC to test it.
But how is it done if I want to? Is it just to check where synaptic puts it all, delete it (in console mode) and then compile the new one?

---

