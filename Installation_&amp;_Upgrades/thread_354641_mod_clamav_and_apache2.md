---
title: "mod_clamav and apache2"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by betatux on 2007-02-06
Hi , 

I'm trying to install mod_clamav ([http://software.othello.ch/mod_clamav/](http://software.othello.ch/mod_clamav/)) on a system but I can't get it to compile :( , I can't find any info or help when I search for the compile error message on the internet so i'm trying my luck here.  Has anyone ever tried this module ?  Could anyone make the source package into an ubuntu package so it can be downloaded though means of Synaptic or apt-get ?

Below you find the compile error.

> 
bart@bart:~/Software/mod_clamav-0.21$ make
if /bin/bash ./libtool --mode=compile `/usr/bin/apxs2 -q CC` -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mod_clamav\" -DVERSION=\"0.21\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_MKSTEMP=1  -I. -I.  -I`/usr/bin/apxs2 -q INCLUDEDIR`  `/usr/bin/apxs2 -q CFLAGS_SHLIB` -g -O2 -MT mod_clamav_la-mod_clamav.lo -MD -MP -MF ".deps/mod_clamav_la-mod_clamav.Tpo" \
          -c -o mod_clamav_la-mod_clamav.lo `test -f 'mod_clamav.c' || echo './'`mod_clamav.c; \
        then mv -f ".deps/mod_clamav_la-mod_clamav.Tpo" ".deps/mod_clamav_la-mod_clamav.Plo"; \
        else rm -f ".deps/mod_clamav_la-mod_clamav.Tpo"; exit 1; \
        fi
mkdir .libs
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mod_clamav\" -DVERSION=\"0.21\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_MKSTEMP=1 -I. -I. -I/usr/include/apache2 -g -O2 -MT mod_clamav_la-mod_clamav.lo -MD -MP -MF .deps/mod_clamav_la-mod_clamav.Tpo -c mod_clamav.c  -fPIC -DPIC -o .libs/mod_clamav_la-mod_clamav.o
mod_clamav.c:151: error: expected specifier-qualifier-list before 'regex_t'
mod_clamav.c: In function 'clamav_safe_to_bypass':
mod_clamav.c:345: error: 'clamav_safeuri' has no member named 'matchtype'
mod_clamav.c:350: error: 'clamav_safeuri' has no member named 'regex'
mod_clamav.c:363: error: 'clamav_safeuri' has no member named 'regex'
mod_clamav.c: In function 'clamav_init_local':
mod_clamav.c:476: warning: assignment discards qualifiers from pointer target type
mod_clamav.c: In function 'clamav_add_safeuri':
mod_clamav.c:1986: error: 'regex_t' undeclared (first use in this function)
mod_clamav.c:1986: error: (Each undeclared identifier is reported only once
mod_clamav.c:1986: error: for each function it appears in.)
mod_clamav.c:1986: error: 'preg' undeclared (first use in this function)
mod_clamav.c:1997: error: 'clamav_safeuri' has no member named 'matchtype'
mod_clamav.c:1999: error: 'clamav_safeuri' has no member named 'matchtype'
mod_clamav.c:2004: error: 'REG_EXTENDED' undeclared (first use in this function)
mod_clamav.c:2010: error: 'clamav_safeuri' has no member named 'regex'
make: *** [mod_clamav_la-mod_clamav.lo] Error 1


Best Regards.

---

