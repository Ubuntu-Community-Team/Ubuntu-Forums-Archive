---
title: "linking problem during installation"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by greenawy on 2015-10-29
I'm trying to install a certain software that requires LAPACk package, I already installed it and specified its path, during installation I get the error message /usr/bin/ld can not find liblapack.
I tried to set the path by using export LD_LIBRARY_PATH and adding the path into /etc.ld.so.conf but it didn't work!
Could you please help me?

---

### Post by steeldriver on 2015-10-29
Exactly what LAPACK package did you install, and how? how did you "specify its path"? What are you trying to install and what are the instructions that you are following?

---

### Post by greenawy on 2015-10-29
I will post it

---

### Post by greenawy on 2015-10-29
I am using Ubuntu 14.04 so the package in the repository is Lapack 3.5.0 and I installed it using Synaptic Package Manager
Lapack libraries are in /usr/lib.
During the installation of the code (s3 that needs Netcdf, Boost and Lapack) it gives the following error:

/usr/bin/ld: cannot find -lliblapack.a:liblapack.so:liblapack.so.3
/usr/bin/ld: cannot find -llibblas.a
/usr/bin/ld: cannot find -llibblas.so
/usr/bin/ld: cannot find -llibblas.so.3
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lliblapack.a:liblapack.so:liblapack.so.3
/usr/bin/ld: cannot find -llibblas.a
/usr/bin/ld: cannot find -llibblas.so
/usr/bin/ld: cannot find -llibblas.so.3
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lliblapack.a:liblapack.so:liblapack.so.3
/usr/bin/ld: cannot find -llibblas.a
/usr/bin/ld: cannot find -llibblas.so
/usr/bin/ld: cannot find -llibblas.so.3
collect2: error: ld returned 1 exit status
make[3]: *** [tds] Error 1

---

### Post by ubfan1 on 2015-10-29
Looks like the liblapack.a ... libraries got installed into /usr/lib/lapack instead of /usr/lib.  Try adjusting the s3 code to add that to its search path.

---

### Post by greenawy on 2015-10-29
My problem is very similar to this thread [http://ubuntuforums.org/showthread.php?t=2105701](http://ubuntuforums.org/showthread.php?t=2105701)
but in my case I want it to be linked to /usr/bin/ld
Any suggestions?
thank you

---

### Post by ubfan1 on 2015-10-29
/usr/bin/ld is the link-loader program.  What path did you add to the /etc/ld.so.conf (/usr/lib/lapack?)?  Where exactly did synaptic install the libraries, (if not in /usr/lib/lapack where the package install puts them)? In the link you gave, the problem was misnaming the libraries by including an extra "lib" on the parameter, that's not your problem.

---

### Post by greenawy on 2015-10-29
Synaptic installed the libraries in /usr/lib (and not in specific folders like /usr/lib/libblas or /usr/lib/lapack).
I added this path to [COLOR=#000000] /etc/ld.so.conf  but same error comes out.
what should I do? 
Do I have to change the make file? How?[/COLOR]

---

### Post by ubfan1 on 2015-10-30
Oops, bad eyes here.  The names do appear to have the "lib" included in them.  Now the colon in the name spec says "use this exactname (don't add 'lib')".  Maybe colon is missing after the -l:liblapack.so ?   Either use -llapack  or -l:liblapack.so  (including any special path works too).  To change the build, edit the makefile for the library paths (or the configure file which the package uses to build the makefile).

---

