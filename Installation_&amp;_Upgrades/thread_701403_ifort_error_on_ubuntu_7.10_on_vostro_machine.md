---
title: "ifort error on ubuntu 7.10 on vostro machine"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by yanyan on 2008-02-19
I installed intel fortran compiler 10.1.014 edition on my ubuntu 7.10 system on vestro machine.  The installation looks good and when I used
>ifort --version
ifort (IFORT) 10.1 20071116
Copyright (C) 1985-2007 Intel Corporation.  All rights reserved.

>icc --version
icc (ICC) 10.1 20080112
Copyright (C) 1985-2007 Intel Corporation.  All rights reserved.

So it should work. But when testing the ifort using a small helloworld.f90 program, it showed me following error message:
>ifort helloworld.f90
Unknown option: GLOB_diag_file
compilation aborted for helloworld.f90 (code 1)

following is the source code of helloworld.f90,
 PROGRAM HelloWorld
      PRINT *, "Hello World"
      END PROGRAM HelloWorld

When I copied the program to super computer and used ifort there to test the program, it can work well. So It is still related to the installation of my ifort on my machine. So where could be the problem? is there anyone suffering from the same problem? Thanks a lot.

---

### Post by yanyan on 2008-02-19
hi, I installed ifort10.1.014 again on my machine and the error message was gone when I tested helloworld.f90 program. So everything is fine now.

---

