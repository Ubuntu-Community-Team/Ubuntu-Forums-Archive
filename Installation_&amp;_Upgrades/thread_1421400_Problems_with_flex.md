---
title: "Problems with flex?"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by larstr on 2010-03-04
Ubuntu 9.10, x86_x64

I'm currently trying to install a third party open source application called [FreeUSP](http://www.freeusp.org/). It looks like there's a problem with flex and I have tried using both flex-old and normal flex. I also have build-essential and bison installed.
```

$ make targets
Makefile:27: Linux/2.6/x86_64/GNU-4/included.files: No such file or directory
ccincl -I/opt/FreeUSP/trcgp/include -I. -r -o${TArchDir} ccincl.c ccincl_s.l > Linux/2.6/x86_64/GNU-4/included.files
/bin/sh: ccincl: not found
make: [Linux/2.6/x86_64/GNU-4/included.files] Error 127 (ignored)
gcc -DNO_RPC_SUPPORT -I/opt/FreeUSP/trcgp/include -I. -DGFORTRAN -D_FILE_OFFSET_BITS=64 -c -o Linux/2.6/x86_64/GNU-4/ccincl.o ccincl.c
ccincl.c: In function ‘main’:
ccincl.c:103: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:120: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:155: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:165: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:197: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:204: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c: In function ‘alteredfilename’:
ccincl.c:219: warning: incompatible implicit declaration of built-in function ‘strlen’
ccincl.c:221: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:224: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccincl.c:225: warning: incompatible implicit declaration of built-in function ‘strcat’
ccincl.c:227: warning: incompatible implicit declaration of built-in function ‘strcat’
ccincl.c:235: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c: In function ‘process’:
ccincl.c:242: warning: conflicting types for built-in function ‘malloc’
ccincl.c:301: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccincl.c:304: warning: incompatible implicit declaration of built-in function ‘strcat’
ccincl.c:307: warning: incompatible implicit declaration of built-in function ‘strcat’
ccincl.c:310: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccincl.c:311: warning: incompatible implicit declaration of built-in function ‘strcat’
ccincl.c:315: warning: incompatible implicit declaration of built-in function ‘strlen’
ccincl.c:317: warning: incompatible implicit declaration of built-in function ‘exit’
ccincl.c:357: warning: incompatible implicit declaration of built-in function ‘strlen’
ccincl.c:358: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccincl.c: In function ‘usage’:
ccincl.c:395: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -DNO_RPC_SUPPORT -I/opt/FreeUSP/trcgp/include -I. -DGFORTRAN -D_FILE_OFFSET_BITS=64 -c -o Linux/2.6/x86_64/GNU-4/ccincl_s.o ccincl_s.c
gcc -DNO_RPC_SUPPORT -L/opt/FreeUSP/trcgp/lib/Linux/2.6/x86_64/GNU-4 -DGFORTRAN -D_FILE_OFFSET_BITS=64 -o /opt/FreeUSP/trcgp/bin/Linux/2.6/x86_64/ccincl  Linux/2.6/x86_64/GNU-4/ccincl.o  Linux/2.6/x86_64/GNU-4/ccincl_s.o
Linux/2.6/x86_64/GNU-4/ccincl.o: In function `main':
ccincl.c:(.text+0x536): undefined reference to `yyin'
ccincl.c:(.text+0x53d): undefined reference to `yyin'
ccincl.c:(.text+0x592): undefined reference to `yylex'
ccincl.c:(.text+0x599): undefined reference to `yyin'
collect2: ld returned 1 exit status
make: *** [/opt/FreeUSP/trcgp/bin/Linux/2.6/x86_64/ccincl] Error 1


```

Any help would be appreciated.

Lars

---

