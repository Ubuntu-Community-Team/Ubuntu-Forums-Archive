---
title: "Installing Sip on Ubuntu 18.04: Fatal Error Python.h"
date: 2019-03-07
forum: Installation &amp; Upgrades
---

### Post by zak100 on 2019-03-07
I am trying to install SIP on Ubuntu 18.04. I have tried the following :
```


  	 	 	 	   
Commands to get, unpack and configure:
 cd /tmp/
wget "https://www.riverbankcomputing.com/static/Downloads/sip/sip-4.19.14.tar.gz"
tar -zxf sip-4.19.14.tar.gz
cd sip-4.19.14/
python configure.py
make  





```

 sudo make

 make[1]: Entering directory '/sip-4.19.14/sipgen'

 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o main.o main.c

 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o transform.o transform.c
 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o gencode.o gencode.c
 gencode.c: In function ‘generateNamedBaseType’:
 gencode.c:9565:23: warning: this statement may fall through [-Wimplicit-fallthrough=]
              nr_derefs = 1;

              ~~~~~~~~~~^~~

 gencode.c:9569:9: note: here

          case byte_type:
          ^~~~
 gencode.c:9627:23: warning: this statement may fall through [-Wimplicit-fallthrough=]
              nr_derefs = 1;
              ~~~~~~~~~~^~~
 gencode.c:9631:9: note: here

          case fake_void_type:

          ^~~~

 gencode.c: In function ‘generateCastZero’:

 gencode.c:7617:13: warning: this statement may fall through [-Wimplicit-fallthrough=]

              prcode(fp, "(%E)0", ed);

              ^~~~~~~~~~~~~~~~~~~~~~~

 gencode.c:7620:5: note: here

      case pyobject_type:
      ^~~~
 gencode.c: In function ‘generateTupleBuilder’:
 gencode.c:8720:16: warning: this statement may fall through [-Wimplicit-fallthrough=]
              if (copyConstRefArg(ad))
                 ^

 gencode.c:8728:9: note: here

          case fake_void_type:
          ^~~~
 gencode.c: In function ‘generateHandleResult’:
 gencode.c:12311:12: warning: this statement may fall through [-Wimplicit-fallthrough=]
          if (ad->u.ed->fqcname != NULL)
             ^

 gencode.c:12334:5: note: here

      case byte_type:
      ^~~~
 gencode.c: In function ‘generateVariableGetter’:
 gencode.c:5206:12: warning: this statement may fall through [-Wimplicit-fallthrough=]
          if (vd->type.u.ed->fqcname != NULL)
             ^

 gencode.c:5229:5: note: here

      case byte_type:

      ^~~~
 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o extracts.o extracts.c
 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o export.o export.c
 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o type_hints.o type_hints.c
 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o heap.o heap.c
 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o parser.o parser.c

 gcc -c -pipe -O2 -Wall -W -DNDEBUG -I. -o lexer.o lexer.c

 g++  -o sip main.o transform.o gencode.o extracts.o export.o type_hints.o heap.o parser.o lexer.o  
 make[1]: Leaving directory '/sip-4.19.14/sipgen'
 make[1]: Entering directory '/sip-4.19.14/siplib'
 gcc -c -pipe -fPIC -O2 -Wall -W -DNDEBUG -I. -I/usr/include/python2.7 -o siplib.o siplib.c
 siplib.c:20:10: fatal error: Python.h: No such file or directory
  #include <Python.h>

           ^~~~~~~~~~

 compilation terminated.
 Makefile:29: recipe for target 'siplib.o' failed
 make[1]: *** [siplib.o] Error 1
 make[1]: Leaving directory '/sip-4.19.14/siplib'
 Makefile:3: recipe for target 'all' failed
 make: *** [all] Error 2

  

I am error at make. Somebody please guide me.


Zulfi.

---

### Post by monkeybrain20122 on 2019-03-07
1) It failed because python.h is missing, and you need to install the package libpython2.7-dev from repo to get python.h

2) python-sip 4.19.7 (for python 2.7) is in the repository. Why do you build from source?( python2 is so old that it will be deprecated in Jan1 2020, PYPI no longer provides binary for sip, so pip install no longer works)

3)why sudo make? You don't need to invoke sudo in make, you only need to invoke sudo in make install if you need to write to a system directory (like /usr/local) This is an abuse of sudo that should be avoided.

4) if you are actually using python3 then simply 
```
sudo pip3 install -U sip
``` (for this you need to install python3-pip from repo)

---

