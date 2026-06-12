---
title: "VMware-server-1.0.2-39867.i386.rpm but cant install it."
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by Cool Surfer on 2007-09-08
I downloaded **VMware-server-1.0.2-39867.i386.rpm but cant install it.**
How do I do it. Need to install windows in ubuntu.

---

### Post by Cool Surfer on 2007-09-08
I get the error archive type not supported. :(

---

### Post by Cool Surfer on 2007-09-08
some one pl reply, I am waiting for instructions  :(

---

### Post by Cool Surfer on 2007-09-08
getting this error on running insall .pl file

[i]
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.[/i]

how to rectify it pl.

---

### Post by Phrawm48 on 2007-09-14
For Feisty (7.04), VMware Server 1.0.3 build-44356.

I was receiving exactly the same Feisty-VMware Server errors as *Cool Surfer* and resolved the problem as follows.

I did a Web search and found, inter alia, this page:

[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

That page pointed me to this list of VMware files:

[http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/)

I used the link on that page to download *vmware-any-any-update113.tar.gz*.

**NOTE**: Check the page for the most current version.  For example, the VMware community post (first URL) cited version *109*, but as of today (14 September, 2007) I was able to download version *113*.

Unzip the patch, open the patch's folder in a terminal window, and run:

```
sudo ./runme.pl

```*runme.pl* appears to be an updated version of the VMware installation script.  (So have your VMware registration key handy...)  The script walked me through the VMware Server installation process; this time, however, installation was successful...

Cheers & hope this helps,
Ric
SFO

---

### Post by Pumalite on 2007-09-14
The thing is RPM's are not used in Ubuntu.

---

