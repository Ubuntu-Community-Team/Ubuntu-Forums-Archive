---
title: "error compiling kernel"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by box2 on 2007-07-17
did an apt-get install of linux-source (2.6.20) and kernel-package.  did a make oldconfig && make menuconfig.  compiling kernel with my new options and it goes for a while then gets this error:

drivers/char/tty_io.c: In function âptmx_openâ:
drivers/char/tty_io.c:2703: error: too few arguments to function âinit_devâ
make[3]: *** [drivers/char/tty_io.o] Error 1

i definately need tty_io, right?

---

### Post by box2 on 2007-07-18
i've been looking at it for a while and searching on google.  i can't find what tty_io.c belongs to, if it's a module or a core component.  and i especially can't figure out which menuconfig option disables using it.  i've tried make clean && make-kpkg clean.  i don't know what else to try..

edit: here's more of the error
```

  CC      drivers/block/rd.o
  LD      drivers/block/built-in.o
  LD      drivers/block/aoe/built-in.o
  LD      drivers/block/paride/built-in.o
  LD      drivers/bluetooth/built-in.o
  LD      drivers/cdrom/built-in.o
  CC      drivers/char/mem.o
  CC      drivers/char/random.o
  CC      drivers/char/tty_io.o
drivers/char/tty_io.c: In function âptmx_openâ:
drivers/char/tty_io.c:2703: error: too few arguments to function âinit_devâ
make[3]: *** [drivers/char/tty_io.o] Error 1
make[2]: *** [drivers/char] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

```

---

