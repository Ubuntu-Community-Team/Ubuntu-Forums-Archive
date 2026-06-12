---
title: "gnome-themes preventing ubuntu-desktop from working."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by jonny_sicoli on 2007-10-21
I just updated from Edgy to Gutsy, and if I try to boot regularly, it only gets past the splash screen, and never goes to the login.  So, I'm forced to go to Recovery mode.  Since I can't exactly copy and paste the data over, I'll write the relevant data here.

Basically, since gnome-themes is a dependancy of ubuntu-desktop, edubuntu-desktop, and john, and since gnome-themes is refusing to work for me (error messages shown later), these programs dependant on it won't configure:

```
ubuntu-desktop depends on gnome-themes; however:
package gnome-themes is not configured yet.
```

When I try to configure gnome-themes:

```
Setting up gnome-themes (2.20.0-0ubuntu1) ...
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g-once_init_enter_impl
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g-once_init_enter_impl
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g-once_init_enter_impl
dpkg: error processing gnome-themes (--configure):
subprocess post-installation script returned error exit status 127
errors were encountered bla bla bla, subprocess /usr/bin/dpkg returned errorcode (1)

NOTE:  Again, not cut and pasted.  Just the data I think might help.
```

I am lost here, and I don't want to reinstall Ubuntu!  I have everything right where I want it, and I want the least amount of reconfiguration possible.  What do I do here?

Thanks in advance!

---

### Post by jonny_sicoli on 2007-10-21
bump.

---

