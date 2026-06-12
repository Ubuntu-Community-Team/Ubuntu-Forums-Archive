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


EDIT: I've gone back to Jaunty, everything seems to be running fine now... as expected.
there must be something wrong in pulseaudio somewhere.. because in jaunty pulseaudio is .14 and karmic updates to 0.17 i think... i have a feeling somethings broken their thats making my sound hiccup.

---

### Post by Fruchtnektar on 2009-09-22
Seems to be a compile-error mixed with some changes in some libraries.
I solved it by patching

```
#include <stdio.h>
```

into *audibleproperties.h* and any other (header)-file in metadata where the compiling error occours.

Helped to get forward building. But still not building though. If I did it, I will reply.

edit: 
found a Debian Bug Report wich discribes the problems we are discovering.
Fixing the things mentioned there: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=504953](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=504953)

You also need to fix several things if you are using libmtp described under: [http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2008-12/msg01970.html](http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2008-12/msg01970.html)

Amarok will be build after applying the stuff.

Still testing if it works like expected. Butt looks good till now.

edit2:
If you now add the amazon<->lastfm cover-patch, and the wikipedia-patch you are really good to go.
[http://forum.kde.org/viewtopic.php?f=117&t=76607&start=0](http://forum.kde.org/viewtopic.php?f=117&t=76607&start=0)
[https://bugs.edge.launchpad.net/ubuntu/+source/amarok/+bug/316140](https://bugs.edge.launchpad.net/ubuntu/+source/amarok/+bug/316140)

---

### Post by Fruchtnektar on 2009-09-22
It's me again. 
I made a patch-set für building amarok 1.4.10 under Ubuntu 9.10 Karmic Koala. I used the information gathered from the links above.

1. Download amarok1.4.10 source and extract it.
2. copy the diff-file to the newly created amarok-1.4.10 folder and extract it.
3. apply the patch by typing: ```
patch -p1 < amarok-1.4.10-both_wikipedia_patch-last.fm_patch-ubuntu_specific_9.10_build_patch.diff 
```
4. run ```
./configure --without-arts
```
5. install missing dependencies
6. run ```
./configure --without-arts
``` again :), until you installed all missing dependencies 
7. type ```
make
```
8. make sure amarok2 isn't installed any more
9. type ```
sudo make install
```

note: I'm building amarok1 without arts-support. I'm not sure if it is even possible to build it with this support. imho it impossible because of pulseaudio. If someone knows how to build with arts-support: please post it here.

---

