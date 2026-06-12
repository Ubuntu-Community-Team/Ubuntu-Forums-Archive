---
title: "GCC and GLIBC_2.11 not found"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by jp10 on 2011-04-08
I re-install GCC using synaptic package

on command line - I'm getting this

gcc: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by gcc)


$ ldd -v /usr/bin/gcc
/usr/bin/gcc: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /usr/bin/gcc)
    linux-gate.so.1 =>  (0xb7721000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb75ad000)
    /lib/ld-linux.so.2 (0xb7722000)

    Version information:
    /usr/bin/gcc:
        libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.11) => not found
        libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
        libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
    /lib/tls/i686/cmov/libc.so.6:
        ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
        ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2


What am I missing or forget to do

Thanks

---

