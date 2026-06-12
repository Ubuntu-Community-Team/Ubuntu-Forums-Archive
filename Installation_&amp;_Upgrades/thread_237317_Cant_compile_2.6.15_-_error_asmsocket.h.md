---
title: "Cant compile 2.6.15 - error: asm/socket.h"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by bcalder01 on 2006-08-16
Hi all,
I'm trying to compile a custom 2.6.15 kernel. After generating my .config file using make menuconfig, I issued:

sudo make-kpg clean

then:

sudo make-kpg --initrd --append-to-version=-custom1 kernel_image

from which I get:
======================================================================
/usr/bin/make EXTRAVERSION=.7-ubuntu1-custom1   \
                                 ARCH=i386 oldconfig
make[1]: Entering directory `/usr/src/linux-source-2.6.15'
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [stamp-kernel-configure] Error 2
======================================================================
I seem to recall in the days of 2.4.x kernels, there was a phrase that needed to be commented out of a file in (I think) /usr/src/linux/include. Is this the case here?

Thanks in advance!

---

### Post by bcalder01 on 2006-08-20
**Gaah!** This is really frustrating!

I decided to compile a new kernel following the [ck patch thread]("http://www.ubuntuforums.org/showthread.php?t=84174&highlight=dapper+ck+patch") elsewhere. I've downloaded & patched a vanilla 2.6.15 kernel. When I run either **make xconfig** or **make menuconfig**, I am getting the same error as noted above:

==================================================================
bcalder@stitch:/usr/src/linux$ sudo make menuconfig
Password:
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

==================================================================

Any help greatly appreciated. I'm ready to kill my laptop!!

---

### Post by mlind on 2006-08-20
hmm. Do you have package called **linux-kernel-headers** installed (this has nothing to do with kernel headers actually, but that's another story..) ?
That package provides file */usr/include/asm/socket.h* which looks to be missing.

If you installed **build-essential** package, linux-kernel-headers should be installed too.

---

### Post by bcalder01 on 2006-08-20
Thanks much for the reply.

Yep, I've got **build-essential**, and therefore **linux-kernel-headers** installed. WTF? Way weird.

---

### Post by mlind on 2006-08-20
Does /usr/include/asm/socket.h file exist?

---

### Post by bcalder01 on 2006-08-21
It does **not!!**


bcalder@stitch:/usr/include$ ls -al |grep asm
lrwxrwxrwx  1 root root     26 2006-08-10 19:11 asm -> /usr/src/linux/include/asm
lrwxrwxrwx  1 root root     34 2006-08-10 19:11 asm-generic -> /usr/src/linux/include/asm-generic
drwxr-xr-x  2 root root     80 2006-05-26 10:56 asm-generic.pbackup
drwxr-xr-x 10 root root   3040 2006-05-26 10:56 asm-i386
drwxr-xr-x  2 root root   3288 2006-05-26 10:56 asm.pbackup
drwxr-xr-x  2 root root   2784 2006-05-26 10:56 asm-x86_64

Nor does it exist in /usr/src/linux/include:

bcalder@stitch:/usr/src/linux-source-2.6.15/include$ ls
acpi       asm-generic  asm-m68knommu  asm-sh       asm-x86_64  media   rxrpc
asm-alpha  asm-h8300    asm-mips       asm-sh64     asm-xtensa  mtd     scsi
asm-arm    asm-i386     asm-parisc     asm-sparc    cluster     net     sound
asm-arm26  asm-ia64     asm-powerpc    asm-sparc64  keys        pcmcia  video
asm-cris   asm-m32r     asm-ppc        asm-um       linux       prism2  wlan
asm-frv    asm-m68k     asm-s390       asm-v850     math-emu    rdma

So ... what do I need to modify??

---

### Post by bcalder01 on 2006-08-21
It does **not!!**


bcalder@stitch:/usr/include$ ls -al |grep asm
lrwxrwxrwx  1 root root     26 2006-08-10 19:11 asm -> /usr/src/linux/include/asm
lrwxrwxrwx  1 root root     34 2006-08-10 19:11 asm-generic -> /usr/src/linux/include/asm-generic
drwxr-xr-x  2 root root     80 2006-05-26 10:56 asm-generic.pbackup
drwxr-xr-x 10 root root   3040 2006-05-26 10:56 asm-i386
drwxr-xr-x  2 root root   3288 2006-05-26 10:56 asm.pbackup
drwxr-xr-x  2 root root   2784 2006-05-26 10:56 asm-x86_64

Nor does it exist in **/usr/src/linux/include**:

bcalder@stitch:/usr/src/linux-source-2.6.15/include$ ls
acpi       asm-generic  asm-m68knommu  asm-sh       asm-x86_64  media   rxrpc
asm-alpha  asm-h8300    asm-mips       asm-sh64     asm-xtensa  mtd     scsi
asm-arm    asm-i386     asm-parisc     asm-sparc    cluster     net     sound
asm-arm26  asm-ia64     asm-powerpc    asm-sparc64  keys        pcmcia  video
asm-cris   asm-m32r     asm-ppc        asm-um       linux       prism2  wlan
asm-frv    asm-m68k     asm-s390       asm-v850     math-emu    rdma

So ... what do I need to modify??

---

### Post by mlind on 2006-08-22
Remove (purge) & install should do it
```

sudo dpkg -P --force-depends linux-kernel-headers
sudo aptitude install linux-kernel-headers

```

But I think your search command is wrong, you should use
```

find /usr/include/ -name socket.h

```
or similar..

---

### Post by bcalder01 on 2006-08-24
Thanks, **mlind,** that did the trick. I'm compiling away!!

I appreciate the time you took to help me thru this - the Open Source community is a miracle!!

And yes, my search command was from outer space ...

---

