---
title: "Problem with linux headers"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by Nunners on 2010-04-13
I've made a complete hash of my ubuntu server (9.04) which is running our asterisk server (PBX).... in trying to reinstall everything I've hit the following problem:

```
root@asterisk:/usr/src/dahdi-linux-2.2.1.1# make clean
make -C drivers/dahdi/firmware clean
make[1]: Entering directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware                                                                             '
rm -f dahdi-fw-*.o
make[1]: Leaving directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware'
root@england:/usr/src/dahdi-linux-2.2.1.1# make
make -C drivers/dahdi/firmware firmware-loaders
make[1]: Entering directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware                                                                             '
make[1]: Leaving directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware'
You do not appear to have the sources for the 2.6.31-20-server kernel installed.
make: *** [modules] Error 1

```I've installed *apt-get source linux-headers-2.6.31-20-server* which I thought would have solved it, but it's still giving me a head ache.

Can anyone give me a nudge in the right direction as to what's wrong?

Thanks
(a very frustrated) Nunners :(

---

### Post by Nunners on 2010-04-16
Sorry to bump this, but I really do need to know what I'm missing... I've tried everything short of rebuilding the whole system which I really don't want to have to do... can anyone help?

Thanks
Nunners

---

### Post by Nunners on 2010-05-17
Hi All,

I'm still struggling to get this installed.  I've tried "apt-get source linux-headers-2.6.31-20-server", but again still getting the same from trying to install dahdi.  Can anyone give me a hint?

Many thanks
Nunners

Please!!!!

---

### Post by ronparent on 2010-05-17
Try the server forum?

---

