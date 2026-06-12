---
title: "how do i apt-build i686"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-04-19
how do i apt-build my ubuntu install for i686.

(if I may, please can we refrain from posts regarding the benfit of i686 over i386 and kernel only upgrades) .... I would like to rebuild for i686 for "research" purposes.

I've installed apt-build and configured the apt-build.conf as follows:
```

build-dir = /home/fred/var/cache/apt-build/build
repository-dir = /home/fred/var/cache/apt-build/repository
Olevel = -O3
march = -march=i686
mcpu = -mcpu=athlon-xp
options = " "
make_options = " "

```

and created a build file in /etc/apt/apt-build.list (just a list of already installed packages)

trying to build however, gives an error:
```

# apt-build world
march: no such variable at /etc/apt/apt-build.conf line 4
mcpu: no such variable at /etc/apt/apt-build.conf line 5
..
..

```

So I changed the conf file to:
```

build-dir = /home/fred/var/cache/apt-build/build
repository-dir = /home/fred/var/cache/apt-build/repository
Olevel = -O3
mtune = -mtune=athlon-xp
options = " "
make_options = " "

```

whilst this did something, it seems to be building for i386 and even then it failed!!
```

# apt-build world
...
...
-----> Building acpid <-----
dpkg-buildpackage: source package acpid
dpkg-buildpackage: source version 1.0.4-7.1
dpkg-buildpackage: source changed by root <root@desktop.WORKGROUP>
dpkg-buildpackage: host architecture i386
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/home/fred/var/cache/apt-build/build/acpid-1.0.4'
rm -f acpid acpi_listen acpid.8.gz acpi_listen.8.gz *.o
make[1]: Leaving directory `/home/fred/var/cache/apt-build/build/acpid-1.0.4'
dh_clean
 debian/rules build
dh_testdir
chmod g-s -R *
/usr/bin/make
make[1]: Entering directory `/home/fred/var/cache/apt-build/build/acpid-1.0.4'
cc -Wall -Werror -g -DVERSION="\"1.0.4\""   -c -o acpid.o acpid.c
cc1: warnings being treated as errors
acpid.c: In function &#8216;main&#8217;:
acpid.c:65: warning: &#8216;sock_fd&#8217; may be used uninitialized in this function
make[1]: *** [acpid.o] Error 1
make[1]: Leaving directory `/home/fred/var/cache/apt-build/build/acpid-1.0.4'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
----> Cleaning up object files <-----
Cleaning in directory .
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/home/fred/var/cache/apt-build/build/acpid-1.0.4'
rm -f acpid acpi_listen acpid.8.gz acpi_listen.8.gz *.o
make[1]: Leaving directory `/home/fred/var/cache/apt-build/build/acpid-1.0.4'
dh_clean
Error while building acpid!
Sorry, no package to install.

```

also, dpkg-architecture seems to not allow i686 or not configured correctly:
```

DEB_BUILD_ARCH=i386
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_GNU_CPU=i486
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=i486-linux-gnu
DEB_HOST_ARCH=i386
DEB_HOST_ARCH_OS=linux
DEB_HOST_ARCH_CPU=i386
DEB_HOST_GNU_CPU=i486
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=i486-linux-gnu

```
I recall reading a thread on some forum (cannot recall) about having to edit /usr/bin/dpkg-architecture to hack in i686 ???

all very confusing.

any ideas?

---

