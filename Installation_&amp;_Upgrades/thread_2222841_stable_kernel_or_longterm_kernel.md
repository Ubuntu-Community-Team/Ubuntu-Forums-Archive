---
title: "stable kernel or longterm kernel?"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by Ubi_one_2014 on 2014-05-08
Hello

current kernel, on ubuntu 14.04:
```
$ uname -r
3.14.2-031402-generic


```

however, when i go to [www.kernel.org](www.kernel.org), i notice of a longterm kernel, version 3.12.18
so what is better, a stable kernel or a longterm kernel

---

### Post by slickymaster on 2014-05-08
There are several main categories into which kernel releases may fall.

_Prepatch kernels_
Prepatch or "RC" kernels are mainline kernel pre-releases that are mostly aimed at other kernel developers and Linux enthusiasts. They must be compiled from source and usually contain new features that must be tested before they can be put into a stable release. Prepatch kernels are maintained and released by Linus Torvalds.
_Mainline kernels_
Mainline tree is maintained by Linus Torvalds. It's the tree where all new features are introduced and where all the new development happens. New mainline kernels are released every 2-3 months.
_Stable kernels_
After each mainline kernel is released, it is considered "stable." Any bug fixes for a stable kernel are backported from the mainline tree and applied by a designated stable kernel maintainer. There are usually only a few bugfix kernel releases until next mainline kernel becomes available -- unless it is designated a "longterm maintenance kernel." Stable kernel updates are released on as-needed basis, usually 2-3 a month.
_Longterm kernels_
There are usually several "longterm maintenance" kernel releases provided for the purposes of backporting bugfixes for older kernel trees. Only important bugfixes are applied to such kernels and they don't usually see very frequent releases, especially for older trees.
_Distribution kernels_
Many Linux distributions provide their own "longterm maintenance" kernels that may or may not be based on those maintained by kernel developers. These kernel releases are not hosted at kernel.org and kernel developers can provide no support for them.

---

