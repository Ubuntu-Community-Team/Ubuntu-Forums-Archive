---
title: "Martian driver for Lucent Agere Modem"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by Wix on 2008-07-14
I came across a problem trying to compile the latest release of Martian driver for the Lucent Agere Modem

First, I did a ScanModem which checked out fine and then proceeded to do a compile.

There seems to be a problem with the latest
martian-full-20080625.tar.gz file. I tried to compile this version with
kernel -2.6.24-19-generic for Ubuntu. I believe there is something wrong
with the make file and ...... I have tried to contact the creator's but, have had no success...........

Following are results from my attempts>>>>>

wix@passport-laptop:~/Lucent$ ls
martian-full-20080625 Scanmodem
wix@passport-laptop:~/Lucent$ cd martian-full-20080625
wix@passport-laptop:~/Lucent/martian-full-20080625$ make all
make: *** No rule to make target `all'. Stop.
wix@passport-laptop:~/Lucent/martian-full-20080625$ make clean
make -C kmodule/ clean
make[1]: Entering directory `/home/wix/Lucent/martian-full-20080625/kmodule'
make -C /lib/modules/2.6.24-19-generic/build
M="/home/wix/Lucent/martian-full-20080625/kmodule" clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/home/wix/Lucent/martian-full-20080625/kmodule'
make -C modem/ clean
make[1]: Entering directory `/home/wix/Lucent/martian-full-20080625/modem'
RM OBJS
RM BINS
RM TOOLS
make[1]: Leaving directory `/home/wix/Lucent/martian-full-20080625/modem'
wix@passport-laptop:~/Lucent/martian-full-20080625$ make all
make: *** No rule to make target `all'. Stop.
wix@passport-laptop:~/Lucent/martian-full-20080625$ ls
ChangeLog INSTALL Makefile~ modem
Cleaning.txt kmodule martian-full-20080625.tar.gz README
Concept Makefile martian.h scripts
wix@passport-laptop:~/Lucent/martian-full-20080625$ make
The martian_dev.ko driver and the complementary helper martian_helper are
for use with kernels after 2.6.20. Use the martian-20080407.tar.gz for
earlier kernels.
wix@passport-laptop:~/Lucent/martian-full-20080625$


Would appreciate any help or direction... Thanks Wix
Wix is online now Report Post

---

