---
title: "eee pc 901 webcam doesn't work in amsn"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jiashen on 2009-03-29
Error messenger:

checking if 'capture' extension is loaded...x

---

### Post by captive on 2009-03-30
Have you tried starting it with 
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so amsn
```?
Replace lib32 with lib64 if you are on amd64 version of jaunty

---

### Post by jiashen on 2009-03-30
> **captive said:**
> Have you tried starting it with 
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so amsn
```?
Replace lib32 with lib64 if you are on amd64 version of jaunty

i tried your code in root but i got this:

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by jiashen on 2009-03-30
> **jiashen said:**
> i tried your code in root but i got this:

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

i got it working now, the code should be:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so amsn

Thank you!!!

---

### Post by captive on 2009-03-30
Yes, lib32 and lib64 are path of 64bit distros, in 32bit you just have lib.
Glad to know it works!

---

### Post by nyarnon on 2009-03-31
> **jiashen said:**
> i got it working now, the code should be:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so amsn

Thank you!!!

If that worked then get the source code and compile from scratch you will have a working AMSN.

---

