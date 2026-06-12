---
title: "gl.h"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2010-05-29
Hi
how do i find which package offers gl.h?
Thanks

---

### Post by ad_267 on 2010-05-29
```
sudo apt-get install apt-file
apt-file search -x "/gl\.h$"
```

The -x means use a regular expression, you could also just use "apt-file search /gl.h" but that would give you some html and other file types too.

There are a number of different libraries that have a gl.h file, the one you're after might be this:
```
mesa-common-dev: /usr/include/GL/gl.h
```

The full output was:
```
k3d-dev: /usr/include/k3d/k3dsdk/gl.h
libcgal-dev: /usr/include/CGAL/gl.h
libclanlib-dev: /usr/include/ClanLib-1.0/ClanLib/gl.h
libcoin40-dev: /usr/include/Inventor/C/glue/gl.h
libcoin40-dev: /usr/include/Inventor/system/gl.h
libcoin60-dev: /usr/include/Inventor/C/glue/gl.h
libcoin60-dev: /usr/include/Inventor/system/gl.h
libfltk1.1-dev: /usr/include/FL/gl.h
libroot5.18: /usr/lib/root/5.18/cint/include/GL/gl.h
libsofa1-dev: /usr/include/sofa/helper/system/gl.h
mesa-common-dev: /usr/include/GL/gl.h
mingw-w64: /usr/amd64-mingw32msvc/include/GL/gl.h
mingw32-runtime: /usr/i586-mingw32msvc/include/GL/gl.h
nvidia-173-dev: /usr/include/nvidia-173/GL/gl.h
nvidia-96-dev: /usr/include/nvidia-96/GL/gl.h
nvidia-current-dev: /usr/include/nvidia-current/GL/gl.h
```

---

