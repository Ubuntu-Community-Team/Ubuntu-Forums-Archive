---
title: "56k modem problem"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by dado on 2005-02-17
I have softk56 modem on my PC
i have downloaded drivers and i have run installer.
and in the end i get this message

Assuming that a C compiler and proper kernel header files are present
on your system, we will now attempt to re-compile the modules.

Where is the directory of C header files that match your running kernel?
[/usr/src/linux]

what should i do next please help me!

---

### Post by az on 2005-02-17
It is referring to your kernel headers.  The package is linux-headers.

So you would install the corresponding linux-headers package and then use whatever directory:

/usr/src/linux-headers-2.6.8.1-4-386


Also, be sure that you have the 'build-essential' package installed.

---

### Post by dado on 2005-02-18
root@ubuntu:/home/dado # hsfconfig
Linux HSF softmodem drivers, version 4.06.06.02
grep: /proc/ksyms: No such file or directory
/usr/sbin/hsfconfig: line 99: [: too many arguments

No pre-built HSF modules are available for your exact kernel:
                Linux-2.6.8.1-3-386-i686-Debian-testing/unstable

Assuming that a C compiler and proper kernel header files are present
on your system, we will now attempt to re-compile the modules.

Where is the directory of C header files that match your running kernel?
[/usr/src/linux] /usr/src/linux-headers-2.6.10-3-386
/usr/sbin/hsfconfig: line 1: gcc: command not found

WARNING: the kernel version () defined in
/usr/src/linux-headers-2.6.10-3-386/include/linux/version.h
does not match the currently running kernel (2.6.8.1-3-386)
The cause of this problem is an incorrect kernel source path.
Please check that /usr/src/linux-headers-2.6.10-3-386 points to the right tree.The cause of this problem is usually a missing or misconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).
/usr/sbin/hsfconfig: line 1: gcc: command not found

Re-compiling HSF modules for kernel , using source directory
/usr/src/linux-headers-2.6.10-3-386. Please wait..

ERROR: Module re-compilation and installation failed!
Please examine the log file "/tmp/hsfconfig-recomp.log.4470" to determine why.
root@ubuntu:/home/dado #

and this is log file:
/bin/sh: line 1: gcc: command not found
/bin/sh: line 1: gcc: command not found
/bin/sh: line 1: gcc: command not found
rm -f *.o
/bin/sh: line 1: gcc: command not found
make[1]: Entering directory `/usr/lib/hsf/modules/osspec'
rm -f *.o
make[1]: Leaving directory `/usr/lib/hsf/modules/osspec'
/bin/sh: line 1: gcc: command not found
Unable to determine version of kernel source directory /usr/src/linux-headers-2.6.10-3-386
make: *** [check_kernelver] Error 1

but when installing headers i get this



root@ubuntu:/home/dado/Desktop/LINUX HEADERS # sudo dpkg -i linux-headers-2.6.10-3-386_2.6.10-19_i386.deb
(Reading database ... 71165 files and directories currently installed.)
Preparing to replace linux-headers-2.6.10-3-386 2.6.10-19 (using linux-headers-2.6.10-3-386_2.6.10-19_i386.deb) ...
Unpacking replacement linux-headers-2.6.10-3-386 ...
dpkg: dependency problems prevent configuration of linux-headers-2.6.10-3-386:
 linux-headers-2.6.10-3-386 depends on linux-headers-2.6.10-3; however:
  Package linux-headers-2.6.10-3 is not installed.
dpkg: error processing linux-headers-2.6.10-3-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.10-3-386
root@ubuntu:/home/dado/Desktop/LINUX HEADERS #



please help me!

---

### Post by az on 2005-02-18
linux-headers-2.6.10-3-386

Wrong package.

It has to match your kernel.

---

### Post by dado on 2005-02-18
Now please can you tell me where can i find this?
i have v4.10 Ubuntu
i haven't change anything and i am beginer
what all should i have installed to it seems that i must have g++ and gcc what versions and where(do I have this on my Ubuntu CD?
thank you very much!
and I am sorry for my bad English!

---

