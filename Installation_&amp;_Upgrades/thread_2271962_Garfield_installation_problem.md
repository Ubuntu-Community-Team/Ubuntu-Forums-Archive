---
title: "Garfield installation problem"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by varun9 on 2015-04-03
Hi,

I am trying to install Garfield . I have a 64 bit macine. OS is Ubuntu !4.04.

I am Getting Following Error:

 FCASPLIT executing.
             Input file : garfadd-9.f
           Shell script : garfadd-9.shfca
              Make file : garfadd-9.mkfca
        Fortran    name : gfortran  
        Fortran options : -c -g -O2 -fno-automatic  
             CC    name : gcc  
             CC options : -c -g -O2  
      Assembler    name : as  
      Assembler options :   
At line 786 of file /build/buildd/cernlib-20061220+dfsg3/src/patchy/fcasplit.F (unit = 11, file = '')
Fortran runtime error: File 'garfadd-9.f' does not exist
make: *** [main-9.f] Error 2


Thanks .

[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

---

### Post by dino99 on 2015-04-03
an old thread about it: [http://ubuntuforums.org/showthread.php?t=1636834&page=5](http://ubuntuforums.org/showthread.php?t=1636834&page=5)

your error:  File 'garfadd-9.f' does not exist
the solution: [https://cbm-wiki.gsi.de/foswiki/bin/view/Homepages/CernlibFlorianUhlig](https://cbm-wiki.gsi.de/foswiki/bin/view/Homepages/CernlibFlorianUhlig)

---

### Post by varun9 on 2015-04-04
Hi 9d9,

Thanks for replying.

I am following your link to installation fortran based cern software. After making lapck directory and making build directory, cmake is not working .

As i give command  cmake .. to run cmake , it gives following error:-
CMake Error: The source directory "/tmp/cern" does not appear to contain CMakeLists.txt.

I do not understand It.

Ps : cmake was not installed on my system earlier . I have installed it before running cmake.

---

### Post by varun9 on 2015-04-06
Hi 9d9,

I am following your link to Install lapack , blas and cernlib package.

[https://cbm-wiki.gsi.de/foswiki/bin/...ibFlorianUhlig]("https://cbm-wiki.gsi.de/foswiki/bin/view/Homepages/CernlibFlorianUhlig")

Lapack and Blas libraries are installed. But during Cernlib installation at step


Before we can start to build the Cernlib we have to build one binary first which is needed by man targets.    gmake bin/kuipc
 If the binary kuips is found in your path, you can start to build the complete project.    make -j<number_of_processes>


I get the following error:-gmake[3]: Entering directory `/tmp/cern/pawlib/paw/uimx'
gmake[3]: Nothing to be done for `archive/objects.list'.
gmake[3]: Leaving directory `/tmp/cern/pawlib/paw/uimx'
In file included from /usr/include/X11/Xft/Xft.h:40:0,
                 from /usr/include/Xm/TextFP.h:34,
                 from /tmp/cern/2006/src/pawlib/paw/xbae/cellp.h:40,
                 from /tmp/cern/2006/src/pawlib/paw/xbae/cell.c:38:
/usr/include/freetype.h:33:28: fatal error: config/ftconfig.h: No such file or directory
 #include FT_CONFIG_CONFIG_H
                            ^
compilation terminated.
gmake[3]: *** [archive/cell.o] Error 1
gmake[3]: Leaving directory `/tmp/cern/pawlib/paw/xbae'
gmake[2]: *** [xbae/archive/objects.list] Error 2
gmake[2]: Leaving directory `/tmp/cern/pawlib/paw'
gmake[1]: *** [paw/archive/objects.list] Error 2
gmake[1]: Leaving directory `/tmp/cern/pawlib'
make: *** [install.lib] Error 2


can you help in this ?

Thanks in Advance.

---

