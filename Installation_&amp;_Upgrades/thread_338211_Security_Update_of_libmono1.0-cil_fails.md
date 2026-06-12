---
title: "Security Update of libmono1.0-cil fails"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Tux Aubrey on 2007-01-14
I did an update on an old machine (running a fairly clean edgy install) today and got an error when the install fails for libmono1.0-cil.  I tried again a couple of hours later and get the same error.

The error says:
> 
E: /var/cache/apt/archives/libmono1.0-cil_1.1.17.1-1ubuntu7.1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/mono/gac/Mono.Data.SybaseClient/1.0.5000.0__0738eb9f132ed756/Mono.Data.SybaseClient.dll.mdb')

The machine rebooted fine, so its obviously not tragic, but does anyone know if this is a bug, a transient thing or something I should fix now.

I wouldn't ask, except its a security update.

---

