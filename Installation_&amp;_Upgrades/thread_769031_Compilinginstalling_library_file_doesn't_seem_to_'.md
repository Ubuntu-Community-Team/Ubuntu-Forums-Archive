---
title: "Compiling/installing library file doesn't seem to 'install' newer version"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Neurowiz on 2008-04-26
[This is part of a project that I'm undertaking to update my Edgy Eft GIMP installation from 2.2 to 2.4.5. I don't wish to update my entire OS to update a program, so I'm going back to my old philosophy of configure/make/install my programs.]

I'm attempting to compile/install libexif v0.6.16 which is not available from 6.10 repositories. 

Everything goes well in configure and make - but when I run make install, I do not seem to update /usr/local/lib - I don't find an updated libexif.so.16, I find libexif.so.12. When I attempt to compile the latest libexif-gtk, it complains of not having an updated libexif - and it claims that my version is still 6.12 (which is what is in 6.10 by default).

Looking at the output, the 'sudo make install' seems to be making .12 lib.so instead of .16 - am I doing something wrong?
```

make[3]: Entering directory `/home/michael/work/libexif-0.6.16/libexif'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libexif.la' '/usr/local/lib/libexif.la'
/usr/bin/install -c .libs/libexif.so.12.2.0 /usr/local/lib/libexif.so.12.2.0
(cd /usr/local/lib && { ln -s -f libexif.so.12.2.0 libexif.so.12 || { rm -f libexif.so.12 && ln -s libexif.so.12.2.0 libexif.so.12; }; })
(cd /usr/local/lib && { ln -s -f libexif.so.12.2.0 libexif.so || { rm -f libexif.so && ln -s libexif.so.12.2.0 libexif.so; }; })
/usr/bin/install -c .libs/libexif.lai /usr/local/lib/libexif.la
/usr/bin/install -c .libs/libexif.a /usr/local/lib/libexif.a
chmod 644 /usr/local/lib/libexif.a
ranlib /usr/local/lib/libexif.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

```

What am I missing? Should I uninstall the old version first before compiling/installing the new one? Shouldn't I be able to have older and new versions available at the same time?

Neurowiz

---

