---
title: "cannot compile kernel"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by Prof_Albert on 2006-06-30
i tried to recompile my kernel with the standard config given in /boot/config-2.6.15-25-386
when i compile I (lateron) get this

```
  CC [M]  drivers/usb/net/zd1211/zddebug.o
drivers/usb/net/zd1211/zddebug.c: In function ‘zd1205_dump_regs’:
drivers/usb/net/zd1211/zddebug.c:57: warning: unused variable ‘flags’
  CC [M]  drivers/usb/net/zd1211/zdtkipseed.o
  CC [M]  drivers/usb/net/zd1211/zdmic.o
  DEVLIST drivers/usb/net/zd1211/zddevlist.h
make[4]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2

```

I tried it on my laptop and desktop and it was the same on both of them.

---

### Post by ranf on 2006-07-01
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-June/018793.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-June/018793.html)

---

