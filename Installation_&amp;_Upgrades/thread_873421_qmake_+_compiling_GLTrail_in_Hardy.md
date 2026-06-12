---
title: "qmake + compiling GLTrail in Hardy"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by skinny honkie on 2008-07-29
So I came across a need for [this app.]("http://www.fudgie.org/gltrail.html") As it isn't in the official repos for gutsy or hardy, I pull down the source [from here]("http://github.com/Fudge/gltrail/tree/master") and RTFM.

The first command (sudo apt-get install qt4-dev-tools) brings about the notification that qmake is available in the libqt4-dev package, which I go and install (it ends up in /usr/bin). I then proceed to step 2, wherein I cd to the dir of the extracted source and run: (qmake -unix -recursive -o Makefile gltrail.pro && make)

Which gives me the following output:

Reading /home/skinny/Desktop/gltrail/src/src.pro
cd src/ && make -f Makefile 
make[1]: Entering directory `/home/skinny/Desktop/gltrail/src'
g++  -o ../bin/gltrail main.o activity.o element.o textured_element.o window.o glwidget.o background_updater.o input.o ssh.o digg.o twitter.o moc_window.o moc_glwidget.o moc_background_updater.o moc_ssh.o moc_digg.o moc_twitter.o    -L/usr/lib -L/usr/X11R6/lib -lQtOpenGL -lQtGui -lQtNetwork -lQtCore -lGLU -lGL -lpthread
/usr/bin/ld: cannot open output file ../bin/gltrail: Permission denied
collect2: ld returned 1 exit status
make[1]: *** [../bin/gltrail] Error 1
make[1]: Leaving directory `/home/skinny/Desktop/gltrail/src'
make: *** [sub-src-make_default] Error 2

I've tried a few different things to sort this out, from various things I've found about qmake on this forum, but I'd be interested to know if anyone else has any knowledge they could impart.


Cheers!

---

### Post by Fudgie on 2008-07-30
Looks like there's already something called gltrail in the /home/skinny/Desktop/gltrail/ directory, which you're unable to overwrite. Maybe you unpacked the archive as root, and am now compiling it as a normal user?

---

### Post by skinny honkie on 2008-07-31
Heh - I initially unpacked it as a normal user, and ran qmake as a normal user.
When qmake didn't work it's magic, I tried running sudo qmake, which failed with the exact same error.

However - when I went to a real root terminal with sudo bash, I was then able to run qmake, and all was happy and good on our test box :-)
I find it interesting that the qmake process would run as root, but not with the root privileges granted by sudo.

Thank you very much Fudgie, for the nudge in the right direction.

Salut!

---

