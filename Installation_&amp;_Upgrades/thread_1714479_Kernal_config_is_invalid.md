---
title: "Kernal config is invalid"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by long813 on 2011-03-25
Hello all, 

I have been searching for this problem and have not come across any results that work. 

I'm running Ubuntu server 10.04, trying to install driver for a hardware encoder "ctr-1475".

When I run 'make' I get: 

```

make -C /lib/modules/2.6.32-30-generic/build/ SUBDIRS=/home/tacklebox/ctr1472 V=1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/tacklebox/ctr1472/.tmp_versions ; rm -f /home/tacklebox/ctr1472/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/tacklebox/ctr1472
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/tacklebox/ctr1472/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/tacklebox/ctr1472] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic'
make: *** [default] Error 2

```I have looked around and both, autoconf.h and auto.conf are in the right directory. 

When I run make oldconfig && make prepare, I also get an error:

```

 HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function â&#8364;&#732;conf_askvalueâ&#8364;&#8482;:
scripts/kconfig/conf.c:105: warning: ignoring return value of â&#8364;&#732;fgetsâ&#8364;&#8482;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function â&#8364;&#732;conf_choiceâ&#8364;&#8482;:
scripts/kconfig/conf.c:307: warning: ignoring return value of â&#8364;&#732;fgetsâ&#8364;&#8482;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#
scripts/kconfig/conf -s arch/x86/Kconfig

*** Error during update of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.

```I'm at a loss for what to try next to resolve these issues. Is this problem on my server? or could it be the company software?. I have emailed the company who provided me with the hardware & drivers, but as I wait, I am still looking for solutions. 

Cheers,

---

