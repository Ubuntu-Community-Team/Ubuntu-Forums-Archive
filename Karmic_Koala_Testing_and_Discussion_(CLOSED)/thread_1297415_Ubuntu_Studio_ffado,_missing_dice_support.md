---
title: "Ubuntu Studio ffado, missing dice support?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nexus_6 on 2009-10-21
I'm wondering why the ffado library that is shipped with ubuntu studio 9.10 seems to be lacking dice support. I don't know if this really is the case, but installing from source solves the problem, as described in this thread: [http://ubuntuforums.org/showthread.php?t=1071904](http://ubuntuforums.org/showthread.php?t=1071904)

Compiling and installing from source makes my FW interface work, but due to the dependencies of ffado and jackd related packages a lot of applications are getting removed in the process :(

Anyone have an idea regarding this matter, or know how to cleanly replace only the jackd and ffado packages? Should i report this somewhere else, or not complain at all? Please help ;)


Edit: Could I just apt-get source the jackd and libffado packages and replace them with the custom versions from svn before building?

---

