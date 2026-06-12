---
title: "too silent bash"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-28
Recently ungraded bash is too silent. Starting an inexistent command doesn't say something such "command wasn't found in this PATH":

```
$ bash --version
GNU bash, version 4.0.28(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
$ qwerty
$

```

How to force a bash to be more informative?

---

### Post by ssam on 2009-08-28
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/419806](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/419806)

---

