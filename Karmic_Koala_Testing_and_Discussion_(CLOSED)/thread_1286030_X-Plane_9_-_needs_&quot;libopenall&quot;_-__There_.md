---
title: "X-Plane 9 - needs &quot;libopenall*&quot; -  There are none in Karmic."
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-08
"./X-Plane_Updater_Linux: error while loading shared libraries:
libopenal.so.0: cannot open shared object file: No such file or
directory."

In Karmic, there are no "libopenal" files in the repository.  There is "libopenal1",  and that is already installed.

Any ideas?


Post on X-Plane Forum:
[http://forums.x-plane.org/index.php?showtopic=41319&st=0&gopid=460284&#entry460284](http://forums.x-plane.org/index.php?showtopic=41319&st=0&gopid=460284&#entry460284)

---

### Post by psyke83 on 2009-10-08
> **emarkay said:**
> "./X-Plane_Updater_Linux: error while loading shared libraries:
libopenal.so.0: cannot open shared object file: No such file or
directory."

In Karmic, there are no "libopenal" files in the repository.  There is "libopenal1",  and that is already installed.

Any ideas?


Post on X-Plane Forum:
[http://forums.x-plane.org/index.php?showtopic=41319&st=0&gopid=460284&#entry460284](http://forums.x-plane.org/index.php?showtopic=41319&st=0&gopid=460284&#entry460284)


The "libopenal1" package is correct, but it appears to be missing a symlink. You can add it yourself:

```
$ sudo ln -s libopenal.so.1.8.466 /usr/lib/libopenal.so.0
```

---

### Post by emarkay on 2009-10-08
EXCELLENT!  Thanks!

(Now I just realized I haven't installed X-Plane in Karmic yet!)  :(

---

