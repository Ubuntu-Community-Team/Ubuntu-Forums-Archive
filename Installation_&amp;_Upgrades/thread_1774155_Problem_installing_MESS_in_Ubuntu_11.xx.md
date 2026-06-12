---
title: "Problem installing MESS in Ubuntu 11.xx"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by castiglione on 2011-06-02
Hi,

I'm trying to install the MESS emulator in Ubuntu 11.xx but I'm running into a problem.

I've gotten as far as downloading the source and all (I think) of the necessary libraries but when I:

make TARGET=mess

I get the following error message:

/usr/bin/ld: cannot find -lSDL_ttf
collect2: ld returned 1 exit status
make: *** [obj/sdl/mess/build/m68kmake] Error 1

I've tried Googling to find out what -lSDL_ttf is but have had no luck.

I would greatly appreciate any help in this matter.

c

---

### Post by Silas (son of Silas) on 2012-06-16
Sadly this issue still exists a year later in 12.04 and the help on the MESS WIKI is less than useless.

---

