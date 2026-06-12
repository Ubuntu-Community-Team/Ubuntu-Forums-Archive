---
title: "libwebkit-dev stripped?"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Roger E Critchlow Jr on 2009-03-13
I've just reinstalled the libwebkit-dev package, 1.0.1-4, to be sure, but it appears to install a library, /usr/lib/libwebkit-1.0.so, which is stripped of symbols.

Actually, it installs a symbolic link to the same library that libwebkit-1.0-1 installed, rather than a library.

Am I doing something wrong, or is the package busted?

libwebkit-1.0-1-dbg has a library with symbols.

-- rec --

---

### Post by chrisccoulson on 2009-03-13
That's normal. libwebkit-dev should ship an unversioned symlink to the versioned SO library file shipped by libwebkit-1.0-1, as well as the header files (somewhere in /usr/include), needed for building software.

That applies for most (all?) *-dev packages in Ubuntu.

---

