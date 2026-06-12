---
title: "Xchat 2.4.0"
date: 2004-10-24
forum: Installation &amp; Upgrades
---

### Post by Neo40 on 2004-10-24
Hi,

apt-get doest have this version. So I installed the sources and when I do a "make" I get this error: 

/usr/bin/ld: cannot find -lperl

I do have perl installed. Any idea?

Thanks

---

### Post by Mikelevel on 2004-10-24
You can use a debian sid repository to install this version , but this can do errors in future with ubuntu updates

---

### Post by snowx1000 on 2004-10-25
You can download the source package and do ./configure --disable-perl
It should work fine after that.

---

### Post by iwasbiggs on 2004-10-26
Perl yes, you probably have.
You need the perl-dev package.

---

