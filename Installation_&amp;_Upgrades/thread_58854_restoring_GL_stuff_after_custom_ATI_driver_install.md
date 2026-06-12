---
title: "restoring GL stuff after custom ATI driver install?"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by OneSeventeen on 2005-08-21
I've done all the crappy fglrx install stuff required to get my Radeon Xpress 200M to work nicely, but in doing so I had to --force-overwrite the aliened version of ATI's RPM drivers.

This overwrote glib-mesa or something like that, and ever since I did that, the interface for blender3d is SUPER slow.

any ideas what I should re-install if anything?

Also, can I use apt-get to reinstall?  I can't seem to get synaptic to reinstall xlibmesa-gl because:
```

E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb:  trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0

```
(that's the file that made me --force-overwrite to get fglrx to install properly)

**EDIT:**
Okay, I got it to work by doing this-
```

$sudo dpkg -i --force-overwrite /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb

```

then, blender3d started running like a champ!
unfortunately... my glxgears went down to 200FPS!!

So unfortunately the libGL.so.1.2 ATI gives works great for everything but blender's interface, and the libGL.so.1.2 that comes with xlibmesa-gl works great for blender's interface, but not for anything else.

So I just did a dpkg -i --force-overwrite fglrx_whatever.deb

---

