---
title: "can't compile gcc-4.4.3 - gtype-c.h not found on Ubuntu Lucid 10.04 amd64"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by bademeister on 2010-07-07
Dear all,

I am trying to compile gcc-4.4.3 from sources but can't, make fails with the following error:

```
../../gcc-4.4.3/gcc/c-lang.c:58:21: error: gtype-c.h: No such file or directory
make[3]: *** [c-lang.o] Error 1
```

I do have build-essential installed and couldn't find anything about other requirements. 

I have also attached the output of the *$configure* and *$make* calls in case that might help. 

(In case you're wondering why I am trying to build gcc-4.4.3 even though it is in the repos:
I am trying to get [GCCsense]("http://cx4a.org/software/gccsense/") (C++ code completion for vim) to work and it requires compiling something that was derived from gcc-4.4.3 . I was seeing the same error there and figured it would be easier to figure out how to build it once I can get gcc-4.4.3 to compile...)

Thanks a million
Paul


EDIT: I forgot, this is on Ubuntu 10.04 amd64 with pretty much everything standard (despite what it's saying on the left...)

---

### Post by bademeister on 2010-07-10
gentle bump

---

