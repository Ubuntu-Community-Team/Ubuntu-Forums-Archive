---
title: "Han anyone tried to install MonetDB on Ubuntu?"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by spearfish on 2007-09-22
Hi All,

Does anyone have advice for installing MonetDB in Ubuntu?  I need to use MonetDB for a Database class, where we learn XQuery.

I looked at the installation instructions on the MonetDB web page and it sure looks confusing!

[http://monetdb.cwi.nl/projects/monetdb/Download/Packages/index.html](http://monetdb.cwi.nl/projects/monetdb/Download/Packages/index.html)

Cheers!

---

### Post by HD Genscher on 2007-09-23
Hi spearfish,

based on a standard Ubuntu 7.04 installation, install the following additional packages:

libtool (and all its dependencies)
libxml2-dev (and all its dependencies)

Then download the following:

1. Boehm garbage collector: [http://www.hpl.hp.com/personal/Hans_Boehm/gc/gc_source/gc.tar.gz](http://www.hpl.hp.com/personal/Hans_Boehm/gc/gc_source/gc.tar.gz)    (Surprisingly, this library is not mentioned in the documentation. It's required for building pathfinder.)
2. MonetDB Common: [http://downloads.sourceforge.net/monetdb/MonetDB-1.18.2.tar.gz](http://downloads.sourceforge.net/monetdb/MonetDB-1.18.2.tar.gz)
3. MonetDB Client: [http://downloads.sourceforge.net/monetdb/clients-1.18.2.tar.gz](http://downloads.sourceforge.net/monetdb/clients-1.18.2.tar.gz)
4. MonetDB4 Server: [http://downloads.sourceforge.net/monetdb/MonetDB4-4.18.2.tar.gz](http://downloads.sourceforge.net/monetdb/MonetDB4-4.18.2.tar.gz)
5. MonetDB XQuery: [http://downloads.sourceforge.net/monetdb/pathfinder-0.18.4.tar.gz](http://downloads.sourceforge.net/monetdb/pathfinder-0.18.4.tar.gz)

Unpack these to separate directories. Change into each directory in the above order, and in each do:

./configure
make
sudo make install

Depending on the speed and memory of your machine, this may take a while. Please note that this will install MonetDB in /usr/local, which is fine in most cases. If you want to install somewhere else instead, add --prefix=<installation path> to the ./configure command and be sure to have <installation path>/bin in your PATH, as well as <installation path>/lib in your LD_LIBRARY_PATH.

To test the MonetDB installation, open a shell and start the server:
sudo Mserver --dbinit="module(pathfinder);"

Now open another shell and start the client:
MapiClient -lx

Finally enter some of the "Hello World" examples on [http://monetdb.cwi.nl/projects/monetdb/XQuery/QuickTour/HelloWorld/index.html](http://monetdb.cwi.nl/projects/monetdb/XQuery/QuickTour/HelloWorld/index.html). Finish each example with Ctrl+D.

Have fun!

---

### Post by luukpeters on 2008-06-06
I've managed to install MonetDB/XQuery on Ubuntu 7.10.
At first I tried the rpms, but since rpm is not supported by default, I tried compiling from source code. This seemed to work, until I tried starting the Mserver:

```

>>Mserver --dbinit="module(pathfinder);"

Mserver: error while loading shared libraries: libmonet.so.0: cannot open shared object file: No such file or directory

```

So that didn't work. I went back to the rpms, there seem to be a tool called alien that converts an rpm to deb. After converting, all deb files seem to install fine when dubbelclicking in dolphin.

Now I can start the Mserver.

---

