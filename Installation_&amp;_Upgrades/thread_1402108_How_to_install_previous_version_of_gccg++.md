---
title: "How to install previous version of gcc/g++"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by matrix72 on 2010-02-08
Hi all.

I have problems with installing of the gtnets simulator (with boeing implementation of ospf manet). According to the documentation, this program is dependent on an older version of
gcc/g++, i.e. version 3.3.3. My question is how can I install this on a newer Ubuntu version. My current version of Ubuntu is 9.10.

Anyone with familiar with this please help.

Regards 

Vinh Pham

---

### Post by gmargo on 2010-02-08
I answered this four days ago when you asked the exact same question.

See the thread: [http://ubuntuforums.org/showthread.php?t=1397510](http://ubuntuforums.org/showthread.php?t=1397510)

---

### Post by matrix72 on 2010-02-09
Dear gmargo.

I sincerly appreciate your reply.
However, I have already tried all the steps performed in your patch. The problem is that the source code I am trying to install is a modified version of GTNetS, implemented by Boeing. Using the patch you provided will not solve the problem.

You may try to install, to check if it works?
All the necessary files are in these links:

1. [http://hipserver.mct.phantomworks.org/ietf/ospf/releases/080602_release-1.01/gtnets-mdr-1.01.tgz](http://hipserver.mct.phantomworks.org/ietf/ospf/releases/080602_release-1.01/gtnets-mdr-1.01.tgz)

2. [http://www.quagga.net/download/attic/quagga-0.99.9.tar.gz](http://www.quagga.net/download/attic/quagga-0.99.9.tar.gz)

3. [http://hipserver.mct.phantomworks.org/ietf/ospf/releases/080602_release-1.01/quagga-0.99.9.ospfv3-manetmdr-gtnets.patch](http://hipserver.mct.phantomworks.org/ietf/ospf/releases/080602_release-1.01/quagga-0.99.9.ospfv3-manetmdr-gtnets.patch)

The documentation can be found here:

[http://hipserver.mct.phantomworks.org/ietf/ospf/releases/080602_release-1.01/ospf6d-boeing.pdf](http://hipserver.mct.phantomworks.org/ietf/ospf/releases/080602_release-1.01/ospf6d-boeing.pdf)




> **gmargo said:**
> I answered this four days ago when you asked the exact same question.

See the thread: [http://ubuntuforums.org/showthread.php?t=1397510](http://ubuntuforums.org/showthread.php?t=1397510)

---

### Post by mushwars on 2010-02-09
you could compile it, glibc and gcc take around 2 hours each to compile, I dont know why you would want an older version, usually with compilers you want the newest version. Otherwise you run into problems compiling.

---

### Post by Bachstelze on 2010-02-09
> **mushwars said:**
> you could compile it, glibc and gcc take around 2 hours each to compile, I dont know why you would want an older version, usually with compilers you want the newest version. Otherwise you run into problems compiling.

Sometimes the code is not compatible with newer versions of gcc, or they create problems. gcc 4.4 has been known to cause problems with a lot of programs that worked fine when compiled with e.g. gcc 4.3.

@OP, gcc 3.3 is available in Hardy, you can probably just add the Hardy repos to your sources.list and do

```
sudo apt-get install gcc-3.3
```

You can also download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them manually, but adding the hardy repos will give you the automatic updates.

*EDIt: it is 3.3.6 however. Are you sure you really need 3.3.3 and not just any 3.3.x?*

---

### Post by matrix72 on 2010-02-09
Hi Bachstelze.

Thx for your reply. I've already tried compiling with 3.3.6 without success.

> **Bachstelze said:**
> Sometimes the code is not compatible with newer versions of gcc, or they create problems. gcc 4.4 has been known to cause problems with a lot of programs that worked fine when compiled with e.g. gcc 4.3.

@OP, gcc 3.3 is available in Hardy, you can probably just add the Hardy repos to your sources.list and do

```
sudo apt-get install gcc-3.3
```

You can also download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them manually, but adding the hardy repos will give you the automatic updates.

*EDIt: it is 3.3.6 however. Are you sure you really need 3.3.3 and not just any 3.3.x?*

---

### Post by gmargo on 2010-02-11
I stumbled across this fellow who has gcc-3.3 and gcc-3.4 compiled for jaunty and karmic:
[https://launchpad.net/~yofel/+archive/off-ppa]("https://launchpad.net/%7Eyofel/+archive/off-ppa")

---

