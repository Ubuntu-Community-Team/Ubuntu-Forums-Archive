---
title: "Having problem in installing systemc-2.1.v1"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by nirmesh2 on 2015-08-01
when i m installing i mgetting following error message 

cd .. && aclocal-1.14 
aclocal-1.14: warning: autoconf input should be named 'configure.ac', not 'configure.in'
aclocal-1.14: warning: 'configure.ac' and 'configure.in' both present.
aclocal-1.14: proceeding with 'configure.ac'
cd .. && \
      automake-1.14 --gnu  --ignore-deps Makefile
automake-1.14: warning: autoconf input should be named 'configure.ac', not 'configure.in'
automake-1.14: warning: 'configure.ac' and 'configure.in' both present.
automake-1.14: proceeding with 'configure.ac'
configure.ac:45: warning: AM_INIT_AUTOMAKE: two- and three-arguments forms are deprecated.  For more info, see:
configure.ac:45: [http://www.gnu.org/software/automake/manual/automake.html#Modernize-AM_005fINIT_005fAUTOMAKE-invocation](http://www.gnu.org/software/automake/manual/automake.html#Modernize-AM_005fINIT_005fAUTOMAKE-invocation)
configure.ac:47: error: required file 'config/compile' not found
configure.ac:47:   'automake --add-missing' can install 'compile'
make: *** [../Makefile.in] Error 1


Should i make change in configure.ac??

---

### Post by bapoumba on 2015-08-01
*Thread moved to **Installation & Upgrades**.*

---

