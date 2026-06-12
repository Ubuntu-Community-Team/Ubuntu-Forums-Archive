---
title: "Hydra installation help."
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2007-08-23
I'm taking some security and forensics classes at school and my instructor suggested a good site for us heavily interested in security. I checked out some linux programs, and after picking hydra and running a make install, this is what I get. What's up?


jason@jason:~/Desktop/hydra-5.4-src$ make install
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBPOSTGRES 
In file included from hydra-mod.h:8,
                 from hydra-vnc.c:10:
hydra.h:4:19: error: stdio.h: No such file or directory
hydra.h:5:20: error: string.h: No such file or directory
hydra.h:6:20: error: unistd.h: No such file or directory
hydra.h:7:20: error: stdlib.h: No such file or directory
hydra.h:8:20: error: signal.h: No such file or directory
hydra.h:10:21: error: strings.h: No such file or directory
hydra.h:11:18: error: time.h: No such file or directory
hydra.h:12:22: error: sys/time.h: No such file or directory
hydra.h:13:23: error: sys/types.h: No such file or directory
hydra.h:14:24: error: sys/socket.h: No such file or directory
hydra.h:15:19: error: netdb.h: No such file or directory
hydra.h:16:24: error: netinet/in.h: No such file or directory
hydra.h:17:23: error: arpa/inet.h: No such file or directory
hydra.h:18:19: error: fcntl.h: No such file or directory
hydra.h:19:19: error: ctype.h: No such file or directory
hydra.h:20:26: error: sys/resource.h: No such file or directory
hydra.h:21:22: error: sys/wait.h: No such file or directory
hydra.h:22:19: error: errno.h: No such file or directory
In file included from hydra-vnc.c:10:
hydra-mod.h:18: error: expected declaration specifiers or ‘...’ before ‘FILE’
hydra-mod.h:19: error: expected declaration specifiers or ‘...’ before ‘FILE’
hydra-mod.h:20: error: expected declaration specifiers or ‘...’ before ‘FILE’
hydra-vnc.c: In function ‘vncEncryptBytes’:
hydra-vnc.c:33: warning: implicit declaration of function ‘strlen’
hydra-vnc.c:33: warning: incompatible implicit declaration of built-in function ‘strlen’
hydra-vnc.c: At top level:
hydra-vnc.c:46: error: expected declaration specifiers or ‘...’ before ‘FILE’
hydra-vnc.c: In function ‘start_vnc’:
hydra-vnc.c:51: warning: incompatible implicit declaration of built-in function ‘strlen’
hydra-vnc.c:54: warning: implicit declaration of function ‘malloc’
hydra-vnc.c:54: warning: incompatible implicit declaration of built-in function ‘malloc’
hydra-vnc.c:58: warning: implicit declaration of function ‘recv’
hydra-vnc.c:65: warning: implicit declaration of function ‘fprintf’
hydra-vnc.c:65: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:65: error: ‘stderr’ undeclared (first use in this function)
hydra-vnc.c:65: error: (Each undeclared identifier is reported only once
hydra-vnc.c:65: error: for each function it appears in.)
hydra-vnc.c:70: warning: implicit declaration of function ‘exit’
hydra-vnc.c:70: warning: incompatible implicit declaration of built-in function ‘exit’
hydra-vnc.c:73: error: ‘fp’ undeclared (first use in this function)
hydra-vnc.c:74: error: ‘stdout’ undeclared (first use in this function)
hydra-vnc.c:99: warning: implicit declaration of function ‘free’
hydra-vnc.c:101: error: ‘NULL’ undeclared (first use in this function)
hydra-vnc.c:107: error: too many arguments to function ‘hydra_report_found_host’
hydra-vnc.c:110: warning: implicit declaration of function ‘memcmp’
hydra-vnc.c:122: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:124: warning: implicit declaration of function ‘sleep’
hydra-vnc.c: At top level:
hydra-vnc.c:136: error: expected declaration specifiers or ‘...’ before ‘FILE’
hydra-vnc.c: In function ‘service_vnc’:
hydra-vnc.c:162: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:162: error: ‘stderr’ undeclared (first use in this function)
hydra-vnc.c:162: warning: implicit declaration of function ‘getpid’
hydra-vnc.c:169: error: ‘NULL’ undeclared (first use in this function)
hydra-vnc.c:169: warning: implicit declaration of function ‘strncmp’
hydra-vnc.c:171: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:176: warning: incompatible implicit declaration of built-in function ‘exit’
hydra-vnc.c:180: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:186: warning: implicit declaration of function ‘strcmp’
hydra-vnc.c:188: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:190: warning: implicit declaration of function ‘strdup’
hydra-vnc.c:190: warning: incompatible implicit declaration of built-in function ‘strdup’
hydra-vnc.c:193: warning: incompatible implicit declaration of built-in function ‘strlen’
hydra-vnc.c:199: error: ‘fp’ undeclared (first use in this function)
hydra-vnc.c:199: error: too many arguments to function ‘start_vnc’
hydra-vnc.c:212: warning: incompatible implicit declaration of built-in function ‘fprintf’
hydra-vnc.c:217: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [hydra-vnc.o] Error 1
jason@jason:~/Desktop/hydra-5.4-src$

---

