---
title: "[SOLVED] Build of transmssion 1.04 fails on Ubuntu 7.10"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Tiggar on 2008-02-03
Hello Folks,

the current transmission binary package does not provide a daemon. So I decided to download the latest stable source from the transmission web site:

[http://download.m0k.org/transmission/files/transmission-1.04.tar.bz2](http://download.m0k.org/transmission/files/transmission-1.04.tar.bz2)

and build the source myself.

But during the build the following error occurs:

```
ranlib libtransmission.a
gcc -DPACKAGE_NAME=\"transmission\" -DPACKAGE_TARNAME=\"transmission\" -DPACKAGE_VERSION=\"1.04\" -DPACKAGE_STRING=\"transmission\ 1.04\" -DPACKAGE_BUGREPORT=\"http://trac.transmissionbt.com/newticket\" -DPACKAGE=\"transmission\" -DVERSION=\"1.04\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_DAEMON=1 -DHAVE_DIRNAME=1 -DHAVE_BASENAME=1 -DSIZEOF_VOIDP=8 -DHAVE_PTHREAD=1 -DGETTEXT_PACKAGE=\"transmission\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -I.  -I. -I.. -I../third-party/ -D__TRANSMISSION__ -I../third-party/libevent   -pthread -g -Wall -W -O3 -funroll-loops -MT bencode-test.o -MD -MP -MF .deps/bencode-test.Tpo -c -o bencode-test.o bencode-test.c
mv -f .deps/bencode-test.Tpo .deps/bencode-test.Po
make[2]: *** No rule to make target `../third-party/miniupnp/libminiupnp.a', needed by `bencode-test'.  Stop.
make[2]: Leaving directory `/opt/transmission-1.04/libtransmission'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/opt/transmission-1.04/libtransmission'
make: *** [install-recursive] Error 1
``` 

Could someone help me to solve this or point me to a binary package which already contains the transmission-daemon executable?

Thanks Tiggar

---

### Post by orange2k on 2008-02-03
There is an older version of Transmission in the repository: its the 1.01 version.

If you want to compile the newest version yourself, take note of the required dependencies.
   >  *   A version of the `getopt' library with getopt_long(). Most systems already have this.
    * intltool 0.23 or later
    * gettext 0.14.1 or later
    * OpenSSL 0.9.8 or later. (See note)
    * GTK+ 2.6 or later. (See note)
    * Note: if installing OpenSSL or GTK+ from a package manager, you'll also need to install their corresponding development packages. These are usually named $PACKAGENAME-devel or $PACKAGENAME-dev, depending on which distribution and/or repository you use.



Ive just compiled the version 1.04 from source and it "just works"...

edit: the development package for OpenSSL on Ubuntu is called libssl-dev, so you just have to mark it in the synaptic package manager to install. Other packages should probably already be installed on your system...

---

### Post by Tiggar on 2008-02-03
Hm. This has not helped. All the dependencies are installed. Configure runs totally fine. I guess the problem is related to "libminiupnp.a". But maybe I'm wrong.

How can we check what's different between our two system configurations and what I have to install, additionally?

Cheers.

---

### Post by orange2k on 2008-02-03
> **Tiggar said:**
> Hm. This has not helped. All the dependencies are installed. Configure runs totally fine. I guess the problem is related to "libminiupnp.a". But maybe I'm wrong.

How can we check what's different between our two system configurations and what I have to install, additionally?

Cheers.

What step of the process is the problem?
Is it the last step?

Im just guessing but maybe you forgot to run "make install" with "sudo" in front...

---

### Post by orange2k on 2008-02-03
Hehe, maybe you don`t have to build from source after all...
There are pre-built packages for Ubuntu 7.10, both 32 and 64-bit...

Look here:

[http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

---

### Post by Tiggar on 2008-02-03
Hi orange2k

> **orange2k said:**
> Hehe, maybe you don`t have to build from source after all...
There are pre-built packages for Ubuntu 7.10, both 32 and 64-bit...

Look here:

[http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

thanks for link. I downloaded and installed the 64bit amd version and it was working out of the box. Although I couldn't manage to build transmission from source. Btw. I tried to build it as root. I really would like to know why it is not working. 

Ok. Another question. The repository from where I downloaded that .deb package for transmission ... how could I include it in the paths for aptitude? 

Cheers.

---

### Post by orange2k on 2008-02-03
I`m not sure that its meant to be used as a software repository...
You could try to add the page to the sources list, but Im not sure if it would work right...

---

### Post by Tiggar on 2008-02-03
A bit of googling took me to this web site, which provides a HowTo for integrating GetDeb.net as software repository into apt-get/aptitude/synaptics: 

[http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/](http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/)

Cheers.

---

### Post by orange2k on 2008-02-03
> **Tiggar said:**
> A bit of googling took me to this web site, which provides a HowTo for integrating GetDeb.net as software repository into apt-get/aptitude/synaptics: 

[http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/](http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/)

Cheers.

Hey thats great!!!
I prefer to keep my source list as clean as possible, but the people at Getdeb do a great job of keeping things updated...

---

