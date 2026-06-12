---
title: "Darktable build issues after 13.04 upgrade"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by Wayne_V on 2013-05-01
Yesterday I did an online update from Ubuntu 12.10 to 13.04. Everything appeared to go smoothly.

Afterwards, when I went to rebuild Darktable (from git), it failed, looking for /usr/lib/libIlmImf.so. I found the lib was there, just not linked properly into /usr/lib.  I fixed that one and then hit a couple more similar issues before the build completed successfully.


I believe I saw that some people have already built Darktable on 13.04 without issues -- but not sure if was a 13.04 upgrade or scratch install ...


So the question is, is this just something that went wrong during my upgrade or has anyone else seen similar problems?


Note -- here is what I had to do to get Darktable to build:


```
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libIlmImf.so.6.0.0 /usr/lib/libIlmImf.so
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libImath.so.6.0.0 /usr/lib/libImath.so
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libIex.so.6.0.0 /usr/lib/libIex.so
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libIlmThread.so.6.0.0 /usr/lib/libIlmThread.so 
$ sudo ln -s /usr/include/lensfun/lensfun.h /usr/include/lensfun.h

```

---

### Post by gwing on 2013-07-05
Thank you for this Wayne.  I had exactly the same problem compiling darktable from git on  a Mint 13.04 fresh install and after your workaround it compiled nice and cleanly.

---

