---
title: "Compiling 2.6.18 kernel, error"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by nariusb on 2006-10-11
Can you help the beginner to figure the compiling error? I follow the instructions here: [http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)
I have Ubuntu 6.06 LTS

I've got to the 4th line and the process stops with error 2:

root@narius-desktop:/usr/src/linux# sudo cp /boot/config-`uname -r` .config && sudo make xconfig
/usr/src/linux-2.6.18/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-2.6.18/scripts/gcc-version.sh: line 12: gcc: command not found
HOSTCC scripts/basic/fixdep
/bin/sh: gcc: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

I did copy/paste of the commands to be sure.
I'm a beginner, so please help if you find a minute.
Thanks

---

### Post by nariusb on 2006-10-12
I figured it out. All it needed is apt-get install gcc-3.4.

I had gcc but not gcc3.4.
It compiled to 6.2.18 with no problems after that just over an hour.

---

