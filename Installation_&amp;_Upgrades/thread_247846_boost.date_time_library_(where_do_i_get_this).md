---
title: "boost.date time library (where do i get this?)"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by bloah on 2006-08-31
hi,

i wanted to try qbittorrent, hence i need libtorrent.

however, when i am trying to compile the libtorrent files, it says

> configure: error: unable to find Boost.DateTime library, currently this is required.

now, i searched everywhere for that damn boost lib, but i couldn't find it ( just some rpm package for another distribution [http://rpm.pbone.net/index.php3/stat/4/idpl/1954966/com/boost-datetime-1.30.2-alt1.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1954966/com/boost-datetime-1.30.2-alt1.i586.rpm.html) ).

does somebody have an idea where to get this ? thanks...

---

### Post by wbc1228 on 2006-09-01
you need to compile it?
I have qbittorrent on my dapper.
All I did was install rb-libtorrent_0.10-0ubuntu4_i386.deb and then qbittorrent_0.6.1-0ubuntu2_i386.deb.
It didn't ask me for a Boost.DateTime library at all.

[http://qbittorrent.sourceforge.net/index.php?option=com_content&task=view&id=19&Itemid=29](http://qbittorrent.sourceforge.net/index.php?option=com_content&task=view&id=19&Itemid=29)

I'm a linux newbie so that is all the help I can provide (if it even helps).  Hopefully it will work.  If not, someone else will have to take a stab at it.

---

### Post by bloah on 2006-09-02
it works, thank you very much...

---

### Post by smmdc3 on 2008-02-14
The package maintainer forgot to call AX_BOOST_BASE. It's good that you found something that works, but if you run into this problem in the future, add this to $SRC/configure.in anywhere before the first call to BOOST_WHATEVER_ISNT_WORKING:

dnl If there's a good samaritan out there
dnl they can inform the package maintainer
dnl that a cursory glance at $PREFIX/share/aclocal/ax_boost_*.m4
dnl will reveal you need to call AX_BOOST_BASE
dnl before using any boost m4 files
dnl I was too lazy myself
AX_BOOST_BASE

(you don't need the dnl lines if you're in a hurry)

Then, on my system, I had to do this as root
(the $PREFIX I used on my system was /usr/local)

cd $PREFIX/include
ln -s boost-1_34_1/boost

Then run

aclocal && autoconf
./configure
make
sudo make install

(adding whatever configure options you want to the configure line)

The symbolic link you only have to do once, and adding the stuff to configure.in and using aclocal and autoconf will work any time a package gives you that error about a boost library

---

### Post by smmdc3 on 2008-03-10
Just an update, I used the m4 files located at
[http://autoconf-archive.cryp.to/](http://autoconf-archive.cryp.to/)

extracted to /usr/share/aclocal

and the dnl lines are probably pretty snippy and unnecessary because of it, and should be replaced with

dnl Modified to conform to autoconf scripts
dnl located at [http://autoconf-archive.cryp.to](http://autoconf-archive.cryp.to)

If your aclocal binary is in /usr/local/bin, or /opt/aclocal/bin, or somewhere, the /usr/local part is your prefix; just make sure that you extract the m4 files to $prefix/share/aclocal


As an aside, my sincere apologies go to the original source authors. The underlying assumption behind my previous comments was that it was reasonable to expect the m4 scripts I thought the authors were relying upon to be on the client systems; it took me helping someone else out who tried to use the instructions I wrote out on this page to make me realize there were two sets of m4 scripts, one included in the source, and one that I was using, and that my m4 scripts were "custom" enough that expecting the source authors to accommodate them is completely unreasonable.

---

### Post by smmdc3 on 2008-03-10
Also, if anyone else finds this, I just got done helping someone else who used similar advice, but ended up needing to copy a file from the libtorrent source

Assuming $prefix is your aclocal prefix, and $source is your libtorrent source directory,

cp $source/m4/acx_pthread.m4 $prefix/share/aclocal

And, again, any other m4 scripts I had, you can get with

wget [http://autoconf-archive.cryp.to/autoconf-archive-2008-02-21.tar.bz2](http://autoconf-archive.cryp.to/autoconf-archive-2008-02-21.tar.bz2)
tar -xf autoconf-archive-2008-02-21.tar.bz2
cd autoconf-archive-2008-02-21.tar.bz2
./configure --prefix=./tmp
make install
mv tmp/share/aclocal/*boost* $prefix/share/aclocal

(just did that myself and did a diff to make sure I was using the same scripts, and sure enough, I was)

/*****************************/

I realize that all seems really complicated

Soooooo...

Here's everything wrapped up in a shell script, start to finish

/******************************/

```

#!/bin/bash

if [ $UID != 0 ]; then
    echo "This script must be run as root!"
fi


# change this to your aclocal prefix
ACLOCAL_PREFIX=/usr
if [ ! -d $ACLOCAL_PREFIX/share/aclocal ]; then
    echo "You need to fix the ACLOCAL_PREFIX variable in this script"
    exit 1
fi

# change this to whatever you want to pass to libtorrent's configure
CONFIG_OPTS="--prefix=/usr/local"

if [ ! -f autoconf-archive-2008-02-21.tar.bz2 ]; then
    wget http://autoconf-archive.cryp.to/autoconf-archive-2008-02-21.tar.bz2
fi
tar -xf autoconf-archive-2008-02-21.tar.bz2
cd autoconf-archive-2008-02-21
./configure --prefix=./tmp
make install
mv tmp/share/aclocal/*boost* $prefix/share/aclocal
cd ..
rm -rf autoconf-archive-2008-02-21
if [ ! -f libtorrent-0.12.1.tar.gz ]; then
    wget http://downloads.sourceforge.net/libtorrent/libtorrent-0.12.1.tar.gz
fi
tar -xf libtorrent-0.12.1.tar.gz
cd libtorrent-0.12.1
cp m4/acx_pthread.m4 $ACLOCAL_PREFIX/share/aclocal
aclocal && autoconf
echo "If there were no errors, hit y or Y to continue (y/N)"
read -n 1 continue
if [ -z "`echo $continue | grep [yY]`" ]; then
    echo "Breaking off before install, check ${ACLOCAL_PREFIX}/share/aclocal for boost m4 files"
    exit 1
fi
./configure $CONFIG_OPTS
make
make install
cd ..
rm -rf libtorrent-0.12.1

```

---

