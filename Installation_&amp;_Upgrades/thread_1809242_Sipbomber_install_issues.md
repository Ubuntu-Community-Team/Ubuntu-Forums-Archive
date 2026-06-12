---
title: "Sipbomber install issues"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by GregSA on 2011-07-21
Hi all

I am having great difficulty installing this app. This is the error I get

```
 
root@gregubuntu:/home/greg/Desktop# tar -xzf sipbomber_0.8.tar.gz 
root@gregubuntu:/home/greg/Desktop# cd sipbomber
root@gregubuntu:/home/greg/Desktop/sipbomber# make
cd stests;make all
make[1]: Entering directory `/home/greg/Desktop/sipbomber/stests'
c++ -O -Wall -W -Wno-long-long -Wno-unused -ansi -DQT_THREAD_SUPPORT -D_REENTRANT -I../ -I/include -I../bnf -I./ -I../cert_test -c sipb_stest.cpp -o sipb_stest.o
In file included from ../sipb_stestinfo.h:10,
                 from sipb_stest.h:9,
                 from sipb_stest.cpp:6:
../sipb_stpacket.h:13:23: error: qdatetime.h: No such file or directory
In file included from sipb_stest.h:10,
                 from sipb_stest.cpp:6:
../sipb_paramlist.h:9:24: error: qvalidator.h: No such file or directory
In file included from ../sipb_stestinfo.h:10,
                 from sipb_stest.h:9,
                 from sipb_stest.cpp:6:
../sipb_stpacket.h:20: error: &#8216;QTime&#8217; does not name a type
../sipb_stpacket.h: In constructor &#8216;sipb_stpacket::sipb_stpacket()&#8217;:
../sipb_stpacket.h:34: error: &#8216;t&#8217; was not declared in this scope
In file included from sipb_stest.h:10,
                 from sipb_stest.cpp:6:
../sipb_paramlist.h: At global scope:
../sipb_paramlist.h:24: error: ISO C++ forbids declaration of &#8216;QValidator&#8217; with no type
../sipb_paramlist.h:24: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../sipb_paramlist.h:59: error: ISO C++ forbids declaration of &#8216;QValidator&#8217; with no type
../sipb_paramlist.h:59: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[1]: *** [sipb_stest.o] Error 1
make[1]: Leaving directory `/home/greg/Desktop/sipbomber/stests'
make: *** [subdirs] Error 2
root@gregubuntu:/home/greg/Desktop/sipbomber#
```Any help will be greatly appreciated 

Thanks

---

### Post by dino99 on 2011-07-21
do you follow this howto:

