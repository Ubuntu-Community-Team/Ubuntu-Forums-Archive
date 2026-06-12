---
title: "The Gremlins got me (unable to load gnome after updates)"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by CJ145 on 2008-02-13
Brand new Ubuntu 7.10 amd64 install.  I have re-installed twice now and I tracked the problem down to installing some updates.

I have all of the sources enabled and two updates checked: Important Security Updates and Recommended Updates.

It installed about 100 updates and when I rebooted I no longer can get back into gnome.  It will let me log in, but right after I hit enter on the password screen it goes to an orange background with a mouse.

I have been trying to figure this out and while doing so I ran into an error when running ldconfig.

It says that there are a bunch of truncated libraries.

/usr/lib32/libX11.so.6
/usr/lib32/libgtk-x11-2.0.so.0
/usr/lib32/lubGLU.so.6.2.0
/usr/lib32/libdb-4.3.so
/usr/lib32.libgtk-x11-2.0.so.0.1200.0
/usr/lib/libgnome-menu.so.2
/usr/lib/libcamel-provider-1.2.so.10
/usr/lib/libcamel-provider-1.2.so.10.0.1
/usr/lib/libgnome-menu.so.2.1.17
/usr/lib/libgs.so.8
/usr/lib/libgs.so.8.61

I know I'm not out of HDD space (22G free on /, 32M free on /boot).  If it matters this is an install on a dmraid device (intel software raid).  I looked around on google a bit and can't seem to find a solution.

---

