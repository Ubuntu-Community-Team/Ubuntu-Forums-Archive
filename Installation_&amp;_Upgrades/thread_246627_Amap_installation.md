---
title: "Amap installation"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by EvilAngel on 2006-08-29
Hi all,

I am on a fresh Dapper install and I am trying to install amap.
I have an error:
```
root@Mojito:/var/www# apt-get install amap
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  amap
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/70.0kB of archives.
After unpacking 209kB of additional disk space will be used.
Selecting previously deselected package amap.
(Reading database ... 71632 files and directories currently installed.)
Unpacking amap (from .../archives/amap_4.8-1.1_i386.deb) ...
Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to www.thc.org/thc-amap
Error: file could not be found by web server: HTTP/1.0 404 no such forward entryServer: redir-httpd
Date: Tue, 29 Aug 2006 18:57:31 GMT
Content-Length: 49
Content-Type: text/html

<html><body>no such forward entry</body></html>

dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amap
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mojito:/var/www#

```The right URL is in fact [http://thc.org.segfault.net/thc-amap/](http://thc.org.segfault.net/thc-amap/) but I don't kow how to change it in the configuration.

ANy idea ??

THanks

---

