---
title: "Can't install THC Hydra"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Joinix on 2008-05-07
I know that many problems on installing THC Hydra has been posted, but i dont have the same problem.

When i have extracted the hydra-5.4-src.tar.gz folder, and CD'ed it. 
I type "./configure" as you should do, nothing goes wrong.

But when i type "make" it says: 

```

******@*******:~/Skrivbord/hydra-5.4-src$ make
gcc -I. -Wall -O2 -c hydra-sip.c  
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1


```
  
Does anyone know whats wrong, and how i can fix it?

---

### Post by omegamartyr on 2009-07-22
I have this same problem and I thought that it was just some libraries that hadn't been downloaded but am not sure.  Anyone got anything helpful to add?



***EDIT***
It says that it cannot find the openssl directory but it is there.  I have the latest version of openssl installed.

---

