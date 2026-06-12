---
title: "why can't I install  R package &quot;gam&quot; in Ubuntu 6.06"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by felixtandt on 2006-07-28
> install.packages("gam")
Warning in install.packages("gam") : argument 'lib' is missing: using /usr/local/lib/R/site-library
--- Please select a CRAN mirror for use in this session ---
Loading Tcl/Tk interface ... done
trying URL 'http://cran.cnr.Berkeley.edu/src/contrib/gam_0.97.tar.gz'
Content type 'application/x-gzip' length 89613 bytes
opened URL
==================================================
downloaded 87Kb

* Installing *source* package 'gam' ...
** libs
g77   -fpic  -g -O2 -c backfit.f -o backfit.o
g77   -fpic  -g -O2 -c backlo.f -o backlo.o
g77   -fpic  -g -O2 -c bsplvd.f -o bsplvd.o
g77   -fpic  -g -O2 -c bvalue.f -o bvalue.o
g77   -fpic  -g -O2 -c bvalus.f -o bvalus.o
g77   -fpic  -g -O2 -c linear.f -o linear.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c loessc.c -o loessc.o
g77   -fpic  -g -O2 -c loessf.f -o loessf.o
g77   -fpic  -g -O2 -c lo.f -o lo.o
g77   -fpic  -g -O2 -c qsbart.f -o qsbart.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c sbart.c -o sbart.o
g77   -fpic  -g -O2 -c sgram.f -o sgram.o
g77   -fpic  -g -O2 -c sinerp.f -o sinerp.o
g77   -fpic  -g -O2 -c splsm.f -o splsm.o
g77   -fpic  -g -O2 -c sslvrg.f -o sslvrg.o
g77   -fpic  -g -O2 -c stxwx.f -o stxwx.o
gcc -shared  -o gam.so backfit.o backlo.o bsplvd.o bvalue.o bvalus.o linear.o loessc.o loessf.o lo.o qsbart.o sbart.o sgram.o sinerp.o splsm.o sslvrg.o stxwx.o -lblas-3 -lg2c -lm -lgcc_s -L/usr/lib/R/lib -lR
[COLOR="Red"]/usr/bin/ld: cannot find -lblas-3
collect2: ld returned 1 exit status
make: *** [gam.so] Error 1
ERROR: compilation failed for package 'gam'[/COLOR]
** Removing '/usr/local/lib/R/site-library/gam'

The downloaded packages are in
        /tmp/RtmpQmwp2v/downloaded_packages
Warning message:
installation of package 'gam' had non-zero exit status in: install.packages("gam")

could some one help me?
many thanks.

---

### Post by cilynx on 2006-07-28
Doing an 'apt-cache search blas' returns (among many other things)
```

refblas3 - Basic Linear Algebra Subroutines 3, shared library
refblas3-dev - Basic Linear Algebra Subroutines 3, static library
lapack3-pic - library of linear algebra routines 3 - static PIC version
lapack3-test - library of linear algebra routines 3 - testing programs

```

Mayhaps install one or all of those would help.  Linear algebra sounds like something the R-pack would like.

Good Luck

---

### Post by felixtandt on 2006-07-29
Thank you very much. I solve the problem now.
1.to search Blas,
$ apt-cache search blas
2. to install the dependency package: refblas3-dev.
$ apt-get install refblas3-dev

---

