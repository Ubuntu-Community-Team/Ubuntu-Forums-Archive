---
title: "how do I get c,c++ to compile"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by UpsideDownFace on 2006-10-25
I have been using breezy on my Lenovo R50e laptop for about a year, to compile c and c++ programs.
I now wish to use a Pentium 3 desktop to do the same.
I installed breezy from the same CD as I used on the laptop and when I type "gcc hello.c" it says "hello.c:1:19: error: stdio.h: no such file or directory".
I have typed "which gcc", "ldd /usr/bin/gcc", "ls -l  /lib/tls/i686/cmov/libc.so.6" on both machines; both give the same results.
Why can't I compile on the desktop?

---

### Post by Rui Pais on 2006-10-25
have you done a:
```
sudo aptitude install build-essential
```

---

### Post by UpsideDownFace on 2006-10-25
Muito obrigado!
I did sudo aptitude install build essential and it now works.
I wonder why I didn't need to do it on my laptop.

---

### Post by Rui Pais on 2006-10-25
> **UpsideDownFace said:**
> Muito obrigado!
De nada ;)

> I wonder why I didn't need to do it on my laptop.
you must have done it at sometime and completely forget it about. 
One of the less intuitive names for a package, isn't it?

---

