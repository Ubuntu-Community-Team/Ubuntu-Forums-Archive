---
title: "Weird sound problems in Karmic"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sudo panda on 2009-09-12
Hey everyone, I'm currently running Ubuntu Karmic 9.10 
ive been having some weird sound problems lately and was wondering if anyone could help me diagnose the problem.

First, i tried to build an amarok 1.4.10 source which failed at the 'make' stage with a recursive error.

```
Making all in audible
make[5]: Entering directory `/home/matt/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
make[6]: Entering directory `/home/matt/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
/bin/bash ../../../../libtool --silent --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../../.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/local/include/taglib    -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT audibleproperties.lo -MD -MP -MF .deps/audibleproperties.Tpo -c -o audibleproperties.lo audibleproperties.cpp
audibleproperties.cpp: In member function 'void TagLib::Audible::Properties::readAudibleProperties(FILE*, int)':
audibleproperties.cpp:77: error: 'fseek' was not declared in this scope
audibleproperties.cpp:78: error: 'fread' was not declared in this scope
make[6]: *** [audibleproperties.lo] Error 1
make[6]: Leaving directory `/home/matt/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/matt/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/matt/Downloads/amarok-1.4.10/amarok/src/metadata'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/matt/Downloads/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matt/Downloads/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matt/Downloads/amarok-1.4.10'
make: *** [all] Error 2

```

Then, i tried to use another player and it played for about 5 seconds and then the sound stopped working completely. :confused:

Does anyone know whats going on?

Any help would be greatly appreciated!

---

### Post by tacantara on 2009-09-12
Karmic is still in the testing stages.  I don't know if that has anything to do with your problem, but you might get more answers on this by posting it in the Karmic Koala Testing thread.  I haven't tinkered with it much, so I can't be of any help on this.  I hope you do find an answer though :)

---

### Post by sudo panda on 2009-09-12
ahhh thats true! :)
thank you very much i shall move it.

---

