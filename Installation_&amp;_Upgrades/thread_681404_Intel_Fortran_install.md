---
title: "Intel Fortran install"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by drewa on 2008-01-28
I'm trying to put Intel Fortran 10.0.026 on a 32 bit Gutsy Gibbon Dell laptop.  I get to this point where I think that things start to go south

\****************************************************************************
Installation package for IA-32.
.....Checking Dependencies ...
Checking operating system requirements .............................
Unable to determine specific operating system / distribution
Checking RPM version ...Checking Kernel and glibc dependencies ...

Your platform   :
    architecture      = i686
    kernel            = 2.6.22-14-generic
    glibc             = unknown
    operating system  = unknown

This product is supported for use with the following combinations   :

    Machine Type                        Kernel  glibc

    IA-32/Intel(R) 64                   2.4.x   2.2.5
    IA-32/Intel(R) 64                   2.4.x   2.2.93
    IA-32/Intel(R) 64                   2.4.x   2.3.2
    IA-32/Intel(R) 64                   2.6.x   2.3.x
    IA-32/Intel(R) 64                   2.6.x   2.4.x
    IA-32/Intel(R) 64                   2.6.x   2.5.x

Would you like to perform an unsupported install of this product [yes/no]  (no) ?   :
****************************************************************************

I try to do it with the unsupported install and it ends up crapping out here:

****************************************************************************
--------------------------------------------------------------------------------
Intel(R) Fortran Compiler for applications running on IA-32, Version 10.0 (10.0.026)
Installing...
Installation failed.
--------------------------------------------------------------------------------


RPM std error output is as follows:

--------------------------------------------------------------------
error: Failed dependencies:
        /bin/bash is needed by intel-ifort100026-10.0.026-1.i386
        /bin/sh is needed by intel-ifort100026-10.0.026-1.i386
        libc.so.6 is needed by intel-ifort100026-10.0.026-1.i386
        libc.so.6(GLIBC_2.0) is needed by intel-ifort100026-10.0.026-1.i386
        libc.so.6(GLIBC_2.1) is needed by intel-ifort100026-10.0.026-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by intel-ifort100026-10.0.026-1.i386
        libc.so.6(GLIBC_2.2) is needed by intel-ifort100026-10.0.026-1.i386
        libc.so.6(GLIBC_2.3) is needed by intel-ifort100026-10.0.026-1.i386
        libdl.so.2 is needed by intel-ifort100026-10.0.026-1.i386
        libdl.so.2(GLIBC_2.0) is needed by intel-ifort100026-10.0.026-1.i386
        libdl.so.2(GLIBC_2.1) is needed by intel-ifort100026-10.0.026-1.i386
        libgcc_s.so.1 is needed by intel-ifort100026-10.0.026-1.i386
        libgcc_s.so.1(GCC_3.0) is needed by intel-ifort100026-10.0.026-1.i386
        libgcc_s.so.1(GLIBC_2.0) is needed by intel-ifort100026-10.0.026-1.i386
        libm.so.6 is needed by intel-ifort100026-10.0.026-1.i386
        libpthread.so.0 is needed by intel-ifort100026-10.0.026-1.i386
        libpthread.so.0(GLIBC_2.0) is needed by intel-ifort100026-10.0.026-1.i386
        libpthread.so.0(GLIBC_2.1) is needed by intel-ifort100026-10.0.026-1.i386
        libpthread.so.0(GLIBC_2.2) is needed by intel-ifort100026-10.0.026-1.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by intel-ifort100026-10.0.026-1.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by intel-ifort100026-10.0.026-1.i386
        libstdc++.so.5 is needed by intel-ifort100026-10.0.026-1.i386
        libstdc++.so.5(GLIBCPP_3.2) is needed by intel-ifort100026-10.0.026-1.i386
--------------------------------------------------------------------

This failure occured using the following RPM options:
    -U --replacefiles --force


-------- WARNING ---------

This is an RPM ERROR CONDITION apparently caused by a dependency problem.
You can choose to retry the RPM installation with dependency enforcement disabled,
and retry the RPM installation using the '--nodeps' option.
This dependency problem will still need to be resolved after the installation,
in order for the software to function properly.

Do you wish to retry the installation with this option? [yes/no] (no) :

****************************************************************************
What package do I need to install to get past this hangup?  Thanks for the help!

---

### Post by Partyboi2 on 2008-01-29
what guide are you using to install with? If you are trying to install a rpm file you will need to convert it with a package called alien.

---

### Post by drewa on 2008-01-29
The file I got from Intel is just a tar.gz file.  I installed **sudo apt-get install rpm build-essential** but it didn't help out.  I'm at a loss.

---

### Post by Partyboi2 on 2008-01-30
Sorry I am not sure how to get around the problem you are having. Have you looked at some other programs like [g77]("http://www.gnu.org/software/fortran/fortran.html")
or
[gfortran]("http://gcc.gnu.org/fortran/")
You can install them by
```
 sudo apt-get install g77
```
```
 sudo apt-get install gfortran
```
If not maybe someone else might know the solution.

---

