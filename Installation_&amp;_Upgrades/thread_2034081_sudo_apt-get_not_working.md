---
title: "sudo apt-get not working"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by ABCraine on 2012-07-27
It's been a while since I've needed to install anything.  I'm wanting to do some image work using php (imagecreatefromJPEG in particular).  It was suggested that I do the following:

sudo apt-get install php5-gd

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  php5-gd
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/38.8 kB of archives.
After this operation, 172 kB of additional disk space will be used.
**E: Sub-process gzip returned an error code (100)**
E: Prior errors apply to /var/cache/apt/archives/php5-gd_5.3.6-13ubuntu3.8_amd64.deb
debconf: apt-extracttemplates failed: 
dpkg-deb (subprocess): unable to execute tar (tar): No such file or directory
dpkg-deb: error: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/php5-gd_5.3.6-13ubuntu3.8_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/php5-gd_5.3.6-13ubuntu3.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What's with the (bolded) error?  I tried to install csh (just to try something else) and got the same error.

What has happened?  What do I need to fix?  It looks like I can't install anything???

---

### Post by miegiel on 2012-07-27
*gzip* extracts (decompresses/unzips) the package you downloaded so *dpkg* can install it. Maybe the package got corrupted during the download.

Not sure this will fix it but it's what I'd try first
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
or
```
sudo apt-get dselect-upgrade
```
It seems you have an update that needs to be installed. Always update/upgrade before installing stuff ;)

If that was not enough:
```
sudo apt-get autoclean
```
should remove all downloaded, but not installed, packages. So it should remove the downloaded *php5-gd* package too. Else go to */var/cache/apt/archives* and delete it manually (you might need to be root, be careful not to make any mistakes).

Do:
```
gksudo nautilus
```
to start the file browser as root.

When all that is done, try to install the package again.

---

