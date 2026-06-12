---
title: "install mspgcc4"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by amuna on 2012-04-16
Hello ,
I installed according to this link mspgcc4 [http://torrentula.to.funpic.de/2012/01/14/installing-the-msp430-toolchain-on-ubuntu/](http://torrentula.to.funpic.de/2012/01/14/installing-the-msp430-toolchain-on-ubuntu/) but by typing 
```
cd mspgcc4 && sudo perl buildgcc.pl 
``` I got this error 
```
checking for msp430-gcc... /home/ubuntu/mspgcc4/build/gcc-4.4.5-build/./gcc/xgcc -B/home/ubuntu/mspgcc4/build/gcc-4.4.5-build/./gcc/ -B/opt/msp430-gcc-4.4.5/msp430/bin/ -B/opt/msp430-gcc-4.4.5/msp430/lib/ -isystem /opt/msp430-gcc-4.4.5/msp430/include -isystem /opt/msp430-gcc-4.4.5/msp430/sys-include  -mmcu=msp3
checking for suffix of object files... configure: error: in `/home/ubuntu/mspgcc4/build/gcc-4.4.5-build/msp430/msp3/libgcc':
configure: error: cannot compute suffix of object files: cannot compile
See `config.log' for more details.
make[1]: *** [configure-target-libgcc] Error 1
make[1]: Leaving directory `/home/ubuntu/mspgcc4/build/gcc-4.4.5-build'
make: *** [all] Error 2
sh do-gcc.sh "/opt/msp430-gcc-4.4.5" "4.4.5" "http://ftp.uni-kl.de" "build" "gcc-4.x" "4.3.1" "2.4.2" exited with status code 2.
Failed to execute sh do-gcc.sh "/opt/msp430-gcc-4.4.5" "4.4.5" "http://ftp.uni-kl.de" "build" "gcc-4.x" "4.3.1" "2.4.2" at buildgcc.pl line 248, <STDIN> line 9.

```Please help me to solve this problem 
THANK'S IN ADVANCE

---

### Post by gordintoronto on 2012-04-16
What convinced you to use those instructions?

[https://launchpad.net/ubuntu/oneiric/+search?text=msp430](https://launchpad.net/ubuntu/oneiric/+search?text=msp430)

What version of Ubuntu are you using?

Perhaps you need to do more reading.

---

### Post by amuna on 2012-04-17
because these instructions and this method are comrehensive and easy 
I use Ubuntu 11.04

---

