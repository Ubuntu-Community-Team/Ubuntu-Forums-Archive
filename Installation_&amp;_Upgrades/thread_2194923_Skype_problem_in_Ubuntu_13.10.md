---
title: "Skype problem in Ubuntu 13.10"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by hrshadhin on 2013-12-21
After installing skype. when i run,its crush. I put these error below. Someone help plz
> skype
*** Error in `skype': double free or corruption (fasttop): 0xed245988 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x767c2)[0xf24d57c2]
/lib/i386-linux-gnu/libc.so.6(+0x77510)[0xf24d6510]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZdlPv+0x1f)[0xf26bca3f]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZdaPv+0x1b)[0xf26bca8b]
skype(+0x10df599)[0xf6ba6599]
skype(+0xf791ba)[0xf6a401ba]
======= Memory map: ========
e1839000-e1a00000 rw-p 00000000 00:00 0 
e1a00000-e1ade000 rw-p 00000000 00:00 0 
e1ade000-e1b00000 ---p 00000000 00:00 0

---

