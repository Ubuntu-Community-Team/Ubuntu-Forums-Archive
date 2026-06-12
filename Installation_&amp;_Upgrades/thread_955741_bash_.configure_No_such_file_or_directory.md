---
title: "bash: ./configure: No such file or directory ????"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by shanks129 on 2008-10-22
thomas@thomas-desktop:~$ cd bwpropset-0.1
thomas@thomas-desktop:~/bwpropset-0.1$ ./configure
bash: ./configure: No such file or directory
thomas@thomas-desktop:~/bwpropset-0.1$ ls
bwpropset.c  Makefile
thomas@thomas-desktop:~/bwpropset-0.1$ 

does anyone know why i get this erroe after using the ./configure command? The only two files i can see in that directory is bwpropset.c and makefile. Anyone have any ideas how i can get this installed? Also if i use the make command i just get a huge list of errors. any help will be greatly appreciated. thanks

---

### Post by Ayuthia on 2008-10-22
What are the errors that you are getting with using make?  Do you have all the dependencies installed?

---

### Post by shanks129 on 2008-10-22
thomas@thomas-desktop:~/bwpropset-0.1$ make
cc -g -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls   -c -o bwpropset.o bwpropset.c
bwpropset.c:18:22: error: X11/Xlib.h: No such file or directory
bwpropset.c:19:23: error: X11/Xutil.h: No such file or directory
bwpropset.c:20:23: error: X11/Xatom.h: No such file or directory
bwpropset.c:21:24: error: X11/Xproto.h: No such file or directory
bwpropset.c:22:28: error: X11/cursorfont.h: No such file or directory
bwpropset.c:24:34: error: X11/extensions/shape.h: No such file or directory
bwpropset.c:25:36: error: X11/extensions/Xrender.h: No such file or directory
bwpropset.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘selectWindow’
bwpropset.c:175: error: expected ‘)’ before ‘*’ token
bwpropset.c:198: error: expected ‘)’ before ‘*’ token
bwpropset.c:216: error: expected ‘)’ before ‘*’ token
bwpropset.c:294: error: expected ‘)’ before ‘*’ token
bwpropset.c:322: error: expected ‘)’ before ‘*’ token
bwpropset.c:347: error: expected ‘)’ before ‘*’ token
bwpropset.c:363: error: expected ‘)’ before ‘*’ token
bwpropset.c:372: error: expected ‘)’ before ‘*’ token
bwpropset.c:379: error: expected ‘)’ before ‘*’ token
bwpropset.c: In function ‘main’:
bwpropset.c:410: error: ‘Display’ undeclared (first use in this function)
bwpropset.c:410: error: (Each undeclared identifier is reported only once
bwpropset.c:410: error: for each function it appears in.)
bwpropset.c:410: error: ‘dpy’ undeclared (first use in this function)
bwpropset.c:412: error: ‘Window’ undeclared (first use in this function)
bwpropset.c:412: error: expected ‘;’ before ‘win’
bwpropset.c:480: warning: implicit declaration of function ‘XParseGeometry’
bwpropset.c:483: error: ‘XValue’ undeclared (first use in this function)
bwpropset.c:483: error: ‘YValue’ undeclared (first use in this function)
bwpropset.c:484: error: ‘WidthValue’ undeclared (first use in this function)
bwpropset.c:484: error: ‘HeightValue’ undeclared (first use in this function)
bwpropset.c:495: error: ‘win’ undeclared (first use in this function)
bwpropset.c:509: warning: implicit declaration of function ‘XOpenDisplay’
bwpropset.c:510: warning: implicit declaration of function ‘XDefaultScreen’
bwpropset.c:513: warning: implicit declaration of function ‘selectWindow’
bwpropset.c:521: warning: implicit declaration of function ‘XGetGeometry’
bwpropset.c:521: error: expected expression before ‘)’ token
bwpropset.c:519: warning: unused variable ‘dummy’
bwpropset.c:528: warning: implicit declaration of function ‘initializeFullscreen’
bwpropset.c:529: warning: implicit declaration of function ‘sendWmStateMessages’
bwpropset.c:530: warning: implicit declaration of function ‘sendWmLevelMessages’
bwpropset.c:533: warning: implicit declaration of function ‘setNoFocus’
bwpropset.c:535: warning: implicit declaration of function ‘setNoInput’
bwpropset.c:537: warning: implicit declaration of function ‘setNoBorder’
bwpropset.c:539: warning: implicit declaration of function ‘XSync’
bwpropset.c:539: error: ‘False’ undeclared (first use in this function)
bwpropset.c:542: warning: implicit declaration of function ‘moveWindow’
bwpropset.c:544: warning: implicit declaration of function ‘resizeWindow’
bwpropset.c:547: warning: implicit declaration of function ‘XCloseDisplay’
make: *** [bwpropset.o] Error 1
thomas@thomas-desktop:~/bwpropset-0.1$ make install
make: *** No rule to make target `install'. Stop.
thomas@thomas-desktop:~/bwpropset-0.1$ make
cc -g -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls   -c -o bwpropset.o bwpropset.c
bwpropset.c:18:22: error: X11/Xlib.h: No such file or directory
bwpropset.c:19:23: error: X11/Xutil.h: No such file or directory
bwpropset.c:20:23: error: X11/Xatom.h: No such file or directory
bwpropset.c:21:24: error: X11/Xproto.h: No such file or directory
bwpropset.c:22:28: error: X11/cursorfont.h: No such file or directory
bwpropset.c:24:34: error: X11/extensions/shape.h: No such file or directory
bwpropset.c:25:36: error: X11/extensions/Xrender.h: No such file or directory
bwpropset.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘selectWindow’
bwpropset.c:175: error: expected ‘)’ before ‘*’ token
bwpropset.c:198: error: expected ‘)’ before ‘*’ token
bwpropset.c:216: error: expected ‘)’ before ‘*’ token
bwpropset.c:294: error: expected ‘)’ before ‘*’ token
bwpropset.c:322: error: expected ‘)’ before ‘*’ token
bwpropset.c:347: error: expected ‘)’ before ‘*’ token
bwpropset.c:363: error: expected ‘)’ before ‘*’ token
bwpropset.c:372: error: expected ‘)’ before ‘*’ token
bwpropset.c:379: error: expected ‘)’ before ‘*’ token
bwpropset.c: In function ‘main’:
bwpropset.c:410: error: ‘Display’ undeclared (first use in this function)
bwpropset.c:410: error: (Each undeclared identifier is reported only once
bwpropset.c:410: error: for each function it appears in.)
bwpropset.c:410: error: ‘dpy’ undeclared (first use in this function)
bwpropset.c:412: error: ‘Window’ undeclared (first use in this function)
bwpropset.c:412: error: expected ‘;’ before ‘win’
bwpropset.c:480: warning: implicit declaration of function ‘XParseGeometry’
bwpropset.c:483: error: ‘XValue’ undeclared (first use in this function)
bwpropset.c:483: error: ‘YValue’ undeclared (first use in this function)
bwpropset.c:484: error: ‘WidthValue’ undeclared (first use in this function)
bwpropset.c:484: error: ‘HeightValue’ undeclared (first use in this function)
bwpropset.c:495: error: ‘win’ undeclared (first use in this function)
bwpropset.c:509: warning: implicit declaration of function ‘XOpenDisplay’
bwpropset.c:510: warning: implicit declaration of function ‘XDefaultScreen’
bwpropset.c:513: warning: implicit declaration of function ‘selectWindow’
bwpropset.c:521: warning: implicit declaration of function ‘XGetGeometry’
bwpropset.c:521: error: expected expression before ‘)’ token
bwpropset.c:519: warning: unused variable ‘dummy’
bwpropset.c:528: warning: implicit declaration of function ‘initializeFullscreen’
bwpropset.c:529: warning: implicit declaration of function ‘sendWmStateMessages’
bwpropset.c:530: warning: implicit declaration of function ‘sendWmLevelMessages’
bwpropset.c:533: warning: implicit declaration of function ‘setNoFocus’
bwpropset.c:535: warning: implicit declaration of function ‘setNoInput’
bwpropset.c:537: warning: implicit declaration of function ‘setNoBorder’
bwpropset.c:539: warning: implicit declaration of function ‘XSync’
bwpropset.c:539: error: ‘False’ undeclared (first use in this function)
bwpropset.c:542: warning: implicit declaration of function ‘moveWindow’
bwpropset.c:544: warning: implicit declaration of function ‘resizeWindow’
bwpropset.c:547: warning: implicit declaration of function ‘XCloseDisplay’
make: *** [bwpropset.o] Error 1




that is the errors im getting, it appears that in that directory there are only 2 files, bwpropset.c and Makefile if that helps at all??  thanks for your help btw.

---

### Post by oldos2er on 2008-10-22
Looks like you're missing some dependencies. Is there a README and/or INSTALL file?

---

### Post by Ayuthia on 2008-10-22
Like oldos2er said, it looks like you are missing some dependencies.  My guess is that you are missing libx11-dev because of the first few error messages saying that it is looking in X11.  Just a guess though.

---

### Post by shanks129 on 2008-10-22
hey man a little bit of success, After i installed that dependency you suggested it got a little further :

thomas@thomas-desktop:~/bwpropset-0.1$ make
cc -g -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls   -c -o bwpropset.o bwpropset.c
cc -lX11 -lXext -lXrender  bwpropset.o   -o bwpropset
thomas@thomas-desktop:~/bwpropset-0.1$ makeinstall
bash: makeinstall: command not found
thomas@thomas-desktop:~/bwpropset-0.1$ make install
make: *** No rule to make target `install'. Stop.
thomas@thomas-desktop:~/bwpropset-0.1$ make
make: `bwpropset' is up to date.
thomas@thomas-desktop:~/bwpropset-0.1$ 


However it still won't install and there is no read me file present with it.

---

### Post by cariboo on 2008-10-22
Does make actually create an executable if so that just type:

```
./bwpropset
```

If the program runs you can move it to /usr/local/bin
once in the directory make sure that is owned by root and executable.

edit: I just had a look at what the program does, Beryl has been folded in to Compiz. To edit Compiz settings, install compizconfig-settings-manager from the repositories

Jim

---

### Post by shanks129 on 2008-10-23
Aye man worked a treat. Cheers. but now i can't get compiz to work properly!! gah!!!

---

