---
title: "Installing GroupWise and Console one on 10.4"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by altonza on 2010-06-15
Hi There
I am battling to install a groupwise client on my ubuntu 10,.4. I downloaded the tar.gz file from novell and then uncompressed the file to reveal a directory. Therafter i tried to use alien to convert the .rpm file to .deb and it did that as well.
However when i try to install the .deb file in ubuntu from a terminal it give the following error.

===
sudo dpkg -i novell-groupwise-gwclient_8.0.0-84910_i386.deb 

(Reading database ... 151254 files and directories currently installed.)
Unpacking novell-groupwise-gwclient (from novell-groupwise-gwclient_8.0.0-84910_i386.deb) ...
dpkg-deb: unexpected end of file in between members in novell-groupwise-gwclient_8.0.0-84910_i386.deb
dpkg: error processing novell-groupwise-gwclient_8.0.0-84910_i386.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 novell-groupwise-gwclient_8.0.0-84910_i386.deb
======

Any ideas would be greatly appreciated.
regards
Alton

---

### Post by incognia on 2010-06-15
To get install ConsoleOne 1.3.6h you can follow this manual:

[http://www.novell.com/coolsolutions/tip/16609.html]("http://www.novell.com/coolsolutions/tip/16609.html")

It works on Ubuntu Lucid (tested), you most execute ConsoleOne as root.

```
sudo /usr/ConsoleOne/bin/ConsoleOne &
```

---

