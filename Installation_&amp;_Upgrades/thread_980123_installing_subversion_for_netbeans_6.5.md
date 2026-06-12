---
title: "installing subversion for netbeans 6.5"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by gmseed on 2008-11-12
Hi

I'm trying to install subversion for Netbeans 6.5 and going through their tutorial:

[http://www.netbeans.org/kb/60/ide/subversion.html](http://www.netbeans.org/kb/60/ide/subversion.html)

I installed the referred to subversion client via the command line aptitude tool [ubuntu package name subversion].

However, I can't locate the executable.

The Netbeans tutorial states it should be located in /usr/local/bin/ for UNIX installations, but it's not there.

The only files I can locate are in /etc/subversion/ which contain config and servers text files.

Cheers

Graham

---

### Post by jameslov on 2009-09-17
This is an old thread, but I came across the same issue and wanted to respond in case someone else googles this issue and ends up here.  NetBeans thinks that subversion should be at /usr/local/bin, but in Ubuntu 9.04 it installs at /usr/bin/svn.  You can find this out for yourself by using the following code: 

```
which svn
```

the output will tell you where subversion is installed.

---

### Post by mysticav on 2010-01-27
You were right, I googled and came here for same question. Thanks.

---

