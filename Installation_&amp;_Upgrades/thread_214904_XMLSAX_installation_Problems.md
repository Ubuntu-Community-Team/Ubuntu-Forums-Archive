---
title: "XML::SAX installation Problems"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by lichtgestalt on 2006-07-13
Hi guys,

got a little problem with the lixml-sax-perl installation i cant fix.
I'm using linux for a long time so advanced instruction should be no problem (just switched to ubuntu last week, as a reliable an stable working envoirement, meaning i'm not so in to ubuntu/debian)

Here we go:
> 
Setting up libxml-filter-saxt-perl (0.01-6) ...
Setting up libxml-namespacesupport-perl (1.09-2) ...
Setting up libxml-perl (0.08-1) ...
[B]Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255[/B]
dpkg: dependency problems prevent configuration of libxml-filter-buffertext-perl:
 libxml-filter-buffertext-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-filter-buffertext-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-writer-perl:
 libxml-sax-writer-perl depends on libxml-filter-buffertext-perl (>= 0.01); however:
  Package libxml-filter-buffertext-perl is not configured yet.
 libxml-sax-writer-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-writer-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpod-sax-perl:
 libpod-sax-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
 libpod-sax-perl depends on libxml-sax-writer-perl (>= 0.39); however:
  Package libxml-sax-writer-perl is not configured yet.
dpkg: error processing libpod-sax-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-libxslt-perl:
 libxml-libxslt-perl depends on libxml-libxml-perl (>= 1.56-3); however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing libxml-libxslt-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-machines-perl:
 libxml-sax-machines-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
 libxml-sax-machines-perl depends on libxml-sax-writer-perl (>= 0.42); however:
  Package libxml-sax-writer-perl is not configured yet.
dpkg: error processing libxml-sax-machines-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simpleobject-libxml-perl:
 libxml-simpleobject-libxml-perl depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing libxml-simpleobject-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-filter-xslt-perl:
 libxml-filter-xslt-perl depends on libxml-libxslt-perl; however:
  Package libxml-libxslt-perl is not configured yet.
 libxml-filter-xslt-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-filter-xslt-perl depends on libxml-sax-writer-perl; however:
  Package libxml-sax-writer-perl is not configured yet.
dpkg: error processing libxml-filter-xslt-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-filter-buffertext-perl
 libxml-sax-writer-perl
 libpod-sax-perl
 libxml-libxml-perl
 libxml-libxslt-perl
 libxml-sax-machines-perl
 libxml-sax-expat-perl
 libxml-simple-perl
 libxml-simpleobject-libxml-perl
 libxml-filter-xslt-perl
[B]E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255[/B]
dpkg: dependency problems prevent configuration of libpod-sax-perl:
 libpod-sax-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libpod-sax-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-filter-buffertext-perl:
 libxml-filter-buffertext-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-filter-buffertext-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-writer-perl:
 libxml-sax-writer-perl depends on libxml-filter-buffertext-perl (>= 0.01); however:
  Package libxml-filter-buffertext-perl is not configured yet.
 libxml-sax-writer-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-writer-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-machines-perl:
 libxml-sax-machines-perl depends on libxml-sax-perl (>= 0.10); however:
  Package libxml-sax-perl is not configured yet.
 libxml-sax-machines-perl depends on libxml-sax-writer-perl (>= 0.42); however:
  Package libxml-sax-writer-perl is not configured yet.
dpkg: error processing libxml-sax-machines-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-filter-xslt-perl:
 libxml-filter-xslt-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-filter-xslt-perl depends on libxml-sax-writer-perl; however:
  Package libxml-sax-writer-perl is not configured yet.
dpkg: error processing libxml-filter-xslt-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simpleobject-libxml-perl:
 libxml-simpleobject-libxml-perl depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing libxml-simpleobject-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-libxslt-perl:
 libxml-libxslt-perl depends on libxml-libxml-perl (>= 1.56-3); however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing libxml-libxslt-perl (--configure):
 dependency problems - leaving unconfigured
:confused: :-k 

That's the output i get trying to install the package. I've got no idea about the debian install system, but i'm willing to learn.

If you need any further information (like config files or installed packages) plz tell me and I'll provide them.

Thanks a lot!

---

### Post by lichtgestalt on 2006-07-13
no1 any idea what could be the prob?

---

### Post by danielk23 on 2006-07-26
I just wrote a reply to another thread with the same problem:
[http://ubuntuforums.org/showthread.php?p=1302053#post1302053](http://ubuntuforums.org/showthread.php?p=1302053#post1302053)

daniel

---

