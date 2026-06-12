---
title: "Need help installing Clearsilver 0.10.4"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Barticus on 2007-05-30
Howdy everyone;

While I can't exactly call myself a newbie to the world of linux, I'm certainly not proficient either and could use a bit of a helping hand to point me in the right direction.

I'm setting up a Dell 1950 server with dual Intel Core Duo processors and Ubuntu 7.04 Desktop - 64 bit.  The end user is a software developer and wants it to be used for Trac, a software package that I had never  even heard of as little as a week ago.  So far the installation had gone pretty smoothly until I got to Clearsilver. As I understand it, since Python 2.5 was already installed it would be best to go with version 0.10.4 of Clearsilver to avoid some problems.  At least, that's what I can make out, I'm not a programmer.  I downloaded the source code and after a few glitches with missing libraries got it to configure properly (adding apache2, python, perl and java to the config).  Now my problem is that I can't get it to make, here is the tail end of the text;

```

*******************************************
** Building Dependencies 
** OSNAME: Linux
** (done) 
make[1]: Leaving directory `/installs/clearsilver-0.10.4/cgi'
make[1]: Entering directory `/installs/clearsilver-0.10.4/cgi'
make[1]: Nothing to be done for `depend'.
make[1]: Leaving directory `/installs/clearsilver-0.10.4/cgi'
make[1]: Entering directory `/installs/clearsilver-0.10.4/util'
make[1]: Nothing to be done for `everything'.
make[1]: Leaving directory `/installs/clearsilver-0.10.4/util'
make[1]: Entering directory `/installs/clearsilver-0.10.4/cs'
make[1]: Nothing to be done for `everything'.
make[1]: Leaving directory `/installs/clearsilver-0.10.4/cs'
make[1]: Entering directory `/installs/clearsilver-0.10.4/cgi'
make[1]: Nothing to be done for `everything'.
make[1]: Leaving directory `/installs/clearsilver-0.10.4/cgi'
make[1]: Entering directory `/installs/clearsilver-0.10.4/perl'
rm -f blib/arch/auto/ClearSilver/ClearSilver.so
cc  -shared -L/usr/local/lib ClearSilver.o  -o blib/arch/auto/ClearSilver/ClearSilver.so        \
           -L/installs/clearsilver-0.10.4/perl/../libs -lneo_cgi -lneo_cs -lneo_utl -lz         \
          
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make[1]: *** [blib/arch/auto/ClearSilver/ClearSilver.so] Error 1
make[1]: Leaving directory `/installs/clearsilver-0.10.4/perl'
make: *** [cs] Error 2

```

Is the 'lz' mentioned is a switch for the compiler not used in Ubuntu?

---

### Post by Barticus on 2007-05-31
Well, it's amazing what a night's rest and a cup of strong coffee can achieve.  Searching the cc man pages reveals that -lz is a call to search a library named 'z'.  On a hunch I installed both the zliblg and zlibc packages with the Synaptic package manager.  Clearsilver now compiles, makes and installs.

---

