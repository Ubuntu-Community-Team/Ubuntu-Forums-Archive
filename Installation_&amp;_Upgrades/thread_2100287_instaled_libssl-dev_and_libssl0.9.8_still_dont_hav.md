---
title: "instaled libssl-dev and libssl0.9.8 still dont have it in usr/lib folder"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by howhy on 2013-01-01
i tried installing libssl.0.9.8

 sudo apt-get install libssl0.9.8

and by  sudo apt-get install libssl-dev 

but i still dont see libssl.so.0.9.8 in usr/lib directory...

I am on ububti x64 does it goes somewhere else ?

---

### Post by steeldriver on 2013-01-01
did you look in the subdirs? I think libssl.so.x.x.x usually goes in an architecture subdir:

```
$ find /usr/lib -name 'libssl*' -ls
1573469    0 lrwxrwxrwx   1 root     root           10 Aug 31 04:02 /usr/lib/x86_64-linux-gnu/libssl3.so.1d -> libssl3.so
1573948  376 -rw-r--r--   1 root     root       383608 Jul 29 08:43 /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0
1585552    0 lrwxrwxrwx   1 root     root           15 Jul 29 08:43 /usr/lib/x86_64-linux-gnu/libssl.so -> libssl.so.1.0.0
1585547    4 -rw-r--r--   1 root     root          290 Jul 29 08:43 /usr/lib/x86_64-linux-gnu/pkgconfig/libssl.pc
1585550  620 -rw-r--r--   1 root     root       634286 Jul 29 08:43 /usr/lib/x86_64-linux-gnu/libssl.a
1573482  260 -rw-r--r--   1 root     root       263040 Aug 31 04:02 /usr/lib/x86_64-linux-gnu/libssl3.so
```

---

### Post by fdrake on 2013-01-01
> **howhy said:**
> i tried installing libssl.0.9.8

 sudo apt-get install libssl0.9.8

and by  sudo apt-get install libssl-dev 

but i still dont see libssl.so.0.9.8 in usr/lib directory...

I am on ububti x64 does it goes somewhere else ?
did the install give any errors?

---

