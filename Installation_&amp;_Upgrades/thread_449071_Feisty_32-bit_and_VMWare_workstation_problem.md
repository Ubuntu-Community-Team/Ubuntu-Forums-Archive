---
title: "Feisty 32-bit and VMWare workstation problem"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Malibyte on 2007-05-19
Hi all -

I recently decided to clean up my old laptop's HDD and installed 32-bit Kubuntu Feisty on it; I'm just running the stock kernel at this time (2.6.20-15-generic).

Workstation 5.5.3 had been working OK on Mandrake 10.2 on this machine previously.

I was able to get 5.5.4 to compile and install after using the any-any-110 patch.  However, even AFTER running vmware-config.pl and going through all of the networking options, etc. and compilation/installation of the kernel modules:

```

root@r2d2:/usr/local/bin# find /* -name vmmon*
/dev/vmmon
/dev/.udev/names/vmmon
/lib/modules/2.6.20-15-generic/misc/vmmon.ko
/lib/modules/2.6.20-15-generic/misc/vmmon.o
/sys/module/vmmon
/sys/class/misc/vmmon

root@r2d2:/usr/local# find /* -name vmnet*
/dev/vmnet2
/dev/vmnet0
/lib/modules/2.6.20-15-generic/misc/vmnet.ko
/lib/modules/2.6.20-15-generic/misc/vmnet.o
/proc/vmnet
/sys/module/vmnet

```

it still won't run...even after running vmware-config.pl AGAIN, I still get:

```

[rcs@r2d2: ~]$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/local/bin/vmware-config.pl.

```

I searched this on this forum and the VMware support forum but didn't find a fix...thanks to anyone who can help with this.

Bob

---

### Post by tormentum on 2007-05-20
I had no problems installing 5.5.3, 5.5.4 or the new 6.0 release.  As far as I know, you only need to use the any-any patch on the VMware Server releases.  All the VMware workstation builds install _unmodified_ without incident and version 6.0 does not even need any install time kernel module compiling.

I'd probably try uninstalling VMware using vmware-uninstall.pl, then run "/etc/cron.daily/find" as root to update your locate database.  Then run "locate vmware" to find and manually delete any vmware files left behind.  After your system is VMware-clean, try installing again.

The only hiccup I had under feisty was that if you run the install script as root like this "./vmware-install.pl" instead of "perl ./vmware-install.pl", it would give a security error and exit.

---

### Post by bhaskar on 2007-05-20
Below is what I encounter when installing unmodified VMWare (VMware-workstation-5.5.4-44386.tar.gz) with perl ./vmware-install.pl (it's pretty much the same result if I do sudo ./vmware-install.pl) on a straight Kubuntu Feisty Fawn 7.04 that is current with patches.  What I am doing differently?  TIA for any help.

Regards
-- Bhaskar

---------------------------------------
<...snip...>

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â...â before âcompat_exitâ
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â...â before âexit_codeâ
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to âintâ in declaration of â_syscall1â
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
---------------------------------------

---

### Post by Malibyte on 2007-05-20
That was what I got before I applied the any-any patch.  Now, I can get it to compile, but still can't get it to run (see first post).

---

### Post by Malibyte on 2007-05-21
I got it fixed.  For some reason, there was a  file called /etc/vmware/not-configured which wasn't getting deleted by the config script.  I deleted it myself, now it's working.  :)

---

