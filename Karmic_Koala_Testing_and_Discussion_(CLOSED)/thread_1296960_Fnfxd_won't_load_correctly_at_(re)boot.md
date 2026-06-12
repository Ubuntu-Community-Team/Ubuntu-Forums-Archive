---
title: "Fnfxd won't load correctly at (re)boot"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ixtao on 2009-10-21
I noticed my function-keys don't work upon installing fnfxd (which for some reason isn't installed by default), and I try 'sudo fnfxd' and it says;

```
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: According to /var/run/fnfxd.pid, another instance of `fnfxd` is already running (PID = 979).
If this is not the case, please remove /var/run/fnfxd.pid.
```
So I 'sudo rm /var/run/fnfxd.pid' + 'sudo fnfxd' and it's ok. 

But why do I have this problem and does anyone know an elegant fix? The same computer functioned just fine with Jaunty..

---

