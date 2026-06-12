---
title: "Trying to compile plugin for kaffeine 0.8.2"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by py67 on 2006-10-28
During make I received this errors

sudo make
make  all-recursive
make[1]: Entering directory `/home/mira67/kaffeine-sc-plugin-0.2'
Making all in src
make[2]: Entering directory `/home/mira67/kaffeine-sc-plugin-0.2/src'
Making all in mgcam
make[3]: Entering directory `/home/mira67/kaffeine-sc-plugin-0.2/src/mgcam'
if /bin/bash ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -fasynchronous-unwind-tables -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT crypto.lo -MD -MP -MF ".deps/crypto.Tpo" -c -o crypto.lo crypto.cpp; \
        then mv -f ".deps/crypto.Tpo" ".deps/crypto.Plo"; else rm -f ".deps/crypto.Tpo"; exit 1; fi
crypto.cpp:24:27: error: asm/unaligned.h: No such file or directory
crypto.h:64: warning: unused parameter 'key7'
crypto.cpp: In member function 'void cDes::Des(unsigned char*, const unsigned char*, int) const':
crypto.cpp:312: error: 'get_unaligned' was not declared in this scope
crypto.cpp:313: error: 'get_unaligned' was not declared in this scope
crypto.cpp:314: error: 'get_unaligned' was not declared in this scope
crypto.cpp:315: error: 'get_unaligned' was not declared in this scope
crypto.cpp:336: error: 'put_unaligned' was not declared in this scope
make[3]: *** [crypto.lo] Error 1
make[3]: Leaving directory `/home/mira67/kaffeine-sc-plugin-0.2/src/mgcam'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mira67/kaffeine-sc-plugin-0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mira67/kaffeine-sc-plugin-0.2'
make: *** [all] Error 2


Source and headers kernel are installed. ](*,) ](*,) ](*,) ](*,)

---

### Post by chefweb on 2006-11-03
i have the same problem.. ./configure works fine but make is broken

Have you found a solution for this problem?

---

### Post by mtron on 2006-11-06
which version of the sc plugin are you using? Check that the right headers of your current kernel are installed.

if you are not sure, run "uname -a" from a terminal.
my output is: Linux workstation 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux
so i need the kernel-headers: linux-headers-2.6.15-27-k7
maybe it helps to run "export CPLUS_INCLUDE_PATH=/usr/src/linux/include" before compiling

you also need an unrestricted openssl version, get the source from [http://www.openssl.org/source/](http://www.openssl.org/source/)
but version 0.2.1 should fix the openssl issue

Please move this discussion to another forum! Cause the usage of this plugin is... you know what i talk about...

---

