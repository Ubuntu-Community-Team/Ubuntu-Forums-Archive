---
title: "Problems after upgrading to Hardy"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by wachaca on 2008-04-30
Hello,
I upgraded the system to hardy.
The new kernel installed without a glitch, and so did many libraries and applications.

However, when I try to install libapache2-mod-php5 I get some error messages that I do not know how to deal with.

**debconf-loadtemplate: error while loading shared libraries: libdebconf.so: cannot open shared object file: No such file or directory**
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I solve this?

I did a search for libdebconf and came up with the following:
/usr/lib/libdebconfclient.so.0
/usr/lib/libdebconfclient.so.0.0.0
/usr/share/doc/libdebconfclient0
/usr/share/doc/libdebconfclient0/changelog.gz
/usr/share/doc/libdebconfclient0/copyright
/var/cache/apt/archives/libdebconfclient0_0.117build1_i386.deb
/var/lib/dpkg/info/libdebconfclient0.list
/var/lib/dpkg/info/libdebconfclient0.postinst
/var/lib/dpkg/info/libdebconfclient0.postrm
/var/lib/dpkg/info/libdebconfclient0.shlibs

---

