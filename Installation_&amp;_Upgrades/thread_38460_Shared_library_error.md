---
title: "Shared library error"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by moment on 2005-05-31
Hi all :)

I installed Eagle (Printed circuit board design tool) 4.11-8 from Hoary today. When I try to run it I got this shared library error:
```
./eagle: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```
I installed the libstdc++6 but it doesn't have this file in it. I tried to make a symbolic link to mine by:
```
ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.2-2.so.3
```
but then I get another error saying:
```
./eagle: relocation error: ./eagle: undefined symbol: __builtin_new
```
so I'm lost here now. Does anybody know how I can get this program working?

---

### Post by moment on 2005-05-31
Nevermind I managed to install it manually from the source.
cheers

---

