---
title: "ld -lssl can't find ssl"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by flickerfly on 2007-12-11
I'm trying to compile a program called Centrallix. It gets almost to the end of configure and pops this error out in config.log.

```
configure:5168: gcc -o conftest -g  -I/usr/include/  -I/usr/include/  conftest.c -lssl  -lCentrallix -lpng -lz -lm -ldl -lcrypt 
 -lreadline -L/usr/include/cxlibs/ >&5
/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status

```

Which reports "configure: error: Centrallix requires OpenSSL to be installed." to the commandline. I have openssl installed.

Any idea what is causing my error?

---

