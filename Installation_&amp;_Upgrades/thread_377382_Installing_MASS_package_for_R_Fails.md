---
title: "Installing MASS package for R Fails"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by dkatz on 2007-03-06
I installed R 2.4.1 sucessfully on the Dapper Drake, but the install.packages() fails for package MASS. The error msg is below and seems to have to do with missing headers. Anyone know how to fix this? maybe I need a lib argument? Thanks!

 install.packages()
Warning in install.packages() : argument 'lib' is missing: using /usr/local/lib/ R/site-library
trying URL 'http://cran.fhcrc.org/src/contrib/VR_7.2-32.tar.gz'
Content type 'application/x-gzip' length 462661 bytes
opened URL
==================================================
downloaded 451Kb

* Installing *source* package 'MASS' ...
** libs
gcc -std=gnu99 -I/usr/share/R/include -I/usr/share/R/include      -fpic  -g -O2 -c lqs.c -o lqs.o
In file included from lqs.c:33:
/usr/share/R/include/R.h:32:20: error: stdlib.h: No such file or directory
/usr/share/R/include/R.h:33:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from /usr/share/R/include/R.h:34,
                 from lqs.c:33:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122:61: error: limits.h: No s uch file or directory
In file included from lqs.c:33:
/usr/share/R/include/R.h:36:18: error: math.h: No such file or directory
In file included from /usr/share/R/include/R.h:49,
                 from lqs.c:33:
/usr/share/R/include/R_ext/RS.h:23:38: error: string.h: No such file or director y
lqs.c: In function ‘lqs_fitlots’:
lqs.c:224: warning: implicit declaration of function ‘fabs’
lqs.c:224: warning: incompatible implicit declaration of built-in function ‘fabs ’
lqs.c:240: warning: implicit declaration of function ‘sqrt’
lqs.c:240: warning: incompatible implicit declaration of built-in function ‘sqrt ’
lqs.c:241: warning: incompatible implicit declaration of built-in function ‘fabs ’
lqs.c: In function ‘do_one’:
lqs.c:321: warning: implicit declaration of function ‘log’
lqs.c:321: warning: incompatible implicit declaration of built-in function ‘log’
lqs.c:321: warning: incompatible implicit declaration of built-in function ‘fabs ’
lqs.c: In function ‘mve_fitlots’:
lqs.c:378: warning: incompatible implicit declaration of built-in function ‘log’
make: *** [lqs.o] Error 1
ERROR: compilation failed for package 'MASS'
** Removing '/usr/local/lib/R/site-library/MASS'
** Removing '/usr/local/lib/R/site-library/class'
** Removing '/usr/local/lib/R/site-library/nnet'
** Removing '/usr/local/lib/R/site-library/spatial'

The downloaded packages are in
        /tmp/Rtmp1uvPBL/downloaded_packages
Warning message:
installation of package 'VR' had non-zero exit status in: install.packages()
> install.packages()
Warning in install.packages() : argument 'lib' is missing: using /usr/local/lib/ R/site-library
trying URL 'http://cran.fhcrc.org/src/contrib/VR_7.2-32.tar.gz'
Content type 'application/x-gzip' length 462661 bytes
opened URL
==================================================
downloaded 451Kb

* Installing *source* package 'MASS' ...
** libs
gcc -std=gnu99 -I/usr/share/R/include -I/usr/share/R/include      -fpic  -g -O2 -c lqs.c -o lqs.o
In file included from lqs.c:33:
/usr/share/R/include/R.h:32:20: error: stdlib.h: No such file or directory
/usr/share/R/include/R.h:33:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from /usr/share/R/include/R.h:34,
                 from lqs.c:33:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122:61: error: limits.h: No s uch file or directory
In file included from lqs.c:33:
/usr/share/R/include/R.h:36:18: error: math.h: No such file or directory
In file included from /usr/share/R/include/R.h:49,
                 from lqs.c:33:
/usr/share/R/include/R_ext/RS.h:23:38: error: string.h: No such file or director y
lqs.c: In function ‘lqs_fitlots’:
lqs.c:224: warning: implicit declaration of function ‘fabs’
lqs.c:224: warning: incompatible implicit declaration of built-in function ‘fabs ’
lqs.c:240: warning: implicit declaration of function ‘sqrt’
lqs.c:240: warning: incompatible implicit declaration of built-in function ‘sqrt ’
lqs.c:241: warning: incompatible implicit declaration of built-in function ‘fabs ’
lqs.c: In function ‘do_one’:
lqs.c:321: warning: implicit declaration of function ‘log’
lqs.c:321: warning: incompatible implicit declaration of built-in function ‘log’
lqs.c:321: warning: incompatible implicit declaration of built-in function ‘fabs ’
lqs.c: In function ‘mve_fitlots’:
lqs.c:378: warning: incompatible implicit declaration of built-in function ‘log’
make: *** [lqs.o] Error 1
ERROR: compilation failed for package 'MASS'
** Removing '/usr/local/lib/R/site-library/MASS'
** Removing '/usr/local/lib/R/site-library/class'
** Removing '/usr/local/lib/R/site-library/nnet'
** Removing '/usr/local/lib/R/site-library/spatial'

The downloaded packages are in
        /tmp/Rtmp1uvPBL/downloaded_packages
Warning message:
installation of package 'VR' had non-zero exit status in: install.packages()
>

---

### Post by dkatz on 2007-03-06
I finally fixed this by installing gfortran, so this is closed.

---

