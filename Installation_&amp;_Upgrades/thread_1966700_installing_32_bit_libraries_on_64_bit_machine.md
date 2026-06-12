---
title: "installing 32 bit libraries on 64 bit machine"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by LonelyStar on 2012-04-27
Hi,

I am using ubuntu 12.04 64bit. I am trying to install 32 bit libaries to compile 32 bit programs. I already install i32-libs-muiltiarch, but many libraries are still missing. So I tried:

```

apt-get install libboost-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libboost-dev:i386 : Depends: libboost1.46-dev:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

mmh, why can't he just install liboost1.46-dev:i386???

Is there a recommended way to get 32bit libraries on a 64bit machine?

Thanks!

---

