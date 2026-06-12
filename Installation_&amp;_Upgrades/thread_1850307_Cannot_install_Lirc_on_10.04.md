---
title: "Cannot install Lirc on 10.04"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by mac666 on 2011-09-26
Hello
I have kernel 2.6.38-10-generic on ubuntu 10.04
I have installed headers for my kernel.
I upgrade my kernel recently and after that i cannot use lirc.
I have tried to purge lirc and reinstall it:


```
dj@diskoteket:~$ sudo apt-get install lirc
[sudo] password for dj:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  lirc-modules-source lirc-x
The following NEW packages will be installed:
  lirc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/589kB of archives.
After this operation, 2,572kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package lirc.
(Reading database ... 179465 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.8.6-0ubuntu4.2_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for hal ...
Regenerating hal fdi cache ...
Processing triggers for man-db ...
Setting up lirc (0.8.6-0ubuntu4.2) ...
ls: cannot access /lib/modules/2.6.38-10-generic/kernel/ubuntu/lirc/: No such file or directory
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

As you see i dont have /lib/modules/2.6.38-10-generic/kernel/ubuntu/lirc/

When i try to install lirc-modules-source:
```

dj@diskoteket:~$ sudo apt-get install lirc-modules-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  kernel-source
The following NEW packages will be installed:
  lirc-modules-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/273kB of archives.
After this operation, 1,204kB of additional disk space will be used.
Selecting previously deselected package lirc-modules-source.
(Reading database ... 179744 files and directories currently installed.)
Unpacking lirc-modules-source (from .../lirc-modules-source_0.8.6-0ubuntu4.2_all.deb) ...
Setting up lirc-modules-source (0.8.6-0ubuntu4.2) ...
Loading new lirc-0.8.6 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-10-generic
Building for architecture x86_64
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.6/build/ for more information.
dpkg: error processing lirc-modules-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 lirc-modules-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The log says:
```
dj@diskoteket:~$ cat /var/lib/dkms/lirc/0.8.6/build/make.log
DKMS make.log for lirc-0.8.6 for kernel 2.6.38-10-generic (x86_64)
Mon Sep 26 14:07:00 CEST 2011
mkdir modules
make -C drivers SUBDIRS="lirc_dev"
make[1]: Entering directory `/var/lib/dkms/lirc/0.8.6/build/drivers'
Making all in lirc_dev
make[2]: Entering directory `/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make[2]: [lirc_dev.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
        make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[3]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (       \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/.tmp_versions ; rm -f /var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev
  gcc -Wp,-MD,/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -I/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/ -I/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/../.. -I/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/../.. -I/lib/modules/2.6.38-10-generic/build/include/ -I/lib/modules/2.6.38-10-generic/build/drivers/media/video/  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/.tmp_lirc_dev.o /var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c:35:28: error: linux/autoconf.h: No such file or directory
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c: In function âlirc_register_driverâ:
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c:302: error: âstruct file_operationsâ has no member named âioctlâ
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c: In function âirctl_ioctlâ:
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c:676: error: âstruct file_operationsâ has no member named âioctlâ
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c:677: error: âstruct file_operationsâ has no member named âioctlâ
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c: At top level:
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c:952: error: unknown field âioctlâ specified in initializer
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.c:952: warning: initialization from incompatible pointer type
make[4]: *** [/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev/lirc_dev.o] Error 1
make[3]: *** [_module_/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make[2]: *** [lirc_dev.o] Error 2
make[2]: Leaving directory `/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_dev'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/lib/dkms/lirc/0.8.6/build/drivers'
make: *** [dev] Error 2

```

If i remove / purge lirc and everything with it, then reboot, i still have lirc in dmesg:

```
dj@diskoteket:~$ dmesg | grep lirc
[    3.429833] lirc_dev: IR Remote Control driver registered, major 250
[    3.434886] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0

