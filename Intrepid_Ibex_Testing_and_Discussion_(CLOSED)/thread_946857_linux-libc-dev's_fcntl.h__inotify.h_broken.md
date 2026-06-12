---
title: "linux-libc-dev's fcntl.h / inotify.h broken?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jmillikin on 2008-10-13
The following program does not compile:

```
#include <linux/inotify.h>

int main () { return 0; }
```

With the error:

```
In file included from /usr/include/asm/fcntl.h:1,
                 from /usr/include/linux/fcntl.h:4,
                 from /usr/include/linux/inotify.h:11,
                 from inotify.c:1:
/usr/include/asm-generic/fcntl.h:120: error: expected specifier-qualifier-list before ‘off_t’
/usr/include/asm-generic/fcntl.h:143: error: expected specifier-qualifier-list before ‘loff_t’

```

It looks like one of the header files is broken, but I can't figure out why -- I haven't done anything wierd with them, just installed the normal linux-libc-dev package.

-----

The specific issue that raised this is that I can no longer compile Tracker in Intrepid.

---

