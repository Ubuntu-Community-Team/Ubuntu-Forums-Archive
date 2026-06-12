---
title: "Compiling lcdtest with scons doesn't work"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by mpw on 2011-02-04
Hello,

I want to test my new lcd display. I could just find one programm for this on Linux: lcdtest.

But there are no binaries, so I tried to compile it with scons, as the README tells me.


[http://www.brouhaha.com/~eric/software/lcdtest/download/]("http://www.brouhaha.com/%7Eeric/software/lcdtest/download/")


What I did:
```
cd /tmp
wget ***.tar.gz
tar xvfz lcd**
cd lcd**
sudo apt-get install libsdl1.2 libsdl1.2-dev
scons
```What I get is:

```
mpw@MPWs-Laptop:/tmp/lcdtest-1.18$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
gcc -o build/lcdtest.o -c -g -Wall -Wextra -DRELEASE=1.18 src/lcdtest.c
src/lcdtest.c:33:27: error: SDL/SDL_image.h: No such file or directory
src/lcdtest.c:34:25: error: SDL/SDL_ttf.h: No such file or directory
src/lcdtest.c:109: error: expected ')' before '*' token
src/lcdtest.c: In function 'create_text_surface':
src/lcdtest.c:157: error: 'TTF_Font' undeclared (first use in this function)
src/lcdtest.c:157: error: (Each undeclared identifier is reported only once
src/lcdtest.c:157: error: for each function it appears in.)
src/lcdtest.c:157: error: 'font' undeclared (first use in this function)
src/lcdtest.c:163: warning: implicit declaration of function 'TTF_WasInit'
src/lcdtest.c:163: warning: implicit declaration of function 'TTF_Init'
src/lcdtest.c:166: warning: implicit declaration of function 'TTF_OpenFont'
src/lcdtest.c:170: warning: implicit declaration of function 'TTF_FontLineSkip'
src/lcdtest.c:172: warning: implicit declaration of function 'get_text_size'
src/lcdtest.c:208: warning: comparison between signed and unsigned integer expressions
src/lcdtest.c:218: warning: implicit declaration of function 'TTF_RenderText_Blended'
src/lcdtest.c:234: warning: implicit declaration of function 'TTF_CloseFont'
scons: *** [build/lcdtest.o] Error 1
scons: building terminated because of errors.
```Ok, then I tried the sources from libsdl.org

They were easy to compile. But still same errors.

Now, when I type: scons /tmp/SDL* it works!

```
mpw@MPWs-Laptop:/tmp/lcdtest-1.18$ scons /tmp/SDL-1.2.14
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
scons: `/tmp/SDL-1.2.14' is up to date.
scons: done building targets.

```But I can't install it with scons install /tmp/SDL* and the subfolder bulid is empty, not lcdtest binary was made.

Thanks for help. I never used scons.

Bye
MPW

---

### Post by realzippy on 2011-02-04
Sorry cannot help with scons,
but maybe you want to install the (older) *.deb* version until you find out what causes the compiling error.

[http://debian.sil.at/grml/bin/pool/main/l/lcdtest/](http://debian.sil.at/grml/bin/pool/main/l/lcdtest/)

---

### Post by mpw on 2011-02-04
Thanks,

but i'd like to understand what's going wrong here.

And, have you seen the year when the deb was made? :P
/ah sorry, there's one from 2007 too. Okay I'm gonna give it a try.

/update: The deb 1.08 works nicely with 10.10. 


But I'd still like to compile it myself :-) Any ideas?

---

