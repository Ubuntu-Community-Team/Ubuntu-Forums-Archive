---
title: "emacs wont open after installation"
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by rajan92 on 2019-04-13
[B]lsb_release -a 
[/B]No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic


[B]CPU
[/B]AMD RYZEN 2600[B]

Error[/B]
emacs25: error while loading shared libraries: libotf.so.0: cannot open shared object file: No such file or directory

---

### Post by Rubi1200 on 2019-04-13
Hi and welcome to the forums :-)

Please post the results of this command:

```
locate libotf.so
```

Thanks.

---

