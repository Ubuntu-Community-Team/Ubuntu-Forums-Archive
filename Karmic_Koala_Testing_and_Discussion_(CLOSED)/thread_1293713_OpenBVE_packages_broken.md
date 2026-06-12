---
title: "OpenBVE packages broken?"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by spoons on 2009-10-17
Is it just me having this problem? OpenBVE depends on a libtaoframework from 2007, when the one installed is 2009. I'm on AMD64, this sounds like a packaging issue?

Here's the problem:
openbve:
  Depends: libtaoframework-openal1.1-cil (<2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed
  Depends: libtaoframework-sdl1.2-cil (<2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed

Any ideas?

---

