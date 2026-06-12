---
title: "Help about Compiling Squid 3.1.11 on 11.10"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by project21 on 2012-01-31
i got some problem in installing squid 3.1.11 , here error report

libtool: compile:  g++ -DHAVE_CONFIG_H -I../.. -I../../include -I../../src -I../../include -I../../libltdl -I. -Wall -Wpointer-arith -Wwrite-strings -Wcomments -Werror -fhuge-objects -D_REENTRANT -g -O2 -MT User.lo -MD -MP -MF .deps/User.Tpo -c User.cc  -fPIC -DPIC -o .libs/User.o
g++: warning: switch '-fhuge-objects' is no longer supported
User.cc: In static member function 'static void AuthUser::CachedACLsReset()':
User.cc:161:17: error: variable 'username' set but not used [-Werror=unused-but-set-variable]
cc1plus: all warnings being treated as errors

make[3]: *** [User.lo] Error 1
make[3]: Leaving directory `/root/squid-3.1.11/src/auth'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/squid-3.1.11/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/squid-3.1.11/src'
make: *** [all-recursive] Error 1
root@kocok:~/squid-3.1.11#

anybody help me about this topic ? thanks before

---

### Post by MicVP on 2013-01-03
Hi,

I'm new to ubuntu. I'm compiling  Squid 3.1.10 on Ubuntu 12.04 LTS and got the same error as you stated. Have you solved this problem this time? Please help me. 

Thanks in advance. Happy New Year. :)

---

