---
title: "Hugin needs libImath?"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sam Lars on 2008-10-28
I upgraded to Intrepid, and now hugin complains on startup about missing a library.
hugin: error while loading shared libraries: libImath.so.2: cannot open shared object file: No such file or directory
I'm running 64-bit, so I tried using getlibs to install hugin-bin, hugin-tools, and libopenexr.  I've tried reinstalling all of them, too.  I looked and found that the libopenexr would be the package containing this libImath, but I even tried installing the regular openexr package and it still won't run.
Anybody know how to get this to work?

---

