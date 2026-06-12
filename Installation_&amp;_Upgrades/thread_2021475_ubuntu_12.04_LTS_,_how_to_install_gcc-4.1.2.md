---
title: "ubuntu 12.04 LTS , how to install gcc-4.1.2?"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by megoo on 2012-07-09
Hi guys! 
Am using ubuntu 12.04 LTS, and I need gcc-4.1.2 for compiling some projects. gcc 4.1.2 is the precise version that the project need. 
I download the 4.1.2 source code but does not compile the source successfully.  So I download .deb files from ubuntu archive, but still, errors show up in software center:
Dependency is not satisfiable: gcc-4.1-base(=4.1.2-27ubuntu1)
using 
sudo dpkg -i *.deb
ends in :
```
Selecting previously unselected package cpp-4.1.
(Reading database ... 325894 files and directories currently installed.)
Unpacking cpp-4.1 (from cpp-4.1_4.1.2-27ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.1.
Unpacking g++-4.1 (from g++-4.1_4.1.2-27ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.1-multilib.
Unpacking g++-4.1-multilib (from g++-4.1-multilib_4.1.2-27ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc-4.1.
Unpacking gcc-4.1 (from gcc-4.1_4.1.2-27ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc-4.1-base.
Unpacking gcc-4.1-base (from gcc-4.1-base_4.1.2-27ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc-4.1-multilib.
Unpacking gcc-4.1-multilib (from gcc-4.1-multilib_4.1.2-27ubuntu1_amd64.deb) ...
Selecting previously unselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from libstdc++6-4.1-dev_4.1.2-27ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of g++-4.1-multilib:
 g++-4.1-multilib depends on lib32stdc++6 (>= 4.1.2-27ubuntu1); however:
  Package lib32stdc++6 is not installed.
dpkg: error processing g++-4.1-multilib (--install):
 dependency problems - leaving unconfigured
Setting up gcc-4.1-base (4.1.2-27ubuntu1) ...
Setting up cpp-4.1 (4.1.2-27ubuntu1) ...
Processing triggers for man-db ...
dpkg: dependency problems prevent configuration of gcc-4.1:
 libgomp1 (4.6.3-1ubuntu5) breaks gcc-4.1 and is installed.
 libstdc++6:i386 (4.6.3-1ubuntu5) breaks gcc-4.1 and is installed.
 libstdc++6 (4.6.3-1ubuntu5) breaks gcc-4.1 and is installed.
 libgcc1:i386 (1:4.6.3-1ubuntu5) breaks gcc-4.1 and is installed.
 libgcc1 (1:4.6.3-1ubuntu5) breaks gcc-4.1 and is installed.
dpkg: error processing gcc-4.1 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-4.1-multilib:
 gcc-4.1-multilib depends on gcc-4.1 (= 4.1.2-27ubuntu1); however:
  Package gcc-4.1 is not configured yet.
dpkg: error processing gcc-4.1-multilib (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-4.1:
 g++-4.1 depends on gcc-4.1 (= 4.1.2-27ubuntu1); however:
  Package gcc-4.1 is not configured yet.
dpkg: error processing g++-4.1 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.1-dev:
 libstdc++6-4.1-dev depends on g++-4.1 (= 4.1.2-27ubuntu1); however:
  Package g++-4.1 is not configured yet.
dpkg: error processing libstdc++6-4.1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-4.1-multilib
 gcc-4.1
 gcc-4.1-multilib
 g++-4.1
 libstdc++6-4.1-dev

```Does anyone know how to install gcc 4.1.2 on ubuntu 12.04 LTS ? :confused:

---

### Post by dino99 on 2012-07-09
you can download the required packages from the lucid repo, to an empty folder;


 then to install them, from that folder:

sudo dpkg -i *

[https://launchpad.net/ubuntu/+source/gcc-4.1](https://launchpad.net/ubuntu/+source/gcc-4.1)

---

### Post by megoo on 2012-07-11
HI ,I download these three files:
        gcc-4.1_4.1.2.orig.tar.gz
        gcc-4.1_4.1.2-27ubuntu1.diff.gz
        gcc-4.1_4.1.2-27ubuntu1.dsc
and put them to empty folder,then use 
        sudo dpkg -i *

But still errors happens,  can you help me? Thanks so much!
```
dpkg-split: error: error reading deb: Is a directory
dpkg: error processing deb (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-deb: error: `gcc-4.1_4.1.2-27ubuntu1.diff.gz' is not a debian format archive
dpkg: error processing gcc-4.1_4.1.2-27ubuntu1.diff.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `gcc-4.1_4.1.2-27ubuntu1.dsc' is not a debian format archive
dpkg: error processing gcc-4.1_4.1.2-27ubuntu1.dsc (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `gcc-4.1_4.1.2.orig.tar.gz' is not a debian format archive
dpkg: error processing gcc-4.1_4.1.2.orig.tar.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-split: error: error reading null: Is a directory
dpkg: error processing null (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 deb
 gcc-4.1_4.1.2-27ubuntu1.diff.gz
 gcc-4.1_4.1.2-27ubuntu1.dsc
 gcc-4.1_4.1.2.orig.tar.gz
 null

```

---

### Post by pedro.nariyoshi on 2012-08-29
Hey megoo,

the files you need are the built ones (*.deb). If you click on Lucid, then under "Builds" there should be one for your arch.

Do you also need to compile mex files?

---

### Post by pedro.nariyoshi on 2012-08-29
Hey Dino,

unfortunately, installing gcc 4.1 conflicts with gcc 4.6 which is installed in Precise.

---

