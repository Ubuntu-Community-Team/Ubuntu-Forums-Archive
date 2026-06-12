---
title: "Nids module wont working"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by gombodorj2 on 2014-10-18
during install pynids there are some error text appeared and i am sucked.

  


sudo python setup.py build
running build
running build_ext
building 'nidsmodule' extension
x86_64-linux-gnu-gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -Ilibnids-1.24/src -I/usr/local/include -I/opt/local/include -I/usr/include/python2.7 -c nidsmodule.c -o build/temp.linux-x86_64-2.7/nidsmodule.o
In file included from nidsmodule.c:29:0:
libnids-1.24/src/nids.h:119:3: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
   void (*syslog) ();
   ^
libnids-1.24/src/nids.h:125:3: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
   int (*ip_filter) ();
   ^
nidsmodule.c: In function ‘hs_get_urgdata’:
nidsmodule.c:385:10: warning: pointer targets in passing argument 1 of ‘PyString_FromStringAndSize’ differ in signedness [-Wpointer-sign]
          sizeof(self->hlfs->urgdata));
          ^
In file included from /usr/include/python2.7/Python.h:94:0,
                 from nidsmodule.c:23:
/usr/include/python2.7/stringobject.h:62:24: note: expected ‘const char *’ but argument is of type ‘u_char *’
 PyAPI_FUNC(PyObject *) PyString_FromStringAndSize(const char *, Py_ssize_t);
                        ^
x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -D_FORTIFY_SOURCE=2 -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security build/temp.linux-x86_64-2.7/nidsmodule.o libnids-1.24/src/libnids.a -L/usr/local/lib -L/opt/local/lib -lpcap -lnet -lglib-2.0 -lgthread-2.0 -o build/lib.linux-x86_64-2.7/nidsmodule.so
/usr/bin/ld: libnids-1.24/src/libnids.a(libnids.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
libnids-1.24/src/libnids.a: error adding symbols: Bad value
collect2: error: ld returned 1 exit status
error: command 'x86_64-linux-gnu-gcc' failed with exit status 1

---

