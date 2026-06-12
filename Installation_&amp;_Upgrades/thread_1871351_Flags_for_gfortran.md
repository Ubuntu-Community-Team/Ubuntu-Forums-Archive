---
title: "Flags for gfortran"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by neelesh28 on 2011-10-28
Hi,

I am new to Ubuntu. I am trying to compile a program using a makefile with not much success. I am unable to find the correct gfortran flags for the program. I tried the following flags
**FFLAGS= -ffixed-line-length-none -c -J ${MODLOC} -I.**
and I get the following error message

---------------------------------------------
Warning: initialization string truncated to match variable at (1)
EACO.EXT:36.15:
    Included at gamma_etc.f:256:

     &       / 'A_3CAR            ', 0.2        , 5            /
               1
Warning: initialization string truncated to match variable at (1)
gamma_etc.f:573.26:

      END MODULE GAMMA_etc
                          1
Fatal Error: Can't open module file '-I./gamma_etc.mod0' for writing at (1): No such file or directory
make: *** [gamma_etc.o] Error 1
------------------------------------------------
Any help in identifying correct gfortran flags will be highly appreciated.

Thanks.
Neelesh

---

