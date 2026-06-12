---
title: "Help - Install/Compiling kqemu"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by tonydm on 2006-10-16
Hi,

I'm trying to enable kqemu support and am failing.  I have been following andrejkw's post at [http://www.ubuntuforums.org/showthread.php?t=187413](http://www.ubuntuforums.org/showthread.php?t=187413).
All is well (or seems to be) until I run sudo ./install_qemu.sh

...
...
...
...
much compiling & linking
...
...

make[1]: Leaving directory `/tmp/build-qemu/qemu-0.8.2/arm-softmmu'
Configuring KQEMU...
No Makefile file present in /lib/modules/2.6.15-26-386/build/ - kqemu cannot be built
grep: /lib/modules/2.6.15-26-386/build//Makefile: No such file or directory
Source path       /tmp/build-qemu/qemu-0.8.2/kqemu
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
Compiling KQEMU...
make -C /lib/modules/2.6.15-26-386/build/ M=`pwd` modules
make: *** /lib/modules/2.6.15-26-386/build/: No such file or directory.  Stop.
make: *** [kqemu.ko] Error 2
ERROR: Unable to Compile KQEMU...

Any of your thoughts would be greatly appreciated!

Tony

---

