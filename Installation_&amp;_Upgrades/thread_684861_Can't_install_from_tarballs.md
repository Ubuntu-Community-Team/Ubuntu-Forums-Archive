---
title: "Can't install from tarballs"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by spiritfox on 2008-02-01
I have had this problem repeatedly with installing from tarballs.
I download the tarball and extract it with no problem.  When I run ./configure, I get the is error message in the terminal:
```

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```
and when i look in config.log, I see this or something similar:

```
configure:2827: checking for C compiler default output file name
configure:2854: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2857: $? = 1
configure:2895: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "murrine"
| #define PACKAGE_TARNAME "murrine"
| #define PACKAGE_VERSION "0.53.1"
| #define PACKAGE_STRING "murrine 0.53.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "murrine"
| #define VERSION "0.53.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2902: error: C compiler cannot create executables
See `config.log' for more details.
```

I assume that this is the problematic section because it ends in the error message i received.  Is this a problem with gcc?

---

### Post by kellemes on 2008-02-01
Install [B]build-essential
[/B]

---

### Post by spiritfox on 2008-02-01
Now on some of the programs I was trying to install I get a different error:

checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

something else I need to install?

---

