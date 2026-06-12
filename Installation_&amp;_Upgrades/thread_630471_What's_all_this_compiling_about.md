---
title: "What's all this compiling about?"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by wrighty on 2007-12-03
I have old an old box running Ubuntu server dishing up web pages to my Windows network.

I now want to install Open2300 which will allow me to transfer data from my weather station via the serial port on this server.  That way, I can include current weather data on my my website.  The download of Open2300 includes a number of scripts written in C (somename.c)  - my understanding is that I now need to compile these so that they will run.  Unbuntu server does not appear to have a compiler so where do I go from here? 

Thanks,

Ian

---

### Post by luisromangz on 2007-12-03
Yeah, no compiler by default neither in Server or Desktop edition, you'll have to install the build-essential package, and all the other dependencies the configure script (by the way a c file is not a script, it's a source code file), tells you it needs if it fails to create a makefile, provided that program uses the autotools build system, of course.

---

