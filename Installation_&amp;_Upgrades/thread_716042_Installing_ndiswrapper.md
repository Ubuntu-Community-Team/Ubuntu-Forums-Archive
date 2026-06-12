---
title: "Installing ndiswrapper"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by hecter on 2008-03-05
I've been trying to get my wireless network card working with ndiswrapper, but I can't seem to install it :( When ever I try, I just get this big slew of errors. I got as far as extracting it. I've tried what was said here:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
but, again, I just got a big slew of errors and warnings. I'm running a dual boot with Vista, so please help! I don't wanna use vista any more...

---

### Post by Pumalite on 2008-03-05
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by hecter on 2008-03-08
Trust me, I've tried all that. It just don't wanna work. Here's my terminal:
```
isaac@Isaac-B:~$ tar xvzf ndiswrapper-1.48.tar.gz
ndiswrapper-1.48/
ndiswrapper-1.48/AUTHORS
ndiswrapper-1.48/ChangeLog
ndiswrapper-1.48/INSTALL
ndiswrapper-1.48/Makefile
ndiswrapper-1.48/README
ndiswrapper-1.48/ndiswrapper.spec
ndiswrapper-1.48/ndiswrapper.8
ndiswrapper-1.48/loadndisdriver.8
ndiswrapper-1.48/utils/
ndiswrapper-1.48/utils/Makefile
ndiswrapper-1.48/utils/ndiswrapper
ndiswrapper-1.48/utils/loadndisdriver.c
ndiswrapper-1.48/utils/ndiswrapper-buginfo
ndiswrapper-1.48/driver/
ndiswrapper-1.48/driver/divdi3.c
ndiswrapper-1.48/driver/hal.c
ndiswrapper-1.48/driver/iw_ndis.c
ndiswrapper-1.48/driver/iw_ndis.h
ndiswrapper-1.48/driver/loader.c
ndiswrapper-1.48/driver/loader.h
ndiswrapper-1.48/driver/longlong.h
ndiswrapper-1.48/driver/Makefile
ndiswrapper-1.48/driver/crt.c
ndiswrapper-1.48/driver/ndis.c
ndiswrapper-1.48/driver/ndis.h
ndiswrapper-1.48/driver/ndiswrapper.h
ndiswrapper-1.48/driver/ntoskernel.c
ndiswrapper-1.48/driver/ntoskernel.h
ndiswrapper-1.48/driver/ntoskernel_io.c
ndiswrapper-1.48/driver/pe_linker.c
ndiswrapper-1.48/driver/pe_linker.h
ndiswrapper-1.48/driver/pnp.c
ndiswrapper-1.48/driver/pnp.h
ndiswrapper-1.48/driver/proc.c
ndiswrapper-1.48/driver/rtl.c
ndiswrapper-1.48/driver/usb.c
ndiswrapper-1.48/driver/usb.h
ndiswrapper-1.48/driver/winnt_types.h
ndiswrapper-1.48/driver/workqueue.c
ndiswrapper-1.48/driver/wrapmem.h
ndiswrapper-1.48/driver/wrapmem.c
ndiswrapper-1.48/driver/wrapper.c
ndiswrapper-1.48/driver/wrapndis.h
ndiswrapper-1.48/driver/wrapndis.c
ndiswrapper-1.48/driver/lin2win.h
ndiswrapper-1.48/driver/win2lin_stubs.S
isaac@Isaac-B:~$ cd ndiswrapper-1.48
isaac@Isaac-B:~/ndiswrapper-1.48$ make distclean
make -C driver clean
make[1]: Entering directory `/home/isaac/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/isaac/ndiswrapper-1.48/driver'
make -C utils clean
make[1]: Entering directory `/home/isaac/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/isaac/ndiswrapper-1.48/utils'
rm -f *~
rm -fr ndiswrapper-1.48 ndiswrapper-1.48.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/isaac/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/isaac/ndiswrapper-1.48/driver'
make -C utils distclean
make[1]: Entering directory `/home/isaac/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/isaac/ndiswrapper-1.48/utils'
rm -f .\#*
isaac@Isaac-B:~/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/isaac/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/isaac/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/isaac/ndiswrapper-1.48/driver/built-in.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/crt.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/hal.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/iw_ndis.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/loader.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/ndis.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/ntoskernel.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/ntoskernel_io.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/pe_linker.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/pnp.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/proc.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/rtl.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/wrapmem.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/wrapndis.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/wrapper.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/usb.o
  CC [M]  /home/isaac/ndiswrapper-1.48/driver/divdi3.o
  LD [M]  /home/isaac/ndiswrapper-1.48/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/isaac/ndiswrapper-1.48/driver/ndiswrapper.mod.o
  LD [M]  /home/isaac/ndiswrapper-1.48/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/isaac/ndiswrapper-1.48/driver'
make -C utils
make[1]: Entering directory `/home/isaac/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/isaac/ndiswrapper-1.48/utils'
make: *** [all] Error 2
isaac@Isaac-B:~/ndiswrapper-1.48$ 
```
I told you, a slew of errors. Did I do something wrong? I've tried just "make install" rather than "sudo make install" as well with the same results.

---

### Post by Pumalite on 2008-03-09
I assume you have build-essential installed.
sudo aptitude install build-essential

---

### Post by khmer04sti on 2008-03-09
I ran into the same problem when I was installing v1.52 (using Gutsy). What I ended up doing was manually installing utils (v1.9) and common before installing ndiswrapper. It's worked fine after that.

I didn't have an active net connection via my Gutsy rig so I downloaded the packages separately from [here]("http://packages.ubuntu.com/gutsy/ndiswrapper-utils-1.9") (utils v1.9) and [here]("http://packages.ubuntu.com/gutsy/ndiswrapper-common") (common).

---

### Post by hecter on 2008-03-21
Sorry for the late bump... Perhaps I should clarify what I have:
I have Ubuntu 7.04 installed.

That about covers it... I don't have anything special done with it, no extra programs, nothing. I don't even have the Ubuntu disc. No internet connection while using Ubuntu, nothing. No matter what I do I always get those damn error messages that I posted above. I have no prior experience with any linux OS, so I also have no idea what I'm doing. All I know is that I don't have internet and that I really want off of Vista and making Linux my main OS. All that I'm asking of you is this: Please help me break my dependency from Steve Jobs and Bill Gates!

I should also note that I don't know any of the commands or what they do. You say manual install I say "Huh?" When I put in "sudo aptitude install build-essential" I just got a big list of commands and then "Super cow is not installed" or something like that at the bottom.

I'd like to finish this by saying that I'm not a complete idiot, just a big one. :)

