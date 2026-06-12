---
title: "SimpleScalar on Ubuntu : Prob ?"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by Yorel on 2007-01-23
Hello,

My first post. :-) 

Well...

I'm trying to install SimpleScalar on Ubuntu and i have more and more difficulties. I follow the instructions on some web sites like [http://www.comp.nus.edu.sg/~panyu/simplesim.htm](http://www.comp.nus.edu.sg/~panyu/simplesim.htm) but after i excute these :

> 
 cd $IDIR/simpleutils-990811/
./configure --host=i386-*-linux --target=sslittle-na-sstrix --with-gnu-as --with-gnu-ld --prefix=$IDIR
make all install 

... the make all install shows me some errors :

> make[3]: entrant dans le répertoire « /home/j9/SimpleScalar/simpleutils-990811/b fd »
/bin/sh ./../mkinstalldirs SimpleScalar/lib
/bin/sh ./libtool  --mode=install /bin/sh /home/j9/SimpleScalar/simpleutils-9908 11/install-sh -c libbfd.la SimpleScalar/lib/libbfd.la
_**libtool: install: `SimpleScalar/lib' must be an absolute directory name**_
Try `libtool --help --mode=install' for more information.
make[3]: *** [install-libLTLIBRARIES] Erreur 1
make[3]: quittant le répertoire « /home/j9/SimpleScalar/simpleutils-990811/bfd »

Somebody could help me ? :( 

Thanks a lot,

Yorel.

---

