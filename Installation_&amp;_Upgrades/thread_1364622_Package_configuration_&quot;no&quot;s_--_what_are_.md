---
title: "Package configuration &quot;no&quot;s -- what are they?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2009-12-26
Hi, all:

Actually, I'm trying to compile R-Cran and install it. 
I did
```
$ ./configure
```
but I obtained the following "no"s, I just want to know what are they?

1) what is dl ? 
```
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
```

2) where is floatingpoint ?
```
checking floatingpoint.h usability... no
checking floatingpoint.h presence... no
checking for floatingpoint.h... no
```

3) What is xmkmf?
```
checking for xmkmf... no
```

Waiting for your instruction.

Best Regards
JIA

---

### Post by gsmanners on 2009-12-26
Those message mean that you are missing some -dev packages.

I think what you're compiling is available in the repos, and also here:

[http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/)

---

