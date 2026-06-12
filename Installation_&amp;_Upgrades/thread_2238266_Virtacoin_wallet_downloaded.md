---
title: "Virtacoin wallet downloaded"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by palacequeen55 on 2014-08-06
A few days ago I downloaded a virtacoin wallet from github. The problem is, I cant get it to install.
Does anyone know how to install a wallet in ubuntu 14.04? Would I have to install it in terminal?
The website doesnt help in giving instruction on how to do this.
Thanks

---

### Post by claracc on 2014-08-07
As far as I know you have downloaded a .zip file which is a source software, I suppose it from this web page: [https://github.com/virtacoin/VirtaCoinProject](https://github.com/virtacoin/VirtaCoinProject), so you have to compile to install and run it.

Here you have a guide to compile from source: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by mcbelisle on 2014-10-11
got this error:
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')

---

### Post by Vladlenin5000 on 2014-10-11
Instruction here: [https://github.com/virtacoin/VirtaCoinProject/blob/master/doc/build-unix.md](https://github.com/virtacoin/VirtaCoinProject/blob/master/doc/build-unix.md)
Make sure you have all the listed dependencies _before_ running the scripts.

---

### Post by mcbelisle on 2014-10-26
installed dependencies
had to do chmod+x autogen.sh
then got these errors:

onfigure.ac:119: installing 'src/build-aux/compile'
configure.ac:12: installing 'src/build-aux/config.guess'
configure.ac:12: installing 'src/build-aux/config.sub'
configure.ac:37: installing 'src/build-aux/install-sh'
configure.ac:37: installing 'src/build-aux/missing'
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
src/Makefile.am: installing 'src/build-aux/depcomp'
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
parallel-tests: installing 'src/build-aux/test-driver'
configure.ac:699: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')

now doing the "make" command

got this error:
/bin/bash: ../share/genbuild.sh: Permission denied
Makefile:1169: recipe for target 'obj/build.h' failed
make[3]: *** [obj/build.h] Error 126
make[3]: Leaving directory '/home/michael/Downloads/VirtaCoinProject-master/src'
Makefile:834: recipe for target 'all-recursive' failed
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/michael/Downloads/VirtaCoinProject-master/src'
Makefile:638: recipe for target 'all' failed
make[1]: *** [all] Error 2
make[1]: Leaving directory '/home/michael/Downloads/VirtaCoinProject-master/src'
Makefile:494: recipe for target 'all-recursive' failed
make: *** [all-recursive] Error 1

---

### Post by Vladlenin5000 on 2014-10-26
Please contact the software developers.

---

