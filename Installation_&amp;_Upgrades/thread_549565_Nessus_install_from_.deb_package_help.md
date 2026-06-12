---
title: "Nessus install from .deb package help"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by mrbond on 2007-09-12
I have tried recently agian to install nessus 3 from deb package on my ubuntu LTS (  2.6.15-27-server #1 SMP  i686 GNU/Linux)

I recieve the following as output with debugging on:


```
root@northstar:/download# dpkg -i --debug=100 Nessus-3.0.6-debian3_i386_2.deb
(Reading database ... 23074 files and directories currently installed.)
Unpacking nessus (from Nessus-3.0.6-debian3_i386_2.deb) ...
Stopping Nessus daemon: nessusd.
D000100: setupvnamevbs main=`/.' tmp=`/..dpkg-tmp' new=`/..dpkg-new'
D000100: tarobject already exists
D000100: tarobject Directory exists
D000100: setupvnamevbs main=`/opt' tmp=`/opt.dpkg-tmp' new=`/opt.dpkg-new'
D000100: tarobject already exists
D000100: tarobject Directory exists
D000100: setupvnamevbs main=`/opt/nessus' tmp=`/opt/nessus.dpkg-tmp' new=`/opt/nessus.dpkg-new'
D000100: tarobject already exists
D000100: tarobject Directory exists
D000100: setupvnamevbs main=`/opt/nessus/bin' tmp=`/opt/nessus/bin.dpkg-tmp' new=`/opt/nessus/bin.dpkg-new'
D000100: tarobject nonexistent
D000100: tarobject Directory creating
D000100: tarobject new - no backup
D000100: tarobject done and installed
D000100: setupvnamevbs main=`/opt/nessus/bin/nasl' tmp=`/opt/nessus/bin/nasl.dpkg-tmp' new=`/opt/nessus/bin/nasl.dpkg-new'
D000100: tarobject nonexistent
D000100: tarobject NormalFile[01] open size=238072
D000100: tarobject new - no backup
D000100: tarobject done and installed
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing Nessus-3.0.6-debian3_i386_2.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
D000100: setupvnamevbs main=`//opt/nessus/bin/nasl' tmp=`//opt/nessus/bin/nasl.dpkg-tmp' new=`//opt/nessus/bin/nasl.dpkg-new'
D000100: cu_installnew removing new file
D000100: unlinkorrmdir `//opt/nessus/bin/nasl' unlink OK
D000100: unlinkorrmdir `//opt/nessus/bin/nasl.dpkg-new' rmdir No such file or directory
D000100: setupvnamevbs main=`//opt/nessus/bin' tmp=`//opt/nessus/bin.dpkg-tmp' new=`//opt/nessus/bin.dpkg-new'
D000100: cu_installnew removing new file
D000100: unlinkorrmdir `//opt/nessus/bin' rmdir OK
D000100: unlinkorrmdir `//opt/nessus/bin.dpkg-new' rmdir No such file or directory
Errors were encountered while processing:
 Nessus-3.0.6-debian3_i386_2.deb
root@northstar:/download#

```

The _2 in the package name is there because i re downloaded the file as i figured the first one was corrupt. 

Looks like some ******* breaking my pipes! Any help appreciated

---

### Post by cabala on 2007-09-17
follow the instructions on the website nessus.org - first download the added packages you need then update the system (you get kernel 16) then try to install linux:

[http://www.nessus.org/documentation/nessus_3.0_installation_guide.pdf](http://www.nessus.org/documentation/nessus_3.0_installation_guide.pdf)

am not having ANY problem with nessus 3 on ubuntu feisty after following the instructions!

for the client, an alternative is to download the Debian 4 package from the "client 3.0.0 client for linux/windows) option on the tenable security (nessus.org) page. double-clicking it places the client in /opt/nessus/bin/

---

