---
title: "problem in installing python-qt4"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2013-09-17
I am having problem in installing python-qt4 in Ubuntu 12.04 
How do I resolve it following is text on terminal
```

user@ubuntu:~$ sudo aptitude install python-qt4
[sudo] password for user: 
The following NEW packages will be installed:
  libqt4-designer{ab} libqt4-help{ab} libqt4-scripttools{ab} 
  libqt4-test{ab} libqtassistantclient4{a} libqtwebkit4{a} python-qt4 
  python-sip{a} 
0 packages upgraded, 8 newly installed, 0 to remove and 1 not upgraded.
Need to get 13.5 MB of archives. After unpacking 54.7 MB will be used.
The following packages have unmet dependencies:
 libqt4-test : Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
 libqt4-designer : Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
                   Depends: libqt4-xml (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
                   Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
                   Depends: libqtgui4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
 libqt4-help : Depends: libqt4-network (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
               Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
               Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
               Depends: libqtgui4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
 libqt4-scripttools : Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
                      Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
                      Depends: libqtgui4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.3 is installed.
Internal error: the solver Install(qdbus:i386 4:4.8.1-0ubuntu4 <libqt4-dbus:amd64 4:4.8.1-0ubuntu4 -S> {qdbus:amd64 4:4.8.1-0ubuntu4 qdbus:i386 4:4.8.1-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 43
Internal error: the solver Install(qdbus:i386 4:4.8.1-0ubuntu4 <libqt4-dbus:amd64 4:4.8.1-0ubuntu4 -S> {qdbus:amd64 4:4.8.1-0ubuntu4 qdbus:i386 4:4.8.1-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 50
Internal error: the solver Install(unixodbc:i386 2.2.14p2-5ubuntu3 <libqt4-sql-odbc:amd64 4:4.8.1-0ubuntu4 -> {libodbc1:amd64 2.2.14p2-5ubuntu3 unixodbc:amd64 2.2.14p2-5ubuntu3 unixodbc:i386 2.2.14p2-5ubuntu3}>) of a supposedly unresolved dependency is already installed in step 72
Internal error: the solver Install(qdbus:i386 4:4.8.1-0ubuntu4 <libqt4-dbus:amd64 4:4.8.1-0ubuntu4 -S> {qdbus:amd64 4:4.8.1-0ubuntu4 qdbus:i386 4:4.8.1-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 74
Internal error: the solver Install(unixodbc:i386 2.2.14p2-5ubuntu3 <libqt4-sql-odbc:amd64 4:4.8.1-0ubuntu4 -> {libodbc1:amd64 2.2.14p2-5ubuntu3 unixodbc:amd64 2.2.14p2-5ubuntu3 unixodbc:i386 2.2.14p2-5ubuntu3}>) of a supposedly unresolved dependency is already installed in step 82
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 127
Internal error: the solver Install(unixodbc:i386 2.2.14p2-5ubuntu3 <libqt4-sql-odbc:amd64 4:4.8.1-0ubuntu4 -> {libodbc1:amd64 2.2.14p2-5ubuntu3 unixodbc:amd64 2.2.14p2-5ubuntu3 unixodbc:i386 2.2.14p2-5ubuntu3}>) of a supposedly unresolved dependency is already installed in step 138
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     libqt4-designer [Not Installed]                    
2)     libqt4-help [Not Installed]                        
3)     libqt4-scripttools [Not Installed]                 
4)     libqt4-test [Not Installed]                        
5)     python-qt4 [Not Installed]        
Accept this solution? [Y/n/q/?] Y    
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         



```

---

