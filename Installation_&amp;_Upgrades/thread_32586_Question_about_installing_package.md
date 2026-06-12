---
title: "Question about installing package"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by makimonaco1 on 2005-05-08
I have tried do compile/install a package called freeradius ([www.freeradius.org)](www.freeradius.org)). After running the ./configure file I get an error at the end saying:

[COLOR=Navy]configuring in libltdl
running /bin/sh ./configure  --enable-ltdl-install --enable-ltdl-install --cache-file=.././config.cache --srcdir=.
./configure: line 595: ./config.log: Permission denied
configure: error: ./configure failed for libltdl [/COLOR] 

Does anyone know what this means? (sorry but I a LINUX newbee)

Thanks,

Makimonaco

---

### Post by dave9191 on 2005-05-08
It cant access something because you dont have enough privlages to do that. Try putting sudo b4 the command if you trust the package to be installed.

---

### Post by makimonaco1 on 2005-05-08
Hello,

Thanks for the reply I have just tried it. It actually did skip the error messages, I then continued the installation/compilation with 

sudo make

it seemed to do a lot of stuff (sorry but I am new with LINUX). I will go all the way thru see what happens.

Thanks

---

