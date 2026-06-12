---
title: "installing 2d soccer simulation base"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by Moh3en_DDD on 2008-09-28
this is an error that when i want to install 2d 2d soccer simulation base , apeared . 

i used ./configure command , then i use make command : 

> In file included from ../../boost/config.hpp:35,
                 from ../../boost/shared_ptr.hpp:18,
                 from parser.hpp:27,
                 from parse.ypp:23:
../../boost/config/compiler/gcc.hpp:66:7: warning: #warning "Unknown compiler version - please run the configure tests and report the results"
In file included from parse.ypp:23:
parser.hpp:182: error: extra qualification 'rcss::conf::Parser::Param::' on member 'operator='
/usr/share/bison.simple: In function 'int RCSS_CONF_parse(void*)':
/usr/share/bison.simple:614: warning: comparison between signed and unsigned integer expressions
/usr/share/bison.simple:626: warning: comparison between signed and unsigned integer expressions
make[3]: *** [parse.lo] Error 1
make[3]: Leaving directory `/home/moh3en/Desktop/rcssbase-10.0.11/rcssbase/conf'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/moh3en/Desktop/rcssbase-10.0.11/rcssbase/conf'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/moh3en/Desktop/rcssbase-10.0.11/rcssbase'
make: *** [all-recursive] Error 1


whats wrong ?  :confused:

---

### Post by cariboo on 2008-09-28
From what the snippet you posted says, it doesn't like the version of gcc that you are using.

JIm

---

