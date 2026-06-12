---
title: "Install Oracle 10gR2 XE on ubuntu 11.04"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by Burfee on 2011-05-15
Hello,

Has anyone managed to install the oracle 10g xe server on ubuntu 11.04? I previously installed it on ubuntu 10.10 following [this]("http://www.ubuntugeek.com/how-to-install-oracle-10g-xe-in-64-bit-ubuntu.html") instructions, but now i am having problems when doing the same thing on ubuntu 11.04.

```
burfee@burfee:~/Downloads/Oracle 10gXE$ sudo dpkg -i --force-architecture libaio_0.3.104-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 200050 files and directories currently installed.)
Unpacking libaio:i386 (from libaio_0.3.104-1_i386.deb) ...
dpkg: error processing libaio_0.3.104-1_i386.deb (--install):
 trying to overwrite '/usr/include/libaio.h', which is also in package libaio-dev 0.3.107-7ubuntu2
Errors were encountered while processing:
 libaio_0.3.104-1_i386.deb

```and then 

```
burfee@burfee:~/Downloads/Oracle 10gXE$ sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.0_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 200050 files and directories currently installed.)
Preparing to replace oracle-xe-universal:i386 10.2.0.1-1.0 (using oracle-xe-universal_10.2.0.1-1.0_i386.deb) ...
Unpacking replacement oracle-xe-universal:i386 ...
dpkg: dependency problems prevent configuration of oracle-xe-universal:i386:
 oracle-xe-universal:i386 depends on libc6 (>= 2.3.2).
 oracle-xe-universal:i386 depends on libaio (>= 0.3.96) | libaio1 (>= 0.3.96); however:
  Package libaio:i386 is not installed.
dpkg: error processing oracle-xe-universal:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
Errors were encountered while processing:
 oracle-xe-universal:i386

```Any help would be very much appreciated as i have been struggling with this issue for a quite a long time now.

---

### Post by tonyozr on 2011-05-15
from this [http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/]("http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/#comment-194921589")

> Hi,

I also had this issue and fixed it today. Extract the deb file, open Oracle-xe-universal_10.2.0.1-1.0_i386/DEBIAN/control and remove the dependency for libc6 so you end up with:

Depends: libaio (>= 0.3.96) | libaio1 (>= 0.3.96)

Then cd to the directory that contains the extracted folders and do a dpkg-deb --build oracle-xe-universal_10.2.0.1-1.0_i386 && sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.0_i386.deb 

Hope this helps, worked for me :D

hope this helps

---

### Post by Burfee on 2011-05-15
Yes, it did! :D :D
Thank you very much for your help!

---