---

### Post by Pumalite on 2008-03-21
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)

---

### Post by dstew on 2008-03-21
You have been trying to compile ndiswrapper from the source code. You don't need to do that. The Ubuntu developers have already compiled it for you, and put into a Debian package. After you get the packages, install them with```
sudo dpkg -i *filename.deb*
```So, do what khmer04sti said. Download the Ubuntu ndiswrapper packages on another computer, transfer then to your Ubuntu machine with a thumb drive or CD-ROM, and install them.

Another way to go for installing packages if you do not have an internet connection is to use the [nonetdebs]("http://nonetdebs.homeip.net/") service. Nonetdebs is good for doing whole upgrades.

---

### Post by hecter on 2008-03-21
> **Pumalite said:**
> [http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
That doesn't help. That tells me quite literally absolutely nothing. You need to actually explain things. Just posting a bunch of cryptic links doesn't help me at all.
> **dstew said:**
> You have been trying to compile ndiswrapper from the source code. You don't need to do that. The Ubuntu developers have already compiled it for you, and put into a Debian package. After you get the packages, install them with```
sudo dpkg -i *filename.deb*
```So, do what khmer04sti said. Download the Ubuntu ndiswrapper packages on another computer, transfer then to your Ubuntu machine with a thumb drive or CD-ROM, and install them.

Another way to go for installing packages if you do not have an internet connection is to use the [nonetdebs]("http://nonetdebs.homeip.net/") service. Nonetdebs is good for doing whole upgrades.
ndiswrapper didn't come in a .deb package, it can in a .tar.gz thing, and when I extracted it it made a folder in my home folder that contained more folders.

---

### Post by Pumalite on 2008-03-21
The links are for you to read and learn before complain.

---

### Post by dstew on 2008-03-21
> ndiswrapper didn't come in a .deb packageHere is the [ndiswrapper-common]("http://packages.ubuntu.com/feisty/ndiswrapper-common") and [ndiswrapper-utils]("http://packages.ubuntu.com/feisty/ndiswrapper-utils-1.9") Debian packages for you to download.

---

### Post by hecter on 2008-03-21
Ya, those, I finally figured this whole thing out! I got those installed and they seem to be working. However! I went and tried to install my inf file, and it didn't work. When ever I check the list, it says "Invalid Driver". When I try to uninstall it (ndiswrapper -e bcmwl5) it doesn't do anything and the driver is still there. I can't reinstall it either.

---

### Post by dstew on 2008-03-22
What card do you have? Post the output of ```
lspci -n
```. What driver did you download? What is the output of ```
ndiswrapper -l
```To remove a driver, I believe the command is```
ndiswrapper -r *driver*
```You might need sudo to run the ndiswrapper commands.

---

### Post by hecter on 2008-03-25
ndiswrapper -r driver gave me an invalid command, when I put in ndiswrapper -e driver (which is says is supposed to remove said driver) it just goes to another line where I input commands and the driver is still there. I can't post any output yet as I have another issue, though...

---

### Post by dstew on 2008-03-25
Please post back when you get your issue solved, I am willing to help you try this. It would be helpful to see the output of lspci and ndiswrapper -l. By the way, you probably need to use sudo with your ndiswrapper configuration commands. That is, ```
sudo ndiswrapper -i bcmwl5.inf
```to install.

---

### Post by solaceinsilence9 on 2008-03-25
try this command:

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common

Of course I used this with Gutsy Gibbon not Feisty Fawn so Im not sure if it will work. But its worth a shot.

---

### Post by hecter on 2008-03-28
> **dstew said:**
> Please post back when you get your issue solved, I am willing to help you try this. It would be helpful to see the output of lspci and ndiswrapper -l. By the way, you probably need to use sudo with your ndiswrapper configuration commands. That is, ```
sudo ndiswrapper -i bcmwl5.inf
```to install.
Well, I've got a GUI again, so I've got the things you've asked for...
```
isaac@Isaac-B:~$ lspci -n
00:00.0 0600: 1002:7910
00:02.0 0604: 1002:7913
00:07.0 0604: 1002:7917
00:12.0 0106: 1002:4380
00:13.0 0c03: 1002:4387
00:13.1 0c03: 1002:4388
00:13.2 0c03: 1002:4389
00:13.3 0c03: 1002:438a
00:13.4 0c03: 1002:438b
00:13.5 0c03: 1002:4386
00:14.0 0c05: 1002:4385 (rev 14)
00:14.1 0101: 1002:438c
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:438d
00:14.4 0604: 1002:4384
00:18.0 0600: 1022:1200
00:18.1 0600: 1022:1201
00:18.2 0600: 1022:1202
00:18.3 0600: 1022:1203
00:18.4 0600: 1022:1204
01:00.0 0300: 10de:0622 (rev a1)
02:00.0 0200: 11ab:4364 (rev 20)
03:01.0 0280: 14e4:4329 (rev 01)
03:06.0 0c00: 104c:8024
```


```
isaac@Isaac-B:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
isaac@Isaac-B:~$ sudo ndiswrapper -e bcmwl5
Password:
isaac@Isaac-B:~$ sudo ndiswrapper -r bcmwl5
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
```
That's correct, right? IT's what you wanted?

---

### Post by dstew on 2008-03-29
Post the output of```
lspci
```Together with the lspci -n output that should tell us exactly what card you have. Then we can check to see if you have the correct windows driver. Where did you get the windows driver?

---

### Post by hecter on 2008-03-29
```
isaac@Isaac-B:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:02.0 PCI bridge: ATI Technologies Inc Unknown device 7913
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Unknown device 1200
00:18.1 Host bridge: Advanced Micro Devices [AMD] Unknown device 1201
00:18.2 Host bridge: Advanced Micro Devices [AMD] Unknown device 1202
00:18.3 Host bridge: Advanced Micro Devices [AMD] Unknown device 1203
00:18.4 Host bridge: Advanced Micro Devices [AMD] Unknown device 1204
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0622 (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 20)
03:01.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
isaac@Isaac-B:~$ 
```
I got the drivers off the disk, but I think I might have forgotten to copy a file...

---

### Post by hecter on 2008-03-29
Alright, so I uninstalled ndiswrapper and reinstalled it, then tried to reinstall bcmwl5 (sudo ndiswrapper -i bcmwl5.inf) and now I'm at the same place as before. One interesting note though; it told me it had "No Vendor". Maybe you can figure something out with that...

---

### Post by dstew on 2008-03-29
So just for reference, you have a Broadcom Corporation BCM43XG (rev 01), with a PCI ID of 14e4:4329 (rev 01). I could not find out which driver is best for that card (you could call it a 4329). Apparently all BCM 43xx drivers use the bcmwl5.inf script for installation, but use different system files. See the [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"), you download the specific driver package for your card, then do sudo ndiswrapper bcmwl5.inf. You have to have the correct .sys file in the directory in order for the .inf script to work correctly. So, what is the name of the .sys file you are using?

If you get the .sys file(s) from a Windows disk, you might have to change the names to lower case to get them to install correctly. Sometimes the driver files have upper case names, but the .inf uses lower case. On a Windows system, this doesn't matter, but in Linux, names are case-sensitive. The .sys file names have to match the case of the names used in the .inf file.

EDIT: In one case, the .sys file(s) had to be hand-copied to the driver directory in /etc/ndiswrapper. It was also a case-sensitivity problem, so I don't know if changing the case before ndiswrapper -i will solve this.

---

### Post by rizitis on 2008-05-24
for bcm4329 look here
[http://ubuntuforums.org/showthread.php?t=805631](http://ubuntuforums.org/showthread.php?t=805631)

---

