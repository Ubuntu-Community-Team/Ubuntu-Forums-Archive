---
title: "error while loading shared libraries"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by sabitha on 2006-09-07
i had installed the CCL(cafe con leche) billing sofware for my internet cafe.
but when i want run that it show me the eror :
> admin@admin-raungnet:~$ /usr/local/bin/cclfox -nossl
/usr/local/bin/cclfox: error while loading shared libraries: libccls.so.0: cannot open shared object file: No such file or directory

so i check that shared library (libcclc.so.0) and i found that library on 
/usr/local/lib/libccls.so.0.7.0
/usr/local/lib/libccls.so.0
/usr/local/lib/libccls.so
/usr/local/lib/libccls.la
/usr/local/lib/libccls.a

please tell me where is the wrong. this is important to help all people who use ubuntu for internet cafe. i think a lot of people here use ubuntu for internet cafe.

---

### Post by danf_1979 on 2008-06-02
Hi, just for the record, because this thread is ooooold:

Use: ./configure --prefix=/usr

that should fix it.

---

