---
title: "Flash 4 Linux - Install from tar.bz2?"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by JoeLatics on 2010-08-20
Hi, trying to install F4L, so I downloaded from their page. I now have "f4l-0.2.1.tar.bz2" sat on my desktop - and I haven't got the first idea about how to install it!!

Any help appreciated!

Cheers :)

---

### Post by akester on 2010-08-20
First, you need to extract it.  Open it with the archive manager (assuming you are on a desktop distro) and extract it anywhere you please.

Then run
```
sudo apt-get install build-essential
```(This gets all the compilers needed to build software from source)

Navigate to the folder where you see a file called Makefile, run in the terminal
```
make clean
make
make test
sudo make install

```That should install it, you may need to reboot before using it.

Hope this helps

---

### Post by JoeLatics on 2010-08-20
Cheers for the reply.

It throws back:

"joelatics@joelatics-laptop:~/Desktop/f4l-0.2.1$ make clean
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.
joelatics@joelatics-laptop:~/Desktop/f4l-0.2.1$ make
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.
joelatics@joelatics-laptop:~/Desktop/f4l-0.2.1$ make test
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.
joelatics@joelatics-laptop:~/Desktop/f4l-0.2.1$ sudo make install"

Cheers,
Joe

---

### Post by JoeLatics on 2010-08-21
Anyone know how to create the rule needed?

---

### Post by dagdeniz on 2010-08-21
The above procedure is not necessarily true for installing every application (and lacks the step of configuration, that's "./configure"). 
Referring to the project's website ([http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)), some more steps may be needed. Finish the procedure described there with "sudo make install" if you wish to install.

---

### Post by JoeLatics on 2010-08-22
What's written on the website doesn't seem to work, unfortunately!

I'm a newbie at Ubuntu, so if there's any step by step instructions available, I'd appreciate those!

Cheers,
Joe

---

### Post by JoeLatics on 2010-08-28
Bump!

---

### Post by mucho_maze on 2011-01-30
Joe, did you manager to compile this? I tried:

1. Downloading, unpack.
2. qmake -config --> no errors
3. qmake -m Makefile f4l.pro --> no errors
4. make --> gives the following errors:

g++ -c -pipe -g -fPIC -w -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34,
                 from FSButtonEvent.cpp:22:
FSVector.h:35: fatal error: new.h: No such file or directory
compilation terminated.
make[1]: *** [FSButtonEvent.o] Fejl 1
make[1]: Leaving folder '/home/mads/flash/mirror2/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform-make_default] Error 2

Are there some files missing? What am I doing wrong?

---

### Post by mucho_maze on 2011-01-31
I succeeded in compiling the stuff. I following the instructions given in the movie: [http://www.youtube.com/watch?v=JooYSc6TftU](http://www.youtube.com/watch?v=JooYSc6TftU), however, one other thing was missing for me.

To compile change the following:

src/flagStonePort/transform-cxx-bsd/transform/FSVector.h
line 35: #include <new.h> --> #include <new>

src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h
line 140: FSDefineSound::FSDefineSound --> FSDefineSound

src/f4lmdoc.cpp
line 24 #include <iostream.h> --> #include <iostream>

After that I could compile flawlessly (Ubuntu 10.10, qt3, g++). Not sure if the program itself behaves exactly as is should...

---

### Post by manolomanolo on 2011-08-19
> **mucho_maze said:**
> I succeeded in compiling the stuff. I following the instructions given in the movie: [http://www.youtube.com/watch?v=JooYSc6TftU](http://www.youtube.com/watch?v=JooYSc6TftU), however, one other thing was missing for me.

To compile change the following:

src/flagStonePort/transform-cxx-bsd/transform/FSVector.h
line 35: #include <new.h> --> #include <new>

src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h
line 140: FSDefineSound::FSDefineSound --> FSDefineSound

src/f4lmdoc.cpp
line 24 #include <iostream.h> --> #include <iostream>

After that I could compile flawlessly (Ubuntu 10.10, qt3, g++). Not sure if the program itself behaves exactly as is should...

That worked for me too. Please mark it as [SOLVED]

Also, meanwhile, did you already find a better solution than F4L?
Thanks

---

### Post by manolomanolo on 2011-08-19
I have been too optimistic. Unfortunately it doesn't work for me.
After following mucho_maze's suggestion I get:
> In file included from canvasItem.cpp:18:0:
canvasItem.h:21:21: fatal error: qcanvas.h: File o directory non esistente
compilation terminated.

What can I do then?
Thanks

---

### Post by reap3r119 on 2012-07-27
> **manolomanolo said:**
> I have been too optimistic. Unfortunately it doesn't work for me.
After following mucho_maze's suggestion I get:


What can I do then?
Thanks

Follow The ENTIRE video tutorial. That includes downloading the source from cvs. The CVS version has all files, so that won't happen.

---

