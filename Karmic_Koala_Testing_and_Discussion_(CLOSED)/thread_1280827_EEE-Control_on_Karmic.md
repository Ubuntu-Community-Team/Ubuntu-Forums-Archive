---
title: "EEE-Control on Karmic"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-10-02
Hey There,

So I like to use EEE Control on my netbook but there is not .deb installer for Karmic on [the website](http://greg.geekmind.org/eee-control/). And when I try to install from source I get the following error message: ```
jeff@eeetop:~/Downloads/eee-control-0.9.4$ python setup.py install
running install
running build
running build_py
running build_ext
building 'EeeControl.ioport' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.6 -c ioport/ioport.c -o build/temp.linux-i686-2.6/ioport/ioport.o
ioport/ioport.c:46:20: error: Python.h: No such file or directory
ioport/ioport.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ioport/ioport.c: In function ‘validate’:
ioport/ioport.c:69: warning: implicit declaration of function ‘PyErr_SetString’
ioport/ioport.c:69: error: ‘ErrorObj’ undeclared (first use in this function)
ioport/ioport.c:69: error: (Each undeclared identifier is reported only once
ioport/ioport.c:69: error: for each function it appears in.)
ioport/ioport.c: At top level:
ioport/ioport.c:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ioport/ioport.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ioport/ioport.c:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ioport/ioport.c:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ioport/ioport.c:162: error: array type has incomplete element type
ioport/ioport.c:163: error: ‘PyCFunction’ undeclared here (not in a function)
ioport/ioport.c:163: error: expected ‘}’ before ‘iop_outb’
ioport/ioport.c:164: error: expected ‘}’ before ‘iop_inb’
ioport/ioport.c:165: error: expected ‘}’ before ‘iop_ioperm’
ioport/ioport.c:166: error: expected ‘}’ before ‘iop_iopl’
ioport/ioport.c:167: error: ‘NULL’ undeclared here (not in a function)
ioport/ioport.c:167: error: expected ‘}’ before ‘NULL’
ioport/ioport.c: In function ‘initioport’:
ioport/ioport.c:176: error: ‘PyObject’ undeclared (first use in this function)
ioport/ioport.c:176: error: ‘m’ undeclared (first use in this function)
ioport/ioport.c:176: error: ‘d’ undeclared (first use in this function)
ioport/ioport.c:176: warning: left-hand operand of comma expression has no effect
ioport/ioport.c:178: warning: implicit declaration of function ‘Py_InitModule4’
ioport/ioport.c:180: error: expected expression before ‘)’ token
ioport/ioport.c:183: warning: implicit declaration of function ‘PyModule_GetDict’
ioport/ioport.c:184: error: ‘ErrorObj’ undeclared (first use in this function)
ioport/ioport.c:184: warning: implicit declaration of function ‘PyString_FromString’
ioport/ioport.c:185: warning: implicit declaration of function ‘PyDict_SetItemString’
ioport/ioport.c:192: warning: implicit declaration of function ‘PyErr_Occurred’
ioport/ioport.c:193: warning: implicit declaration of function ‘Py_FatalError’
error: command 'gcc' failed with exit status 1

```

Any suggestions? Or anyone know if there is a .deb installer lurking around for Karmic for this package?

Thanks,
~Jeff

---

### Post by jbernardo on 2009-10-02
I just picked the jaunty deb, and repackaged it to disable the dkms part, which doesn't work in karmic kernels. Anyway, the author is working on a karmic version, should be out there soon, now that karmic is in beta.

---

### Post by kgarbutt on 2009-10-08
There is a similar one called eee-applet which is in the karmic repositiories. If you want to check it out, then apt-cache show eee-applet from the terminal. Should you install it, you should find it in the System Tools menu.

I like eee-control better though so I'm waiting for it.

---

### Post by beastrace91 on 2009-10-08
> **kgarbutt said:**
> I like eee-control better though so I'm waiting for it.

Yep, I've found eee-applet does not work in the slightest (at least on my 900A) I wish they'd put eee-control on the repos...

~Jeff

---

### Post by gmc on 2009-10-08
Hmm, I don't know if you saw this or not but it looks like you can install the jaunty version into karmic (if you can't wait for an official version).

[http://ubuntuforums.org/showthread.php?t=1274216](http://ubuntuforums.org/showthread.php?t=1274216)

G

---

### Post by tawmas on 2009-10-08
> **gmc said:**
> Hmm, I don't know if you saw this or not but it looks like you can install the jaunty version into karmic (if you can't wait for an official version).

[http://ubuntuforums.org/showthread.php?t=1274216](http://ubuntuforums.org/showthread.php?t=1274216)

G

I carried over the jaunty version when I upgraded, and it's working fine, except that the camera is always enabled at startup...

---

### Post by sprince09 on 2009-10-09
I was able to sort-of install the eee-control jaunty .deb in karmic. dpkg complained and said something or other failed to install, but I was able to start the daemon+applet. It seemed to work (fans got quiet, bluetooth toggled on/off, etc...), however after running it for a few hours I noticed some system instabilities which I think was related to eee-control, so I uninstalled it and am now waiting for the updated version :(

It would be awesome eee-control ended up in the repos... I've also tried the eee-applet package from universe, and it doesn't work at all on my EEE 1000, even in karmic.

---

