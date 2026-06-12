---
title: "c-client - make errors"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by dcogley on 2006-09-21
Can anyone help me build c-client under Ubuntu 6.06?

I am trying to build c-client which is a dependency for php imap support.
In Ubuntu 6.06, I have downloaded everything I need.

From the php src directory, I enter
./configure --with-apxs2=/usr/bin/apxs2 --with-mysql --with-imap --with-curl --with-zlib --enable-mbstring

and see the message

configure: error: Cannot find imap library (libc-client.a). 
Please check your c-client installation.

So, I 
[ftp://ftp.cac.washington.edu/imap](ftp://ftp.cac.washington.edu/imap)
get c-client.tar.Z

I 
tar zxvf c-client.tar.Z

cd to the appropriate directory and
make ldb

as indicated in README

I get a lot of these messages
warning: pointer targets in assignment differ in signedness

-------------------------

Searching with google, I find no solution.
There is a hint that the Ubuntu gcc is more strict than
the cc used by the University of Washington team.
It could be that "ldb" is the wrong argument.
"ldb" applies to Debian.
Ubuntu is not listed in the Makefile.

-------------------------

---

