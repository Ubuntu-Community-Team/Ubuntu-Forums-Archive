---
title: "GCC 4.3 availability in Karmic?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by toopi on 2009-08-13
Does anyone know if gcc 4.3 will be included in Karmic for backward compatibilities with certain projects?  Can they even coexist on the same system?

---

### Post by taavikko on 2009-08-13
> **toopi said:**
> Does anyone know if gcc 4.3 will be included in Karmic for backward compatibilities with certain projects?  Can they even coexist on the same system?

```
 dpkg -l gcc-4.\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                            Version                                         Description
+++-===============================================-===============================================-==============================================================================================================
ii  gcc-4.3                                         4.3.4-1ubuntu1                                  The GNU C compiler
ii  gcc-4.3-base                                    4.3.4-1ubuntu1                                  The GNU Compiler Collection (base package)
un  gcc-4.3-doc                                     <none>                                          (no description available)
un  gcc-4.3-locales                                 <none>                                          (no description available)
un  gcc-4.3-multilib                                <none>                                          (no description available)
ii  gcc-4.4                                         4.4.1-1ubuntu3                                  The GNU C compiler
ii  gcc-4.4-base                                    4.4.1-1ubuntu3                                  The GNU Compiler Collection (base package)

```

---

### Post by slakkie on 2009-08-13
Yes, I even have 4.2.x installed.

```

dpkg -l | grep gcc
ii  gcc                                        4:4.4.0-3ubuntu1                           The GNU C compiler
ii  gcc-4.2                                    4.2.4-5ubuntu1                             The GNU C compiler
ii  gcc-4.2-base                               4.2.4-5ubuntu1                             The GNU Compiler Collection (base package)
ii  gcc-4.3                                    4.3.4-1ubuntu1                             The GNU C compiler
ii  gcc-4.3-base                               4.3.4-1ubuntu1                             The GNU Compiler Collection (base package)
ii  gcc-4.4                                    4.4.1-1ubuntu3                             The GNU C compiler
ii  gcc-4.4-base                               4.4.1-1ubuntu3                             The GNU Compiler Collection (base package)
ii  libgcc1                                    1:4.4.1-1ubuntu3                           GCC support library

```

---

### Post by toopi on 2009-08-13
Oh great.  Thanks for the confirmation guys.  That eases my mind greatly now.  :)

---

