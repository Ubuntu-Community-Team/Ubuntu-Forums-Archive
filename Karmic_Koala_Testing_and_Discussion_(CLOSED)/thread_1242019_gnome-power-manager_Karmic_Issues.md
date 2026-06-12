---
title: "gnome-power-manager Karmic Issues"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chronosMark on 2009-08-16
Hi All

I've been experiencing some issues under karmic where the power management does not seem to be functioning correctly either not working at all or only working intermediately.
I had chance to look into the issue today and I found that by killing the gnome-power-manager process that is spawned at startup and then running gnome-power-manager everything seems to work fine.

So I was wondering has anyone else experienced this issue? 
Also does anyone know if this is perhaps an issue to do with the order stuff is started in I was wondering in paticular if it was to do with the change from HAL to DeviceKit-power. If so does anyone know how to change this order?

Edit: 

Forgot to mention I noticed in the syslog this warning

Aug 16 20:24:00 X gdm-simple-greeter[4312]: WARNING: Could not ask power manager if user can suspend: The name org.freedesktop.PowerManagement was not provided by any .service files

anyideas if this is something important? I did have a Google but did not find anything very helpful and nothing about this warning under Ubuntu.

Thanks

---

