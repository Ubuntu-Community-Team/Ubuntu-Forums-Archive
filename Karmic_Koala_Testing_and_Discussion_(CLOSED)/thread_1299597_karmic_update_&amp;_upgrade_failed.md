---
title: "karmic update &amp; upgrade failed"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mepp on 2009-10-24
i got error messages while performing daily apt-get update & upgrade:

```

Preparing to replace util-linux 2.16-1ubuntu4 (using .../util-linux_2.16-1ubuntu5_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/util-linux_2.16-1ubuntu5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.16-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```i'm using ubuntu 9.10.
any information to fix this? thx.

---

### Post by mepp on 2009-10-24
solved by:
sudo mv /usr/local/bin/install-info /usr/local/bin/install-info-gnu

---

### Post by motsteve on 2009-10-24
Does this mean you had to move the name of the sub directory? Yikes!

---

### Post by mepp on 2009-10-24
> **motsteve said:**
> Does this mean you had to move the name of the sub directory? Yikes!
it's a file, not a directory.
i dont if there any side effect. my ubuntu works just all right so far.

---

