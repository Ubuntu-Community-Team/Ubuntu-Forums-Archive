---
title: "libexosip2 not available from repositories? install error"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by anilp on 2011-08-01
I could not find libeXosip2 3.5 - perhaps it is not available in Synaptic package manager on my ubuntu (10.10).
I downloaded it libexosip2-3.5 from [http://download.savannah.gnu.org/releases/exosip/](http://download.savannah.gnu.org/releases/exosip/) and tried to build

   $> ./configure
   $> make

libtool: link: gcc -g -pthread -DOSIP_MT -pedantic -DENABLE_DEBUG -g -DENABLE_TRACE -g -o .libs/sip_reg sip_reg.o  ../src/.libs/libeXosip2.so -L/usr/local/lib /usr/lib/libosip2.so /usr/lib/libosipparser2.so -lnsl -lrt -lresolv -pthread
../src/.libs/libeXosip2.so: undefined reference to `osip_strcasestr'
collect2: ld returned 1 exit status
make[2]: *** [sip_reg] Error 1
make[2]: Leaving directory `/home/anil/Downloads/libeXosip2-3.5.0/tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/anil/Downloads/libeXosip2-3.5.0'
make: *** [all] Error 2

Any help appreciated.
Anil

---

### Post by owennewo on 2011-08-12
I had the same error.  

libexosip depends on libosip.  I'm guessing you will need to do what I did.  remove the repository version of libosip and download and compile osip as well as exosip.

source for osip v 3.5.0 from [http://ftp.gnu.org/gnu/osip/?C=M;O=D](http://ftp.gnu.org/gnu/osip/?C=M;O=D)

---

