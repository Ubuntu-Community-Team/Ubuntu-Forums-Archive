---
title: "Problems after upgrade"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by jondecker76 on 2012-09-18
An elderly couple that I try to help out is having problems on a recent upgrade to 12.04.  The upgrade appeared to be successful, and upon bootup, the graphical GUI to login appears.  When attempting to log in, it just drops to a terminal.  I have tried running unity from the command line, and I get an error:
```

>unity
> (a bunch of normal messages)
> Starting gtk-window-decorator
> ERROR 2012-09-17 17:39:04 unity.glib-gobject <unknown>:0 g_object_unref: assertion G_IS_OBJECT'(object)' failed
> Setting update "main_menu_key"
> Settign update "run_key"
> Window manager warning: failed to load theme "Adwaita": failed to find a valid file for theme Adwaita
> Segmentation fault (core dumped)

```

Even though it segfaults, the desktop partially loads and I can see a few of the icons and the wallpaper, though no panels or unity sidebar.

The guest login account doesn't drop to a terminal, but still fails to load the unity sidebar or any panels as well.

I have tried deleting ~/.Xauthority* and xorg.conf, but neither of those worked.  

Any ideas what could be going on?

thanks!

---

