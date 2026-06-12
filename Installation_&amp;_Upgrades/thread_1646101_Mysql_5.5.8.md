---
title: "Mysql 5.5.8"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by Blastnsmash on 2010-12-15
Does anyone know when mysql 5.5.8 will be available within the synaptic package manager?

---

### Post by q999 on 2010-12-15
[http://en.wikipedia.org/wiki/LAMP_(software_bundle](http://en.wikipedia.org/wiki/LAMP_(software_bundle))
is lamp what you want?

---

### Post by Blastnsmash on 2010-12-15
> **q999 said:**
> [http://en.wikipedia.org/wiki/LAMP_(software_bundle](http://en.wikipedia.org/wiki/LAMP_(software_bundle))
is lamp what you want?

Mysql 5.5.8 just reached general availability status. I want to know when that version is going to be available through the synaptic package manager or if i should just install the linux binaries.

---

### Post by Milflyboy on 2010-12-16
I'd like to upgrade to 5.5 as well, but I suspect that unless an Ubuntu maintainer is particularly eager to use 5.5 in lucid, you'll only see it in synaptic if and after the following occur:
1. a mysql-server-5.5 appears in stable Debian -- don't see it [there]("http://packages.debian.org/search?keywords=mysql-server") yet
2. the Ubuntu team makes an Ubuntu variant of that package and tests it in either 10.10 or the current development version until they consider it stable
3. someone backports it to 10.04

#1-2 are certain to happen--just a matter of when. #3 is not certain to ever happen. :(

Bottom line: don't wait up for it. I'm guessing it'll be weeks if not months, but would love it if I were wrong! :p

---

### Post by thefirstM on 2010-12-16
I filed a bug report asking for an update here: [https://bugs.edge.launchpad.net/ubuntu/+source/mysql-5.1/+bug/690925]("https://bugs.edge.launchpad.net/ubuntu/+source/mysql-5.1/+bug/690925")

---

### Post by cyrex on 2010-12-16
I find it ridiculous that mysql has a million RPM packages but not even one DEB package, taking into consideration that Debian and all derivatives from it have far more linux users. Am not adding that CenOs, Red Hat and other RPM distros are more used as servers since they more likely began first but there are a lot of places where deb systems are used as servers like godaddy, mochahost, mediatemple and others i have worked with.

The part that got me was this: [http://dev.mysql.com/downloads/mysql/](http://dev.mysql.com/downloads/mysql/)

As you can see there, 2 billion RPM packages but no DEB package WTF??, only the binaries at the end for x86 and 64bit. Ridiculous indeed.

@thefirstM - Thank you friend for the bug report. There should be a way to tell the oracle people that HEY, In Linux there are DEB packages also. They could make every possible RPM combination but not even one DEB one.

---

### Post by Blastnsmash on 2010-12-16
Thank you all for the comments. 


hopefully we can get  this package available ASAP. Ubuntu is a very popular distro, it deserves attention.

---

### Post by simon_w on 2010-12-17
Best / most likely prospect is a version from dotdeb.org, which will probably be forthcoming fairly soon, I imagine.

[http://www.dotdeb.org/tag/mysql/](http://www.dotdeb.org/tag/mysql/)

:)

---

### Post by hhlp on 2010-12-18
a step by step guide how to install MYSQL 5.5 


[http://www.ovaistariq.net/490/a-step-by-step-guide-to-upgrading-to-mysql-5-5/]("http://www.ovaistariq.net/490/a-step-by-step-guide-to-upgrading-to-mysql-5-5/")

---

### Post by thiyagi on 2011-01-31
thanks guys...

---

### Post by ivotron on 2011-06-15
FYI, there's a PPA with a .deb here [https://launchpad.net/~clint-fewbar/+archive/mysql](https://launchpad.net/~clint-fewbar/+archive/mysql)

---

