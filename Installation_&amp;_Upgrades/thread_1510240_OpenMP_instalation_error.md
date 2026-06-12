---
title: "OpenMP instalation error"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by lunit2 on 2010-06-15
Hi,

I get an error trying to install OpenMP, the gcc compiler version 4.3.2.

I installed the two things it requires, gmp and mpfr. Plus the others which come with ubuntu.

```

checking for i686-pc-linux-gnu-gcc... /home/user2/Install/gcc-4.3.2/host-i686-pc-linux-gnu/gcc/xgcc -B/home/user2/Install/gcc-4.3.2/host-i686-pc-linux-gnu/gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include
checking for suffix of object files... configure: error: cannot compute suffix of object files: cannot compile
See `config.log' for more details.
make[2]: *** [configure-stage1-target-libgcc] Error 1
make[2]: Leaving directory `/home/user2/Install/gcc-4.3.2'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/user2/Install/gcc-4.3.2'
make: *** [all] Error 2

```How can I fix this?


Thanks.

---

