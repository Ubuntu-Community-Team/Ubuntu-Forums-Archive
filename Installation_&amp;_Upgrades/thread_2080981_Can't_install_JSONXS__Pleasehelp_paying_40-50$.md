---
title: "Can't install JSON::XS ???? Pleasehelp paying 40-50$"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by port22 on 2012-11-05
Hello, well I'm trying to install the shodan library


docs.shodanhq.com/perl/tutorial.html

Have issues It won't install JSON::XS

'sudo perl -MCPAN -e 'install JSON::XS'
```


Checking if your kit is complete...
Looks good
Writing Makefile for JSON::XS
Writing MYMETA.yml
cp XS/Boolean.pm blib/lib/JSON/XS/Boolean.pm
cp XS.pm blib/lib/JSON/XS.pm
/usr/bin/perl /usr/share/perl/5.14/ExtUtils/xsubpp  -typemap /usr/share/perl/5.14/ExtUtils/typemap -typemap typemap  XS.xs > XS.xsc && mv XS.xsc XS.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"2.33\" -DXS_VERSION=\"2.33\" -fPIC "-I/usr/lib/perl/5.14/CORE"   XS.c
/bin/sh: 1: cc: not found
make: *** [XS.o] Error 127
  MLEHMANN/JSON-XS-2.33.tar.gz
  /usr/bin/make -- NOT OK
'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible


```

ny ideas?

Also curl cmd didn't work i used wget instead is it the same? btw I have PHP installed.

'curl -OL github.com/downloads/achillean/shodan-perl/Shodan-0.3.tar.gz' didn't work so I just used wget hope it's the same.

I'm a utter noob. If someone could help me I can reward them 20-50$ via PayPal/LR

---

### Post by Lars Noodén on 2012-11-05
Search in the Ubuntu repositories using Synaptic or the software center.  you'll find a package called [libjson-xs-perl](apt:libjson-xs-perl) which will give you the CPAN module you are looking for.  No need to trouble with CPAN if you can get it from the repository.

---

