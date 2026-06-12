---
title: "failed dependencies on USB dongle aksusbd rpm"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by jbaltrus on 2010-06-06
I am trying to install aksusbd-redhat-1.14-3.i386.rpm package that came with the proprietary software to activate the USB dongle for that software. When trying that I get failed dependencies:

cmrfocf@schedule-cmrf:/usr/spartan08.131_26_int9e/hasp/driver/HASP_SRM_LINUX_3.50_RedHat_RPM_R
un-time_Installer$ rpm -i "aksusbd-redhat-1.14-3.i386.rpm" --force-debian
error: Failed dependencies:
        /bin/sh is needed by aksusbd-redhat-1.14-3.i386
        chkconfig is needed by aksusbd-redhat-1.14-3.i386
        libc.so.6 is needed by aksusbd-redhat-1.14-3.i386
        libc.so.6(GLIBC_2.0) is needed by aksusbd-redhat-1.14-3.i386
        libc.so.6(GLIBC_2.1) is needed by aksusbd-redhat-1.14-3.i386
        libpthread.so.0 is needed by aksusbd-redhat-1.14-3.i386
        libpthread.so.0(GLIBC_2.0) is needed by aksusbd-redhat-1.14-3.i386
        libpthread.so.0(GLIBC_2.1) is needed by aksusbd-redhat-1.14-3.i386

What would be the easiest way to get all those taken care of? Can I install some random aksusbd package from somwhere on internet, package manager or apt-get so it installs it with all dependencies?

thanks

Jonas

---