```

dpkg-reconfigure says that lirc-modules-source is broken or incomplete. 

Any ideas? please? Thank you..!

---

### Post by vinterkind on 2011-09-26
> cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory

Well, you really seem to miss a few files.
Do you have another kernel to boot (some fallback) ?

2.6.38 is no default kernel for ubuntu 10.04. Did you build it up yourself ?

If you get the sources of lirc, you could build it up manually. 
Why ```
apt-get install
``` ?

---

### Post by mac666 on 2011-09-26
> **vinterkind said:**
> Well, you really seem to miss a few files.
Do you have another kernel to boot (some fallback) ?

2.6.38 is no default kernel for ubuntu 10.04. Did you build it up yourself ?

If you get the sources of lirc, you could build it up manually. 
Why ```
apt-get install
``` ?

Hello
I got the kernel from apt-get. 
What kernel is the latest for ubuntu 10.04 ?
I had problems with my networkcard, but in this kernel it works... but now lirc doesnt work :/

---

### Post by vinterkind on 2011-09-26
Well normally only the ubuntu kernel has a /lib/modules/<kv>/kernel/ubuntu directory.

But you're right. 
I've seen the linux-image-2.6.38-10-generic kernel. I'll install it and try the same.

My default kernel for 10.04 is 2.6.32-33-generic via the last update.

---

### Post by mac666 on 2011-09-26
> **vinterkind said:**
> Well normally only the ubuntu kernel has a /lib/modules/<kv>/kernel/ubuntu directory.

But you're right. 
I've seen the linux-image-2.6.38-10-generic kernel. I'll install it and try the same.

My default kernel for 10.04 is 2.6.32-33-generic via the last update.

Yes, i had this kernel too. i can still boot into it. 
Dunno how lirc works in that kernel now, only have ssh to the pc atm. 
Please do install it and try out lirc!

---

### Post by vinterkind on 2011-09-26
Ok. Installation went well.

Installed kernel and headers, but there is definitely no "lirc" directory in /lib/modules.
I'll reboot and give it a try.

---

### Post by vinterkind on 2011-09-26
What an Odyssey :-)

I've upgraded to Kernel 2.6.38-10-generic and the first thing to do is to get the 
nvidia driver from nvidia, because the ubuntu-version doesn't install ;)

Ok. But lirc.

I've copied the lirc-folder from /lib/modules/2.6.32-33-generic to /lib/modules/2.6.38-10-generic

```
cp -r /lib/modules/2.6.32-33-generic/kernel/ubuntu/lirc /lib/modules/2.6.38-10-generic/kernel/ubuntu
```

and installed it again with.

```
apt-get install --reinstall lirc
```

then I created the pid directory

```
mkdir /var/run/lirc
```

and started the daemon. so far it worked.

---

### Post by mac666 on 2011-09-26
> **vinterkind said:**
> What an Odyssey :-)

I've upgraded to Kernel 2.6.38-10-generic and the first thing to do is to get the 
nvidia driver from nvidia, because the ubuntu-version doesn't install ;)

Ok. But lirc.

I've copied the lirc-folder from /lib/modules/2.6.32-33-generic to /lib/modules/2.6.38-10-generic

```
cp -r /lib/modules/2.6.32-33-generic/kernel/ubuntu/lirc /lib/modules/2.6.38-10-generic/kernel/ubuntu
```

and installed it again with.

```
apt-get install --reinstall lirc
```

then I created the pid directory

```
mkdir /var/run/lirc
```

and started the daemon. so far it worked.

Ive tried to copy them allready, not working. 
I think it might have something to do with lirc-modules-source,
i cant remove it! 
Any suggestions?

Edit: after purging everything and rebooting, then install lirc:
i get this error:
Setting up lirc (0.8.6-0ubuntu4.2) ...
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

---

### Post by vinterkind on 2011-09-26
try 

```
dpkg -P 
```

on the sources.
what does it say ?

---

### Post by mac666 on 2011-09-26
its says that lirc-modules-source isnt installed, thats good i guess. 
However,
when i try to use irw i get no output ( asked my girl at home to press on the remote :-) )
Any ideas?

---

### Post by vinterkind on 2011-09-26
> its says that lirc-modules-source isnt installed, thats good i guess. 

Jeg tror det.. ;)
Well I think too, that's good. If you invoke

```
dpkg -C 
```and there is no output, your packages are all right. (it's the audit command).

irw without output is better, than no connection to socket ;)

Sorrily I've got no remote here. So I'm out here.
What you could try is a trace

```
strace -e open irw
```maybe that helps.

---

### Post by mac666 on 2011-09-26
> **vinterkind said:**
> Jeg tror det.. ;)
Well I think too, that's good. If you invoke

```
dpkg -C 
```and there is no output, your packages are all right. (it's the audit command).

irw without output is better, than no connection to socket ;)

Sorrily I've got no remote here. So I'm out here.
What you could try is a trace

```
strace -e open irw
```maybe that helps.

Output: 
[sudo] password for dj:
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libc.so.6", O_RDONLY)        = 3

tried to dpkc --configure lirc-modules-source
and i get Error! Bad return status for module build on kernel: 2.6.38-10-generic (x86_64)
It must have something to do with this!

---

### Post by vinterkind on 2011-09-27
Have you tried to reinstall it, and then remove it ?

```
apt-get install --reinstall lirc-modules-source
apt-get purge lirc-modules-source
```

and you haven't had any output with dpkg -C ??

---

### Post by vinterkind on 2011-09-27
Since I've got VirtualBox, I found another thing.
The headers I've installed are just 2.6.38.7. So it complained about it while building the dkms modules.

First I've missed the "linux" link on my sources (/usr/src/linux)
then a

```
 head -n4 Makefile
```

showed that it isn't 2.6.38.10-generic ...
That is one problem that bugged my builds.

> Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-10-generic -C /lib/modules/2.6.38-10-generic/build M=/var/lib/dkms/vboxhost/4.0.2/build....(bad exit status: 2)
0
0
Failed to install using DKMS, attempting to install without
Makefile:178: *** Error: /usr/src/linux (version 2.6.38.7) does not match the current kernel (version 2.6.38-10-generic).

---

