---
title: "capture 1.0.4 make error"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by shrive22 on 2007-12-26
Hello everyone, I am trying to install the capture-1.0.4-cvs-20071123.  when i perform the make command i receive this error:

johns@johnsubuntu:~/Desktop/capture-1.0.4-cvs-20071123$ make
gcc capture.o ptp-utils.o server.o client.o properties.o commands.o viewfinder.o -pedantic -pedantic-errors -Wall -ggdb -O0  -DHAVE_GTK -DHAVE_READLINE `pkg-config --cflags gtk+-2.0`  -lusb -lptp2 -lpthread `pkg-config --libs gtk+-2.0` -lreadline -lhistory -lncurses -o capture
/usr/bin/ld: cannot find -lreadline
collect2: ld returned 1 exit status
make: *** [capture] Error 1

I have searched for lreadline but could not find anything.  I think it has something to do with the linker(ld) but beyond that I have no idea.

Thanks for the help.

---

