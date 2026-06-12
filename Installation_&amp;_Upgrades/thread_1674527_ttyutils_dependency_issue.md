---
title: "ttyutils dependency issue"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by dc200 on 2011-01-24
I'm trying to install ttyutils and have had to satisfy each one of its dependencies manually. I was able to satisfy all of them up until LUA, and am now stuck at that point in the configuration. Here's where I get stuck:

```
checking for LUA... configure: error: Package requirements (lua >= 5.1) were not met:

No package 'lua' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LUA_CFLAGS
and LUA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

As far as I can tell, I've already got the right LUA libraries. Does anyone know exactly which one it's looking for, and where?

---