[http://linux.softpedia.com/get/Programming/Quality-Assurance-and-Testing/Sipbomber-17789.shtml](http://linux.softpedia.com/get/Programming/Quality-Assurance-and-Testing/Sipbomber-17789.shtml)

you may pay attention at 2 packages inside synaptic: 
- libqt3-mt-dev
- libqt3-compat-headers

and watch their descriptions at bottom.

some comments, but quite old: 2006 :(

[http://metalinkltd.com/downloads.php](http://metalinkltd.com/downloads.php)

---

### Post by GregSA on 2011-07-22
> **dino99 said:**
> do you follow this howto:

[http://linux.softpedia.com/get/Programming/Quality-Assurance-and-Testing/Sipbomber-17789.shtml](http://linux.softpedia.com/get/Programming/Quality-Assurance-and-Testing/Sipbomber-17789.shtml)

you may pay attention at 2 packages inside synaptic: 
- libqt3-mt-dev
- libqt3-compat-headers

and watch their descriptions at bottom.

some comments, but quite old: 2006 :(

[http://metalinkltd.com/downloads.php](http://metalinkltd.com/downloads.php)

Thanks dino99,

Yes, I followed that howto, its fairly straight forward as far as installs go O:)

The two packages you mention are already installed.

sipbomber still won't install :(

```
greg@gregubuntu:~$ sudo apt-get install libqt3-mt-dev
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-mt-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 413 not upgraded.
greg@gregubuntu:~$ sudo apt-get install libqt3-compat-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-compat-headers is already the newest version.
libqt3-compat-headers set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 413 not upgraded.
greg@gregubuntu:~$
```

---

### Post by GregSA on 2011-07-22
I made the following changes to the Makefile but still no luck

Changed the lines


INC=-I./ -I$(QTDIR)/include -Istests/ -Ibnf/ -Icert_test
to
INC=-I./ -I/usr/include/qt4/QT -Istests/ -Ibnf/ -Icert_test

LIBS=-L$(QTDIR)/lib -lqt-mt -lpthread
to
LIBS=-L/usr/lib -lqt-mt -lpthread

MOC=$(QTDIR)/bin/moc
to
MOC=/usr/share/qt4/bin/moc

---

### Post by GregSA on 2011-07-22
Ok, I've just installed Ubuntu netbook edition in a VM and upgraded all packages and installed the necessary compilers using apt-get install build-essential

Getting this error

```
greg@ubuntu:~/Desktop/sipbomber$ make
cd stests;make all
make[1]: Entering directory `/home/greg/Desktop/sipbomber/stests'
c++ -O -Wall -W -Wno-long-long -Wno-unused -ansi -DQT_THREAD_SUPPORT -D_REENTRANT -I../ -I/include -I../bnf -I./ -I../cert_test -c sipb_stest.cpp -o sipb_stest.o
In file included from ../sipb_stestinfo.h:10,
                 from sipb_stest.h:9,
                 from sipb_stest.cpp:6:
../sipb_stpacket.h:13: fatal error: qdatetime.h: No such file or directory
compilation terminated.
make[1]: *** [sipb_stest.o] Error 1
make[1]: Leaving directory `/home/greg/Desktop/sipbomber/stests'
make: *** [subdirs] Error 2
greg@ubuntu:~/Desktop/sipbomber$ 
```


any ideas?  this is freaking me out

---

### Post by dino99 on 2011-07-22
i suppose you already have seen this reply:

[http://www.avforums.co.za/index.php?PHPSESSID=2b3610f9ad9aa9bd2409ef16c5afbef0&topic=10563.msg127461#msg127461](http://www.avforums.co.za/index.php?PHPSESSID=2b3610f9ad9aa9bd2409ef16c5afbef0&topic=10563.msg127461#msg127461)

with:

The package you need installed is libqt4-dev

---

### Post by dino99 on 2011-07-22
interesting link explaining which needed packages have to be installed first:

[http://www.icewalkers.com/rpm/sipbomber/mandriva-2007.0/download/sipbomber-23359.html](http://www.icewalkers.com/rpm/sipbomber/mandriva-2007.0/download/sipbomber-23359.html)


as its for 0.7, may be the package versions is updated too.

at least you can try to install the compiled rpm with alien

---

### Post by GregSA on 2011-07-22
> **dino99 said:**
> i suppose you already have seen this reply:

[http://www.avforums.co.za/index.php?PHPSESSID=2b3610f9ad9aa9bd2409ef16c5afbef0&topic=10563.msg127461#msg127461](http://www.avforums.co.za/index.php?PHPSESSID=2b3610f9ad9aa9bd2409ef16c5afbef0&topic=10563.msg127461#msg127461)

with:

The package you need installed is libqt4-dev

Yip thanks, Im a frequent flyer there:D

---

### Post by GregSA on 2011-07-22
> **dino99 said:**
> interesting link explaining which needed packages have to be installed first:

[http://www.icewalkers.com/rpm/sipbomber/mandriva-2007.0/download/sipbomber-23359.html](http://www.icewalkers.com/rpm/sipbomber/mandriva-2007.0/download/sipbomber-23359.html)


as its for 0.7, may be the package versions is updated too.

at least you can try to install the compiled rpm with alien

Thanks, but none of the download links are valid anymore ](*,)

---

### Post by dino99 on 2011-07-22
> **GregSA said:**
> Thanks, but none of the download links are valid anymore ](*,)

just reopened icewalker link here fastly

---

