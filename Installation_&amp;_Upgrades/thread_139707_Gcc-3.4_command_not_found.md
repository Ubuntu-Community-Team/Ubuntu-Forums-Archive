---
title: "Gcc-3.4: command not found"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by benskiedra on 2006-03-04
Hello everybody,

I'm trying to make my AccessRunner DSL PCI modem work in Ubuntu... This is the part of the process...

benskis@beno:~$ cd /root/
benskis@beno:/root$ dir
CnxADSL-6.1.2.007-PIM-2.6-1.3  dbootstrap_settings
CnxADSL-6.1.2.007-PIM-2.6-1.4  Desktop
benskis@beno:/root$ cd CnxADSL-6.1.2.007-PIM-2.6-1.4
benskis@beno:/root/CnxADSL-6.1.2.007-PIM-2.6-1.4$ make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[3]: gcc-3.4: Command not found
make[3]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o
/bin/sh: gcc-3.4: command not found
make[4]: *** [/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o] Error 127
make[3]: *** [_module_/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: *** [CnxADSL.ko] Error 2
make[2]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make: *** [all] Error 2
benskis@beno:/root/CnxADSL-6.1.2.007-PIM-2.6-1.4$


What should I do to remove those errors?

---

### Post by kaamos on 2006-03-04
Install the needed version
```
sudo apt-get install gcc-3.4
```
You need an Internet connection for this though. So you could write down what packages would be installed and download them from packages.ubuntu.com and transfer to the machine where gcc 3.4 is needed.

---

### Post by benskiedra on 2006-03-04
Made it. But as soon as I've done that this is what I get:

benas@ubuntu:/root/CnxADSL-6.1.2.007-PIM-2.6-1.3$ make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/ARMAbstract.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/BufMgmt.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardAL.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALADSLDiag.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALBdDp.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALBd.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALTigris.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALTigrisDiag.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALTigrisLC.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardMgmt.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardMgmtLink.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardMgmtVc.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CellDataTest.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CellDataTestMgmt.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/ChipALBusCtlP46.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/ChipALCdsl.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/ChipALDMAChanP46.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/ChipALIoP46.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALTigrisDp.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CardALTigrisHal.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/ChipALSEmw.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CnxTTY.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/FrameAl.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/FrameALAAL.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/FrameALATM.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/FrameALATMOAM.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/FrameALATMShaper.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/FrameALHec.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/KThread.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/LnxTools.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/SmLnxIf.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/SmSysIf.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/UtilStr.o
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/UtilTmr.o
  LD [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CnxADSL.o
  Building modules, stage 2.
  MODPOST
[COLOR="Red"]Warning: could not find /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/.dpcont roller.o.new.cmd for /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/dpcontroll er.o.new[/COLOR]
  CC      /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CnxADSL.mod.o
  LD [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/CnxADSL.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/DownLoadApp'
cc -DCPU=486 -march=i486 -DUTS_MACHINE='"i386"' -c -Wall -O -I/usr/include -I. - I../ -I../KernelModule -M *.c > .depend
/bin/sh: cc: command not found
make[1]: *** [.depend] Error 127
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/DownLoadApp'
make: *** [all] Error 2
benas@ubuntu:/root/CnxADSL-6.1.2.007-PIM-2.6-1.3$

-----

This error: Warning: could not find /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/.dpcont roller.o.new.cmd for /root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule/dpcontroll er.o.new . I thought I could make a correction like copying dpcontroller.o.new. and renaming the copy to .dpcontroller.o.new. :) Done so. Then I launch make again and get:

benas@ubuntu:~$ sudo gedit
benas@ubuntu:~$ cd /root
benas@ubuntu:/root$ cd CnxADSL-6.1.2.007-PIM-2.6-1.3/
benas@ubuntu:/root/CnxADSL-6.1.2.007-PIM-2.6-1.3$ make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[2]: `CnxADSL.ko' is up to date.
make[2]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/DownLoadApp'
cc -DCPU=486 -march=i486 -DUTS_MACHINE='"i386"' -c -Wall -O -I/usr/include -I. -I../ -I../KernelModule   -c -o cnxadslload.o cnxadslload.c
make[1]: cc: Command not found
make[1]: *** [cnxadslload.o] Error 127
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/DownLoadApp'
make: *** [all] Error 2
benas@ubuntu:/root/CnxADSL-6.1.2.007-PIM-2.6-1.3$


Any thoughts? Any help would be appreciated.

---

### Post by kaamos on 2006-03-04
It's not pretty to begin with so try this. :)

To deal with the "not found":
```
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/cc
```
Make sure to remove the link afterwards!
```
sudo rm /usr/bin/cc
```

---

### Post by benskiedra on 2006-03-05
Method worked but as soon as I put make command into the terminal I get lots of errors and warnings. :cry: Maybe there are some links missing?


benas@ubuntu:/root/CnxADSL-6.1.2.007-PIM-2.6-1.3$ make
for n in KernelModule/DpController; \
        do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[2]: `CnxADSL.ko' is up to date.
make[2]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/KernelModule'
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/DownLoadApp'
cc -DCPU=486 -march=i486 -DUTS_MACHINE='"i386"' -c -Wall -O -I/usr/include -I. -I../ -I../KernelModule   -c -o cnxadslload.o cnxadslload.c
cnxadslload.c:36:20: stdlib.h: No such file or directory
cnxadslload.c:37:19: stdio.h: No such file or directory
cnxadslload.c:38:19: fcntl.h: No such file or directory
cnxadslload.c:39:19: ctype.h: No such file or directory
cnxadslload.c:40:28: getopt.h: No such file or directory
cnxadslload.c:41:18: wait.h: No such file or directory
cnxadslload.c:42:22: sys/stat.h: No such file or directory
cnxadslload.c:43:20: unistd.h: No such file or directory
cnxadslload.c:45:20: stdint.h: No such file or directory
cnxadslload.c:46:20: string.h: No such file or directory
cnxadslload.c:47:24: sys/socket.h: No such file or directory
cnxadslload.c:48:23: sys/ioctl.h: No such file or directory
cnxadslload.c:49:22: sys/time.h: No such file or directory
In file included from /usr/include/linux/atm.h:19,
                 from cnxadslload.c:50:
/usr/include/linux/types.h:4:23: sys/types.h: No such file or directory
In file included from /usr/include/linux/posix_types.h:47,
                 from /usr/include/linux/types.h:5,
                 from /usr/include/linux/atm.h:19,
                 from cnxadslload.c:50:
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/asm/posix_types.h:13:22: features.h: No such file or directory
cnxadslload.c: In function `main':
cnxadslload.c:134: warning: implicit declaration of function `getopt'
cnxadslload.c:134: error: `EOF' undeclared (first use in this function)
cnxadslload.c:134: error: (Each undeclared identifier is reported only once
cnxadslload.c:134: error: for each function it appears in.)
cnxadslload.c:141: warning: implicit declaration of function `atoi'
cnxadslload.c:141: error: `optarg' undeclared (first use in this function)
cnxadslload.c:149: error: `optind' undeclared (first use in this function)
cnxadslload.c:150: warning: implicit declaration of function `printf'
cnxadslload.c:154: warning: implicit declaration of function `exit'
cnxadslload.c:158: warning: implicit declaration of function `strcpy'
cnxadslload.c:159: warning: implicit declaration of function `strcat'
cnxadslload.c:163: warning: implicit declaration of function `socket'
cnxadslload.c:163: error: `PF_ATMPVC' undeclared (first use in this function)
cnxadslload.c:163: error: `SOCK_DGRAM' undeclared (first use in this function)
cnxadslload.c:190: warning: implicit declaration of function `open'
cnxadslload.c:190: error: `O_RDONLY' undeclared (first use in this function)
cnxadslload.c:202: warning: implicit declaration of function `ioctl'
cnxadslload.c:213: warning: implicit declaration of function `close'
cnxadslload.c: In function `downLoadMicroCode':
cnxadslload.c:298: warning: implicit declaration of function `malloc'
cnxadslload.c:319: warning: implicit declaration of function `read'
cnxadslload.c:335: warning: implicit declaration of function `isspace'
cnxadslload.c:461: warning: implicit declaration of function `free'
cnxadslload.c: In function `SendUserParams':
cnxadslload.c:605: error: `FILE' undeclared (first use in this function)
cnxadslload.c:605: error: `FileHandle' undeclared (first use in this function)
cnxadslload.c:690: warning: implicit declaration of function `memset'
cnxadslload.c:697: warning: implicit declaration of function `fopen'
cnxadslload.c:711: warning: implicit declaration of function `fgets'
cnxadslload.c:711: warning: assignment makes pointer from integer without a castcnxadslload.c:727: warning: implicit declaration of function `isalpha'
cnxadslload.c:753: warning: implicit declaration of function `strcmp'
cnxadslload.c:831: warning: implicit declaration of function `sscanf'
cnxadslload.c:831: error: `EOF' undeclared (first use in this function)
cnxadslload.c:908: warning: implicit declaration of function `fclose'
make[1]: *** [cnxadslload.o] Error 1
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.3/DownLoadApp'
make: *** [all] Error 2
benas@ubuntu:/root/CnxADSL-6.1.2.007-PIM-2.6-1.3$

---

### Post by benskiedra on 2006-03-05
Nobody knows how to solve this problem? :cry:

---

### Post by Sutekh on 2006-03-05
I don't know anything about what your trying to compile, but in my experience source code requires
```
./configure
``` before using make.

---

