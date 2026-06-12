---
title: "xercesc installation"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by sehriyar on 2008-10-25
Hi,

Is there anyone who can install and use xerces-c-3.0.0. I installed it with

configure
make
make install

commands without any argument. But when I try to compile a program with g++, it gives me lots of undefined reference errors. The xerces-c.a library stands in /usr/local/lib folder. And I try to compile with "g++ file.cpp". And file.cpp includes the following headers.

#include <xercesc/parsers/XercesDOMParser.hpp>
#include <xercesc/util/XMLUni.hpp>

Can anyone explain how to correct install and use of it.

Thanks in advance.

---

### Post by RomanIvanov on 2008-12-26
Follow up this: [http://xerces.apache.org/xerces-c/install-3.html#Unix](http://xerces.apache.org/xerces-c/install-3.html#Unix)
Download from this: [http://xerces.apache.org/xerces-c/download.cgi](http://xerces.apache.org/xerces-c/download.cgi)

Do not forget to copy include files to Ubuntu includes:
Place there you install for example - /usr/share/xerces-c-3.0.0-x86-linux-gcc-3.4/

```
sudo cp -r /usr/share/xerces-c-3.0.0-x86-linux-gcc-3.4/include/xercesc /usr/include

```

---

