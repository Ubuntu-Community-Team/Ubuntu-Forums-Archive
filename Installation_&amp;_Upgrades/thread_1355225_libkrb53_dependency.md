---
title: "libkrb53 dependency"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by kitestar on 2009-12-14
Hi,

Ubuntu Server 9.10 i386:  I have a problem with a libkrb53 dependancy.  I understand this package has been split into multiple new packages (all of which I have installed) but I can't get past this point.

Any help appreciated.


I have been searching around and found some similar postings outside of here but nothing that gets me any closer to fixing this.

I started with a fresh install of Ubuntu 9.10 server i386 with nothing added and have added openSSH, and the zarafa prerequistites apache2, mysql5 and postfix

Here's what I get:

$ sudo dpkg -i zarafa_6.30.4-17264_i386.deb 
(Reading database ... 44355 files and directories currently installed.)
Preparing to replace zarafa 6.30.5-17658 (using zarafa_6.30.4-17264_i386.deb) ...
Unpacking replacement zarafa ...
dpkg: dependency problems prevent configuration of zarafa:
 zarafa depends on libkrb53 (>= 1.6.dfsg.2); however:
  Package libkrb53 is not installed.
dpkg: error processing zarafa (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 zarafa

So I tried sudo apt-get install libkrb53

$ sudo apt-get install libkrb53
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libkrb53 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-pkinit libkrb5support0 libkrb5-3 libk5crypto3 libgssapi-krb5-2
E: Package libkrb53 has no installation candidate

I tried installing each of these and was told the following or similar for each one.

$ sudo apt-get install libgssapi-krb5-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgssapi-krb5-2 is already the newest version.

Where do I go next?

---

### Post by Ac1D on 2010-01-23
Hava you already solved this problem, cause within a few minutes I'm going to start my try to get it running within 9.10 server.

---

### Post by nasenmann72 on 2010-02-18
Hi,

me too have the same problem. Trying to install Zarafa Server 6.40 on Ubuntu 9.10... 

Any help appreciated. Thanks! 

Der Nasenmann

---

### Post by ridetheteapot on 2010-02-23
From launchpad :
It was suggested to build your own fake libkrb53 deb with libkrb5-3, libgssapi-krb5-2, libk5crypto3, libkrb5support0 as its dependancies. than install it to satisfy the libkrb53 dependancy. (If this works then forcing the install without making the dummy package should also work).
otherwise
[http://packages.debian.org/en/lenny/libkrb53](http://packages.debian.org/en/lenny/libkrb53)
you can grab the package from debian - but i do not know what issues exist with it.

---

