---
title: "error making omnet in ubuntu"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by mahmoodn on 2007-12-17
I want to install omnetpp in gutsy. the problem is although I set environment variables:
```
export PATH=$PATH:/home/omnetpp-3.4b2/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/omnetpp-3.4b2/lib

```
whenever I "make", it says that opp_msgc command can not be found!. I manually searched for "opp_msgc" and found in /home/omnetpp-3.4b2/bin which is indeed in the path.
```
/include -I. -DBUILDING_SIM -I../nedxml -o distrib.o distrib.cc
opp_msgc -Xnc -Xns sim_std.msg
make[1]: opp_msgc: Command not found
make[1]: *** [sim_std_m.cc] Error 127
make[1]: Leaving directory `/home/omnetpp-3.4b2/src/sim'
make: *** [sim] Error 2

```

What is the problem?

---

### Post by newsman on 2008-01-24
your export paths are wrong.  you wrote:

export PATH=$PATH:/home/omnetpp-3.4b2/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/omnetpp-3.4b2/lib

they should not be /home/omnetppxxx but /home/yourname/omnetpp

so in my case they would be for example:  /home/umar/omnetppxxx  etc.


meanwhile, i get a different error:

```
b2/include -I. -DBUILDING_SIM   -I../nedxml -o distrib.o distrib.cc
opp_msgc -Xnc -Xns sim_std.msg
opp_msgc - part of OMNeT++. (c) 2002-2005 Andras Varga
Translates .msg files into C++

Usage: opp_msgc [-s <cc-file-suffix>] [-t <h-file-suffix>]
                [-I <dir> -I ...] [-h] <nedfile>
  -I <dir>    add directory to include path
  -s <suffix> output C++ file suffix (defaults to: _m.cc)
  -t <suffix> output C++ header file suffix (defaults to: _m.h)
  -P <symbol> add dllexport/dllimport symbol to class declarations
  -h          output in current directory
make[1]: *** [sim_std_m.cc] Error 1
make[1]: Leaving directory `/home/umar/omnetpp-3.4b2/src/sim'
make: *** [sim] Error 2

```

---

### Post by newsman on 2008-01-25
after doing make clean and make (after a reboot) everything worked. I guess bashrc file was not sourced correctly, but i don't know why i always did source command a couple of thousand time :confused: mystery

---

### Post by arejae on 2008-05-30
> **newsman said:**
> after doing make clean and make (after a reboot) everything worked. I guess bashrc file was not sourced correctly, but i don't know why i always did source command a couple of thousand time :confused: mystery
Hi newsman, I think it's not because of bashrc not sourced correctly.

Normally our PATH is in something like /home/arejae/.bashrc right, but when we run sudo command the PATH that we use is actually read from /root/.bashrc

correct me if im wrong yer. this is what i understand now.

anyway, i manage to install omnet in Hardy Heron. here are the details:

[http://www.arejae.com/blog/how-to-install-omnet-in-ubuntu-804.html](http://www.arejae.com/blog/how-to-install-omnet-in-ubuntu-804.html)

---

