---
title: "lirc modules on 2.6.37-12"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by fuzzyworbles on 2011-01-15
hey all,

I can't seem to figure out how to compile and install the lirc modules on the latest 2.6.37-12 kernel. this on on 10.04.1. when attempting to compile the modules, I get the following error:


> Error! Bad return status for module build on kernel: 2.6.37-12-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.6/build/ for more information.
dpkg: error processing lirc-modules-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 lirc-modules-sourceso I go ahead and check out the suggested log file, which reads in relevant part,

> make[3]: Entering directory `/usr/src/linux-headers-2.6.37-12-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (                \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo; so then, i follow those instructions, but alas the error i'm given here leaves me with no more suggestions:

> root@entertainment:/usr/src/linux-headers-2.6.37-12-generic# make oldconfig && make prepare
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
scripts/kconfig/conf --silentoldconfig Kconfig
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2does anybody have any idea about how to, like, produce a rule for kernel/bounds.s necessary to make said target?

thanks

---

### Post by L_V on 2011-02-28
Are you sure you need to compile anything related to lirc in ubuntu ?
I think no.

```
grep lirc /lib/modules/2.6.37-1-686/modules.symbols

alias symbol:lirc_dev_fop_poll lirc_dev
alias symbol:lirc_get_pdata lirc_dev
alias symbol:lirc_dev_fop_ioctl lirc_dev
alias symbol:lirc_dev_fop_write lirc_dev
alias symbol:lirc_unregister_driver lirc_dev
alias symbol:lirc_dev_fop_open lirc_dev
alias symbol:lirc_register_driver lirc_dev
alias symbol:lirc_dev_fop_close lirc_dev
alias symbol:lirc_dev_fop_read lirc_dev

```

---

